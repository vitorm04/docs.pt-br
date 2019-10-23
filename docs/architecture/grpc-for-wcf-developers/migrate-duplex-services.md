---
title: Migrar serviços do WCF duplex para gRPC-gRPC para desenvolvedores do WCF
description: Saiba como migrar várias formas de serviço de duplex do WCF para serviços de streaming do gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1c3f87b035cea367188e8357f4755c7b6786ab77
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770390"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a>Migrar serviços duplex do WCF para gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Agora que os conceitos básicos estão em vigor, esta seção examinará os serviços gRPC de *streaming* mais complicados.

Há várias maneiras de usar os serviços duplex no Windows Communication Foundation (WCF). Alguns serviços são iniciados pelo cliente e, em seguida, transmitem dados do servidor. Outros serviços Full duplex podem envolver uma comunicação bidirecional mais contínua como o exemplo clássico de "calculadora" da documentação do WCF. Este capítulo usará duas implementações possíveis de "cotação de ações" do WCF e as migrará para o gRPC: uma usando um RPC de streaming de servidor e a outra usando um RPC de streaming bidirecional.

## <a name="server-streaming-rpc"></a>RPC de streaming do servidor

No [exemplo da solução SimpleStockTicker do WCF](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), *SimpleStockPriceTicker*, há um serviço duplex em que o cliente inicia a conexão com uma lista de símbolos de ações e o servidor usa a interface de *retorno de chamada* para enviar atualizações como elas torna-se disponível. O cliente implementa essa interface para responder a chamadas do servidor.

### <a name="the-wcf-solution"></a>A solução WCF

A solução WCF é implementada como um servidor NetTCP auto-hospedado em um aplicativo de console .NET Framework 4. x.

#### <a name="the-servicecontract"></a>O ServiceContract

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

O serviço tem um único método sem nenhum tipo de retorno, pois ele usará a interface de retorno de chamada `ISimpleStockTickerCallback` para enviar dados para o cliente em tempo real.

#### <a name="the-callback-interface"></a>A interface de retorno de chamada

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

As implementações dessas interfaces podem ser encontradas na solução, juntamente com dependências externas falsas para fornecer dados de teste.

### <a name="grpc-streaming"></a>streaming de gRPC

A maneira gRPC de lidar com dados em tempo real é diferente. Uma chamada do cliente para o servidor pode criar um fluxo persistente, que pode ser monitorado para mensagens que chegam de forma assíncrona. Apesar da diferença, os fluxos podem ser uma maneira mais intuitiva de lidar com esses dados e são mais relevantes para a programação moderna com ênfase em LINQ, fluxos reativos, programação funcional e assim por diante.

A definição de serviço precisa de duas mensagens: uma para a solicitação e outra para o fluxo. O serviço retorna um fluxo da mensagem de `StockTickerUpdate` usando a palavra-chave `stream` em sua declaração de `return`. É recomendável que você adicione um `Timestamp` à atualização para mostrar a hora exata em que o preço foi alterado.

#### <a name="simple_stock_tickerproto"></a>simple_stock_ticker. proto

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.SimpleStockTickerServer.Protos";

import "google/protobuf/timestamp.proto";

package SimpleStockTickerServer;

service SimpleStockTicker {
  rpc Subscribe (SubscribeRequest) returns (stream StockTickerUpdate);
}

message SubscribeRequest {
  repeated string symbols = 1;
}

