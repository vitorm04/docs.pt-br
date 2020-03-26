---
title: Tipos de RPC - gRPC para desenvolvedores WCF
description: Uma revisão dos tipos de chamada de procedimento remoto suportado pelo WCF e seus equivalentes em gRPC
ms.date: 09/02/2019
ms.openlocfilehash: 40c0779dc015904e9dabbb448075e3c5aa5dc49a
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111082"
---
# <a name="types-of-rpc"></a>Tipos de RPC

Como um desenvolvedor do Windows Communication Foundation (WCF), você provavelmente está acostumado a lidar com os seguintes tipos de chamada de procedimento remoto (RPC):

- Solicitação/resposta
- Duplex:
  - Duplex unidirecional com sessão
  - Duplex completo com sessão
- Unidirecional

É possível mapear esses tipos de RPC de forma bastante natural aos conceitos de gRPC existentes. Este capítulo analisará cada uma dessas áreas por sua vez. [O capítulo 5](migrate-wcf-to-grpc.md) explorará exemplos semelhantes em maior profundidade.

| WCF | gRPC |
| --- | ---- |
| Solicitação/resposta regular | Unário |
| Serviço duplex com sessão usando uma interface de retorno de chamada do cliente | Streaming de servidor |
| Serviço full duplex com sessão | Streaming bidirecional |
| Operações unidirecionais | Streaming de clientes |

## <a name="requestreply"></a>Solicitação/resposta

Para métodos simples de solicitação/resposta que pegam e devolvem pequenas quantidades de dados, use o padrão gRPC mais simples, o RPC unary.

```protobuf
service Things {
    rpc Get(GetThingRequest) returns (GetThingResponse);
}
```

```csharp
public class ThingService : Things.ThingsBase
{
    public override async Task<GetThingResponse> Get(GetThingRequest request, ServerCallContext context)
    {
        // Get thing from database
        return new GetThingResponse { Thing = thing };
    }
}
```

```csharp
public async Task ShowThing(int thingId)
{
    var thing = await _thingsClient.GetAsync(new GetThingRequest { ThingId = thingId });
    Console.WriteLine($"{thing.Name}");
}
```

Como você pode ver, a implementação de um método de serviço RPC unary gRPC é semelhante à implementação de uma operação WCF. A diferença é que, com o gRPC, você anula um método de classe base em vez de implementar uma interface. No servidor, os métodos base <xref:System.Threading.Tasks.Task%601>gRPC sempre retornam, embora o cliente forneça métodos de sincronia e bloqueio para chamar o serviço.

## <a name="wcf-duplex-one-way-to-client"></a>WCF duplex, uma maneira de cliente

Os aplicativos WCF (com certas vinculações) podem criar uma conexão persistente entre cliente e servidor. O servidor pode enviar dados assíncronamente ao cliente até que a conexão <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> seja fechada, usando uma interface de retorno de *chamada* especificada na propriedade.

Os serviços gRPC fornecem funcionalidade semelhante com fluxos de mensagens. Os fluxos não mapeiam *exatamente* os serviços duplex wcf em termos de implementação, mas você pode alcançar os mesmos resultados.

### <a name="grpc-streaming"></a>streaming gRPC

O gRPC suporta a criação de fluxos persistentes de cliente para servidor e de servidor para cliente. Ambos os tipos de fluxo podem estar ativos simultaneamente. Essa habilidade é chamada de streaming bidirecional.

Você pode usar fluxos para mensagens arbitrárias e assíncronas ao longo do tempo. Ou você pode usá-los para passar grandes conjuntos de dados que são grandes demais para gerar e enviar uma única solicitação ou resposta.

O exemplo a seguir mostra um RPC de streaming de servidor.

```protobuf
service ClockStreamer {
    rpc Subscribe(ClockSubscribeRequest) returns (stream ClockMessage);
}
```

```csharp
public class ClockStreamerService : ClockStreamer.ClockStreamerBase
{
    public override async Task Subscribe(ClockSubscribeRequest request,
        IServerStreamWriter<ClockMessage> responseStream,
        ServerCallContext context)
    {
        while (!context.CancellationToken.IsCancellationRequested)
        {
            var time = DateTimeOffset.UtcNow;
            await responseStream.WriteAsync(new ClockMessage { message = $"The time is {time:t}." });
            await Task.Delay(TimeSpan.FromSeconds(10), context.CancellationToken);
        }
    }
}
```

Esse fluxo de servidor pode ser consumido a partir de um aplicativo cliente, conforme mostrado no código a seguir:

```csharp
public async Task TellTheTimeAsync(CancellationToken token)
{
    var channel = GrpcChannel.ForAddress("https://localhost:5001");
    var client = new ClockStreamer.ClockStreamerClient(channel);

    var request = new ClockSubscribeRequest();
    var response = client.Subscribe(request);

    await foreach (var update in response.ResponseStream.ReadAllAsync(token))
    {
        Console.WriteLine(update.Message);
    }
}
```

> [!NOTE]
> Os RPCs de streaming de servidor são úteis para serviços de estilo de assinatura. Eles também são úteis para o envio de grandes conjuntos de dados quando seria ineficiente ou impossível construir todo o conjunto de dados na memória. No entanto, as respostas de `repeated` streaming não são tão rápidas quanto enviar campos em uma única mensagem. Como regra geral, o streaming não deve ser usado para pequenos conjuntos de dados.

