---
title: Tipos de RPC-gRPC para desenvolvedores do WCF
description: Uma revisão dos tipos de chamada de procedimento remoto com suporte pelo WCF e seus equivalentes no gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: ce5bf03b01dff3f7bb201ff08c9065abc2e58360
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846227"
---
# <a name="types-of-rpc"></a>Tipos de RPC

Como desenvolvedor de Windows Communication Foundation (WCF), você provavelmente está acostumado a lidar com os seguintes tipos de RPC (chamada de procedimento remoto):

- Solicitação/resposta
- Duplex
  - Duplex unidirecional com sessão
  - Full duplex com sessão
- Unidirecional

É possível mapear esses tipos de RPC razoavelmente naturalmente para os conceitos de gRPC existentes e este capítulo examinará cada uma dessas áreas por vez. Exemplos semelhantes serão explorados com uma profundidade muito maior no [capítulo 5](migrate-wcf-to-grpc.md).

| WCF | gRPC |
| --- | ---- |
| Solicitação/resposta regular | Unário |
| Serviço duplex com sessão usando uma interface de retorno de chamada do cliente | Transmissão de servidor |
| Serviço full duplex com sessão | Streaming bidirecional |
| Operações unidirecionais | Streaming de cliente |

## <a name="requestreply"></a>Solicitação/resposta

Para métodos simples de solicitação/resposta que levam e retornam pequenas quantidades de dados, use o padrão gRPC mais simples, o RPC unário.

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

Como você pode ver, a implementação de um método de serviço RPC unário gRPC é muito semelhante à implementação de uma operação do WCF, exceto pelo fato de que com gRPC você substitui um método de classe base em vez de implementar uma interface. Observe que, no servidor, os métodos de base gRPC sempre retornam um <xref:System.Threading.Tasks.Task%601>, embora o cliente forneça métodos assíncronos e de bloqueio para chamar o serviço.

## <a name="wcf-duplex-one-way-to-client"></a>WCF duplex, unidirecional para cliente

Os aplicativos WCF (com determinadas associações) podem criar uma conexão persistente entre cliente e servidor, e o servidor pode enviar dados de forma assíncrona para o cliente até que a conexão seja fechada, usando uma *interface de retorno de chamada* especificada no <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> Propriedade.

os serviços gRPCs fornecem funcionalidade semelhante com fluxos de mensagens. Os fluxos não são mapeados *exatamente* para os serviços do WCF duplex em termos de implementação, mas os mesmos resultados podem ser obtidos.

### <a name="grpc-streaming"></a>streaming de gRPC

o gRPC dá suporte à criação de fluxos persistentes do cliente para o servidor e do servidor para o cliente. Ambos os tipos de fluxo podem estar ativos simultaneamente; Isso é chamado de streaming bidirecional. Os fluxos podem ser usados para mensagens assíncronas arbitrárias ao longo do tempo ou para passar grandes conjuntos de data que são muito grandes para gerar e enviar em uma única solicitação ou resposta.

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

Esse fluxo de servidor pode ser consumido de um aplicativo cliente, conforme mostrado no código a seguir:

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
> As RPCs de streaming de servidor são úteis para serviços de estilo de assinatura e também para enviar conjuntos de grandes volumes de banco de altos quando eles seriam ineficientes ou impossíveis de criar todo o conjunto de linhas na memória. No entanto, as respostas de streaming não são tão rápidas quanto enviar `repeated` campos em uma única mensagem, portanto, como um streaming de regra não deve ser usado para pequenos conjuntos de linhas.

### <a name="differences-to-wcf"></a>Diferenças no WCF

Um serviço do WCF duplex usa uma interface de retorno de chamada do cliente que pode ter vários métodos. Um serviço de streaming do servidor gRPC pode enviar mensagens apenas por meio de um único fluxo. Se você precisar de vários métodos, use um tipo de mensagem com [qualquer campo ou um campo](protobuf-any-oneof.md) para enviar mensagens diferentes e escreva o código no cliente para tratá-los.

No WCF, a classe [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) com a sessão é mantida ativa até que a conexão seja fechada e vários métodos podem ser chamados dentro da sessão. No gRPC, o `Task` retornado pelo método de implementação não deve ser concluído até que a conexão seja fechada.

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>Operações unidirecionais do WCF e streaming de cliente gRPC

O WCF fornece operações unidirecionais (marcadas com `[OperationContract(IsOneWay = true)]`) que retornam uma confirmação específica de transporte. os métodos de serviço gRPC sempre retornam uma resposta, mesmo se estiverem vazios, e o cliente sempre deve esperar essa resposta. Para mensagens de estilo "Fire-and-esqueça" no gRPC, você pode criar um serviço de streaming de cliente.

### <a name="thing_logproto"></a>thing_log. proto

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

Novamente, as RPCs de streaming do cliente podem ser usadas para mensagens de incêndio e esquecer, conforme mostrado no exemplo anterior, mas também para enviar conjuntos de grandes volumes de clientes para o servidor. O mesmo aviso sobre o desempenho se aplica: para conjuntos de valores menores, use `repeated` campos em mensagens regulares.

## <a name="wcf-full-duplex-services"></a>Serviços Full duplex do WCF

A associação duplex do WCF dá suporte a várias operações unidirecionais na interface do serviço e na interface de retorno de chamada do cliente, permitindo conversas contínuas entre o cliente e o servidor. o gRPC dá suporte a algo semelhante com RPCs de streaming bidirecional, em que ambos os parâmetros são marcados com o modificador de `stream`.

### <a name="chatproto"></a>chat. proto

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

No exemplo anterior, você pode ver que o método de implementação recebe um fluxo de solicitação (`IAsyncStreamReader<MessageRequest>`) e um fluxo de resposta (`IServerStreamWriter<MessageResponse>`) e pode ler e gravar mensagens até que a conexão seja fechada.

### <a name="chatter-client"></a>Cliente informativo

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
>[Anterior](wcf-bindings.md)
>[Próximo](metadata.md)