message StockTickerUpdate {
  string symbol = 1;
  int32 price_cents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-the-simplestockticker"></a>Implementar o SimpleStockTicker

Reutilize o `StockPriceSubscriber` falso do projeto do WCF copiando as três classes da biblioteca de classes `TraderSys.StockMarket` em uma nova biblioteca de classes de .NET Standard na solução de destino. Para seguir melhor as práticas recomendadas, adicione um tipo de `Factory` para criar instâncias dele e registrar o `IStockPriceSubscriberFactory` com os serviços de injeção de dependência de ASP.NET Core.

#### <a name="the-factory-implementation"></a>A implementação de fábrica

```csharp
public interface IStockPriceSubscriberFactory
{
    IStockPriceSubscriber GetSubscriber(string[] symbols);
}

public class StockPriceSubscriberFactory : IStockPriceSubscriberFactory
{
    public IStockPriceSubscriber GetSubscriber(string[] symbols)
    {
        return new StockPriceSubscriber(symbols);
    }
}
```

#### <a name="registering-the-factory"></a>Registrando a fábrica

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

Agora, essa classe pode ser usada para implementar o serviço gRPC StockTicker.

#### <a name="stocktickerservicecs"></a>StockTickerService.cs

```csharp
public class StockTickerService : Protos.SimpleStockTicker.SimpleStockTickerBase
{
    private readonly IStockPriceSubscriberFactory _subscriberFactory;

    public StockTickerService(IStockPriceSubscriberFactory subscriberFactory)
    {
        _subscriberFactory = subscriberFactory;
    }

    public override async Task Subscribe(SubscribeRequest request, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
    {
        var subscriber = _subscriberFactory.GetSubscriber(request.Symbols.ToArray());

        subscriber.Update += async (sender, args) =>
            await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

        await AwaitCancellation(context.CancellationToken);
    }

    private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
    {
        try
        {
            await stream.WriteAsync(new StockTickerUpdate
            {
                Symbol = symbol,
                PriceCents = (int)(price * 100),
                Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
            });
        }
        catch (Exception e)
        {
            // Handle any errors due to broken connection etc.
            _logger.LogError($"Failed to write message: {e.Message}");
        }
    }

    private static Task AwaitCancellation(CancellationToken token)
    {
        var completion = new TaskCompletionSource<object>();
        token.Register(() => completion.SetResult(null));
        return completion.Task;
    }
}
```

Como você pode ver, embora a declaração no arquivo `.proto` diga que o método "retorna" um fluxo de `StockTickerUpdate` mensagens, de fato ele retorna uma `Task` de baunilha. O trabalho de criar o fluxo é tratado pelo código gerado e pelas bibliotecas de tempo de execução gRPC, que fornecem o fluxo de resposta `IServerStreamWriter<StockTickerUpdate>`, pronto para uso.

Ao contrário de um serviço do WCF duplex, em que a instância da classe de serviço é mantida ativa enquanto a conexão está aberta, o serviço gRPC usa a tarefa retornada para manter o serviço ativo. A tarefa não deve ser concluída até que a conexão seja fechada.

O serviço pode informar quando o cliente fechou a conexão usando o `CancellationToken` da `ServerCallContext`. Um método estático simples, `AwaitCancellation`, é usado para criar uma tarefa que é concluída quando o token é cancelado.

No método `Subscribe`, em seguida, obtenha um `StockPriceSubscriber` e adicione um manipulador de eventos que grava no fluxo de resposta. Em seguida, aguarde até que a conexão seja fechada, antes de descartar imediatamente o `subscriber` para impedir que ele tente gravar dados no fluxo fechado.

O método `WriteUpdateAsync` tem um bloco `try` / `catch` para lidar com quaisquer erros que possam ocorrer durante a gravação de uma mensagem no fluxo. Essa é uma consideração importante em conexões persistentes em redes, que podem ser quebradas a qualquer milissegundo, intencionalmente ou devido a uma falha em algum lugar.

### <a name="using-the-stocktickerservice-from-a-client-application"></a>Usando o StockTickerService de um aplicativo cliente

Siga as mesmas etapas na seção anterior para criar uma biblioteca de classes de cliente compartilhável do arquivo `.proto`. No exemplo, há um aplicativo de console do .NET Core 3,0 que demonstra como usar o cliente.

#### <a name="example-programcs"></a>Exemplo de Program.cs

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        using var channel = GrpcChannel.ForAddress("https://localhost:5001");
        var client = new SimpleStockTicker.SimpleStockTickerClient(channel);

        var request = new SubscribeRequest();
        request.Symbols.AddRange(args);

        using var stream = client.Subscribe(request);

        var tokenSource = new CancellationTokenSource();

        var task = DisplayAsync(stream.ResponseStream, tokenSource.Token);

        WaitForExitKey();

        tokenSource.Cancel();
        await task;
    }
}
```

Nesse caso, o método `Subscribe` no cliente gerado não é assíncrono. O fluxo é criado e utilizável imediatamente, porque seu método de `MoveNext` é assíncrono e a primeira vez que ele é chamado não é concluído até que a conexão esteja ativa.

O fluxo é passado para um método assíncrono de `DisplayAsync`; em seguida, o aplicativo aguarda que o usuário pressione uma tecla e, em seguida, cancela o método `DisplayAsync` e aguarda a conclusão da tarefa antes de sair.

> [!NOTE]
> Esse código está usando a nova C# sintaxe 8 "usando declaração" para descartar o fluxo e o canal quando o método `Main` é encerrado. É uma pequena alteração, mas uma boa que reduz recuos e linhas vazias.

#### <a name="consume-the-stream"></a>Consumir o fluxo

As interfaces de retorno de chamada do WCF usavam para permitir que o servidor Chame métodos diretamente no cliente. os fluxos de gRPC funcionam de maneira diferente. O cliente itera sobre o fluxo retornado e processa as mensagens, assim como se elas fossem retornadas de um método local que retorna um `IEnumerable`.

O tipo de `IAsyncStreamReader<T>` funciona de forma muito semelhante a uma `IEnumerator<T>`: há um método `MoveNext` que retornará true, desde que haja mais dados e uma propriedade `Current` que retorne o valor mais recente. A única diferença é que o método `MoveNext` retorna um `Task<bool>` em vez de apenas um `bool`. O método de extensão `ReadAllAsync` encapsula o fluxo em um `IAsyncEnumerable` C# Standard 8 que pode ser usado com a nova sintaxe `await foreach`.

```csharp
static async Task DisplayAsync(IAsyncStreamReader<StockTickerUpdate> stream, CancellationToken token)
{
    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            Console.WriteLine($"{update.Symbol}: {update.Price}");
        }
    }
    catch (RpcException e) when (e.StatusCode == StatusCode.Cancelled)
    {
        return;
    }
    catch (OperationCanceledException)
    {
        Console.WriteLine("Finished.");
    }
}
```

> [!TIP]
> A seção sobre [bibliotecas de cliente](client-libraries.md#iobservable) no final deste capítulo analisa como adicionar um método e classes de extensão para encapsular `IAsyncStreamReader<T>` em um `IObservable<T>` para desenvolvedores que usam padrões de programação reativos.

Mais uma vez, tenha cuidado para capturar exceções aqui, devido à possibilidade de falha de rede, bem como à <xref:System.OperationCanceledException> que será inevitavelmente gerada porque o código está usando uma <xref:System.Threading.CancellationToken> para interromper o loop. O tipo de `RpcException` tem muitas informações úteis sobre erros de tempo de execução gRPC, incluindo o `StatusCode`. Para obter mais informações, consulte [ *tratamento de erros* no capítulo 4](error-handling.md).

## <a name="bidirectional-streaming"></a>Streaming bidirecional

Um serviço do WCF Full-duplex permite mensagens assíncronas e em tempo real em ambas as direções. No exemplo de transmissão de servidor, o cliente inicia uma solicitação e recebe um fluxo de atualizações. Uma versão melhor desse serviço permitiria que o cliente adicionasse e removesse ações da lista sem precisar parar e criar uma nova assinatura. Essa funcionalidade foi implementada na [solução de exemplo FullStockTicker](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).

A interface `IFullStockTickerService` fornece três métodos:

- `Subscribe` inicia a conexão.
- `AddSymbol` adiciona um símbolo de ação a ser observado.
- `RemoveSymbol` remove um símbolo da lista observada.

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(IFullStockTickerCallback))]
public interface IFullStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe();

    [OperationContract(IsOneWay = true)]
    void AddSymbol(string symbol);

    [OperationContract(IsOneWay = true)]
    void RemoveSymbol(string symbol);
}
```