### <a name="differences-from-wcf"></a>Diferenças em relação ao WCF

Um serviço duplex WCF usa uma interface de retorno de chamada do cliente que pode ter vários métodos. Um serviço de streaming de servidor gRPC só pode enviar mensagens por um único fluxo. Se você precisar de vários métodos, use um tipo de mensagem com [um campo Qualquer ou um de campo](protobuf-any-oneof.md) para enviar mensagens diferentes e escreva código no cliente para manuseá-las.

No WCF, a classe [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) com a sessão é mantida viva até que a conexão seja encerrada. Vários métodos podem ser chamados dentro da sessão. No gRPC, `Task` o retorno do método de implementação não deve ser concluído até que a conexão seja fechada.

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>Operações unidirecionais wcf e streaming de clientes gRPC

O WCF fornece operações `[OperationContract(IsOneWay = true)]`unidirecionais (marcadas com ) que retornam um reconhecimento específico do transporte. Os métodos de serviço gRPC sempre retornam uma resposta, mesmo que esteja vazia. O cliente deve sempre aguardar essa resposta. Para o estilo "fogo e esquecimento" de mensagens no gRPC, você pode criar um serviço de streaming de clientes.

### <a name="thing_logproto"></a>thing_log.proto

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a>ThingLogService.cs

```csharp
public class ThingLogService : Protos.ThingLog.ThingLogBase
{
    private static readonly ConnectionClosedResponse EmptyResponse = new ConnectionClosedResponse();
    private readonly ILogger<ThingLogService> _logger;
    public ThingLogService(ILogger<ThingLogService> logger)
    {
        _logger = logger;
    }

    public override async Task<CompletedResponse> OpenConnection(IAsyncStreamReader<Thing> requestStream, ServerCallContext context)
    {
        while (await requestStream.MoveNext(context.CancellationToken))
        {
            _logger.LogInformation(requestStream.Current.Description);
        }
        return EmptyResponse;
    }
}
```

### <a name="thinglog-client-example"></a>Exemplo de cliente ThingLog

```csharp
public class ThingLogger : IAsyncDisposable
{
    private readonly ThingLog.ThingLogClient _client;
    private readonly AsyncClientStreamingCall<ThingLogRequest, CompletedResponse> _stream;

    public ThingLogger(ThingLog.ThingLogClient client)
    {
        _client = client;
        _stream = client.OpenConnection();
    }

    public async Task WriteAsync(string description)
    {
        await _stream.RequestStream.WriteAsync(new Thing
        {
            Description = description,
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        _stream.Dispose();
    }
}
```

Você pode usar RPCs de streaming de cliente para mensagens de fogo e esquecimento, como mostrado no exemplo anterior. Você também pode usá-los para enviar conjuntos de dados muito grandes para o servidor. O mesmo aviso sobre desempenho se aplica: `repeated` para conjuntos de dados menores, use campos em mensagens regulares.

## <a name="wcf-full-duplex-services"></a>Serviços full-duplex wcf

A vinculação duplex do WCF suporta várias operações unidirecionais tanto na interface de serviço quanto na interface de retorno de chamada do cliente. Esse suporte permite conversas contínuas entre cliente e servidor. o gRPC suporta algo semelhante com RPCs de streaming bidirecional, onde ambos os parâmetros são marcados com o `stream` modificador.

### <a name="chatproto"></a>chat.proto

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a>ChatterService.cs

```csharp
public class ChatterService : Chatter.ChatterBase
{
    private readonly IChatHub _hub;

    public ChatterService(IChatHub hub)
    {
        _hub = hub;
    }

    public override async Task Connect(IAsyncStreamReader<MessageRequest> requestStream, IServerStreamWriter<MessageResponse> responseStream, ServerCallContext context)
    {
        _hub.MessageReceived += async (sender, args) =>
            await responseStream.WriteAsync(new MessageResponse {Text = args.Message});

        while (await requestStream.MoveNext(context.CancellationToken))
        {
            await _hub.SendAsync(requestStream.Current.Text);
        }
    }
}
```

No exemplo anterior, você pode ver que o método`IAsyncStreamReader<MessageRequest>`de implementação`IServerStreamWriter<MessageResponse>`recebe tanto um fluxo de solicitação ( ) quanto um fluxo de resposta ( ). O método pode ler e escrever mensagens até que a conexão seja fechada.

### <a name="chatter-client"></a>Cliente tagarela

```csharp
public class Chat : IAsyncDisposable
{
    private readonly Chatter.ChatterClient _client;
    private readonly AsyncDuplexStreamingCall<MessageRequest, MessageResponse> _stream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _readTask;

    public Chat(Chatter.ChatterClient client)
    {
        _client = client;
        _stream = _client.Connect();
        _cancellationTokenSource = new CancellationTokenSource();
        _readTask = ReadAsync(_cancellationTokenSource.Token);
    }

    public async Task SendAsync(string message)
    {
        await _stream.RequestStream.WriteAsync(new MessageRequest {Text = message});
    }

    private async Task ReadAsync(CancellationToken token)
    {
        while (await _stream.ResponseStream.MoveNext(token))
        {
            Console.WriteLine(_stream.ResponseStream.Current.Text);
        }
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        await _readTask;
        _stream.Dispose();
    }
}
```

>[!div class="step-by-step"]
>[Próximo](wcf-bindings.md)
>[anterior](metadata.md)