A interface de retorno de chamada permanece a mesma.

A implementação desse padrão no gRPC é menos simples, porque agora há dois fluxos de dados com mensagens sendo passadas: um do cliente para o servidor e outro do servidor para o cliente. Não é possível usar vários métodos para implementar a operação adicionar e remover, mas mais de um tipo de mensagem pode ser passado em um único fluxo, usando o tipo de `Any` ou a palavra-chave `oneof`, que foram abordados no [capítulo 3](protobuf-any-oneof.md).

Para um caso em que há um conjunto específico de tipos que são aceitáveis, `oneof` é uma maneira melhor de começar. Use um `ActionMessage` que possa conter um `AddSymbolRequest` ou um `RemoveSymbolRequest`.

```protobuf
message ActionMessage {
  oneof action {
    AddSymbolRequest add = 1;
    RemoveSymbolRequest remove = 2;
  }
}

message AddSymbolRequest {
  string symbol = 1;
}

message RemoveSymbolRequest {
  string symbol = 1;
}
```

Declare um serviço de streaming bidirecional que usa um fluxo de mensagens de `ActionMessage`.

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

A implementação para esse serviço é semelhante ao exemplo anterior, exceto que o primeiro parâmetro do método `Subscribe` agora é um `IAsyncStreamReader<ActionMessage>`, que pode ser usado para lidar com as solicitações `Add` e `Remove`.

```csharp
public override async Task Subscribe(IAsyncStreamReader<ActionMessage> requestStream, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
{
    using var subscriber = _subscriberFactory.GetSubscriber();

    subscriber.Update += async (sender, args) =>
        await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

    var actionsTask = HandleActions(requestStream, subscriber, context.CancellationToken);

    _logger.LogInformation("Subscription started.");
    await AwaitCancellation(context.CancellationToken);

    try { await actionsTask; } catch { /* Ignored */ }

    _logger.LogInformation("Subscription finished.");
}

private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
{
    try
    {
        await stream.WriteAsync(new StockTickerUpdate
        {
            Symbol = symbol,
            PriceCents = (int)(price * 100),
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }
    catch (Exception e)
    {
        // Handle any errors due to broken connection etc.
        _logger.LogError($"Failed to write message: {e.Message}");
    }
}

private static Task AwaitCancellation(CancellationToken token)
{
    var completion = new TaskCompletionSource<object>();
    token.Register(() => completion.SetResult(null));
    return completion.Task;
}
```

A classe `ActionMessage` que o gRPC gerou para nós garante que apenas uma das propriedades `Add` e `Remove` possa ser definida, e localizar qual delas não é `null` é uma maneira válida de localizar o tipo de mensagem que é usado , mas há uma maneira melhor. A geração de código também criou um `enum ActionOneOfCase` na classe `ActionMessage`, que tem a seguinte aparência:

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

A propriedade `ActionCase` no objeto `ActionMessage` pode ser usada com uma instrução `switch` para determinar qual campo está definido.

```csharp
private async Task HandleActions(IAsyncStreamReader<ActionMessage> requestStream, IFullStockPriceSubscriber subscriber, CancellationToken token)
{
    await foreach (var action in requestStream.ReadAllAsync(token))
    {
        switch (action.ActionCase)
        {
            case ActionMessage.ActionOneofCase.None:
                _logger.LogWarning("No Action specified.");
                break;
            case ActionMessage.ActionOneofCase.Add:
                subscriber.Add(action.Add.Symbol);
                break;
            case ActionMessage.ActionOneofCase.Remove:
                subscriber.Remove(action.Remove.Symbol);
                break;
            default:
                _logger.LogWarning($"Unknown Action '{action.ActionCase}'.");
                break;
        }
    }
}
```

> [!TIP]
> A instrução `switch` tem um caso `default` que registra um aviso se um valor de `ActionOneOfCase` desconhecido for encontrado. Isso pode ser útil para indicar que um cliente está usando uma versão mais recente do arquivo de `.proto` que adicionou mais ações. Essa é uma razão pela qual o uso de um `switch` é melhor do que o teste para `null` em campos conhecidos.

### <a name="use-the-fullstocktickerservice-from-a-client-application"></a>Usar o FullStockTickerService de um aplicativo cliente

Há um aplicativo .NET Core 3,0 WPF simples para demonstrar o uso desse cliente mais complexo. O aplicativo completo pode ser encontrado [no GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).

O cliente é usado na classe `MainWindowViewModel`, que obtém uma instância do tipo `FullStockTicker.FullStockTickerClient` da injeção de dependência.

```csharp
public class MainWindowViewModel : IAsyncDisposable, INotifyPropertyChanged
{
    private readonly FullStockTicker.FullStockTickerClient _client;
    private readonly AsyncDuplexStreamingCall<ActionMessage, StockTickerUpdate> _duplexStream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _responseTask;
    private string _addSymbol;

    public MainWindowViewModel(FullStockTicker.FullStockTickerClient client)
    {
        _cancellationTokenSource = new CancellationTokenSource();
        _client = client;
        _duplexStream = _client.Subscribe();
        _responseTask = HandleResponsesAsync(_cancellationTokenSource.Token);

        AddCommand = new AsyncCommand(Add, CanAdd);
    }
```

O objeto retornado pelo método `client.Subscribe()` agora é uma instância do tipo de biblioteca gRPC `AsyncDuplexStreamingCall<TRequest, TResponse>`, que fornece um `RequestStream` para enviar solicitações ao servidor e um `ResponseStream` para lidar com as respostas.

O fluxo de solicitação é usado de alguns métodos de `ICommand` do WPF para adicionar e remover símbolos. Para cada operação, defina o campo relevante em um objeto `ActionMessage`:

```csharp
private async Task Add()
{
    if (CanAdd())
    {
        await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Add = new AddSymbolRequest {Symbol = AddSymbol}});
    }
}

public async Task Remove(PriceViewModel priceViewModel)
{
    await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Remove = new RemoveSymbolRequest {Symbol = priceViewModel.Symbol}});
    Prices.Remove(priceViewModel);
}
```

> [!IMPORTANT]
> Definir o valor de um campo de `oneof` em uma mensagem limpa automaticamente todos os campos que foram definidos anteriormente.

O fluxo de respostas é tratado em um método `async` e o `Task` que ele retorna é mantido para ser Descartado quando a janela é fechada.

```csharp
private async Task HandleResponsesAsync(CancellationToken token)
{
    var stream = _duplexStream.ResponseStream;

    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            var price = Prices.FirstOrDefault(p => p.Symbol.Equals(update.Symbol));
            if (price == null)
            {
                price = new PriceViewModel(this) {Symbol = update.Symbol, Price = update.PriceCents / 100m};
                Prices.Add(price);
            }
            else
            {
                price.Price = update.PriceCents / 100m;
            }
        }
    }
    catch (OperationCancelledException) { }
}
```

### <a name="client-clean-up"></a>Limpeza do cliente

Quando a janela é fechada e a `MainWindowViewModel` é descartada (do evento `Closed` de `MainWindow`), é recomendável descartar corretamente o objeto `AsyncDuplexStreamingCall`. Em particular, o método `CompleteAsync` na `RequestStream` deve ser chamado para fechar o fluxo normalmente no servidor. O exemplo a seguir mostra o método `DisposeAsync` do exemplo de exibição-modelo:

```csharp
public ValueTask DisposeAsync()
{
    try
    {
        await _duplexStream.RequestStream.CompleteAsync().ConfigureAwait(false);
        await _responseTask.ConfigureAwait(false);
    }
    finally
    {
        _duplexStream.Dispose();
    }
}
```

O fechamento de fluxos de solicitação permite que o servidor descarte seus próprios recursos em tempo hábil. Isso melhora a eficiência e a escalabilidade dos serviços e impede exceções.

>[!div class="step-by-step"]
>[Anterior](migrate-request-reply.md)
>[Próximo](streaming-versus-repeated.md)
