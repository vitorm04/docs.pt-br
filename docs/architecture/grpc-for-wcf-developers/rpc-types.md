---
title: Tipos de RPC-gRPC para desenvolvedores do WCF
description: Uma revisão dos tipos de chamada de procedimento remoto com suporte pelo WCF e seus equivalentes no gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 4fed4ca7fa4ae6a0f861185719917ff0ed5929fd
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184158"
---
# <a name="types-of-rpc"></a><span data-ttu-id="3bdcb-103">Tipos de RPC</span><span class="sxs-lookup"><span data-stu-id="3bdcb-103">Types of RPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="3bdcb-104">Como desenvolvedor de Windows Communication Foundation (WCF), você provavelmente está acostumado a lidar com os seguintes tipos de RPC (chamada de procedimento remoto):</span><span class="sxs-lookup"><span data-stu-id="3bdcb-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of Remote Procedure Call (RPC):</span></span>

- <span data-ttu-id="3bdcb-105">Solicitação/resposta</span><span class="sxs-lookup"><span data-stu-id="3bdcb-105">Request/Reply</span></span>
- <span data-ttu-id="3bdcb-106">Duplex</span><span class="sxs-lookup"><span data-stu-id="3bdcb-106">Duplex:</span></span>
  - <span data-ttu-id="3bdcb-107">Duplex unidirecional com sessão</span><span class="sxs-lookup"><span data-stu-id="3bdcb-107">One-way duplex with session</span></span>
  - <span data-ttu-id="3bdcb-108">Full duplex com sessão</span><span class="sxs-lookup"><span data-stu-id="3bdcb-108">Full duplex with session</span></span>
- <span data-ttu-id="3bdcb-109">Unidirecional</span><span class="sxs-lookup"><span data-stu-id="3bdcb-109">One-way</span></span>

<span data-ttu-id="3bdcb-110">É possível mapear esses tipos de RPC razoavelmente naturalmente para os conceitos de gRPC existentes e este capítulo examinará cada uma dessas áreas por vez.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts and this chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="3bdcb-111">Exemplos semelhantes serão explorados com uma profundidade muito maior no [capítulo 5](migrate-wcf-to-grpc.md).</span><span class="sxs-lookup"><span data-stu-id="3bdcb-111">Similar examples will be explored in much greater depth in [Chapter 5](migrate-wcf-to-grpc.md).</span></span>

| <span data-ttu-id="3bdcb-112">WCF</span><span class="sxs-lookup"><span data-stu-id="3bdcb-112">WCF</span></span> | <span data-ttu-id="3bdcb-113">gRPC</span><span class="sxs-lookup"><span data-stu-id="3bdcb-113">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="3bdcb-114">Solicitação/resposta regular</span><span class="sxs-lookup"><span data-stu-id="3bdcb-114">Regular request/reply</span></span> | <span data-ttu-id="3bdcb-115">Unário</span><span class="sxs-lookup"><span data-stu-id="3bdcb-115">Unary</span></span> |
| <span data-ttu-id="3bdcb-116">Serviço duplex com sessão usando uma interface de retorno de chamada do cliente</span><span class="sxs-lookup"><span data-stu-id="3bdcb-116">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="3bdcb-117">Transmissão de servidor</span><span class="sxs-lookup"><span data-stu-id="3bdcb-117">Server streaming</span></span> |
| <span data-ttu-id="3bdcb-118">Serviço full duplex com sessão</span><span class="sxs-lookup"><span data-stu-id="3bdcb-118">Full duplex service with session</span></span> | <span data-ttu-id="3bdcb-119">Streaming bidirecional</span><span class="sxs-lookup"><span data-stu-id="3bdcb-119">Bidirectional streaming</span></span> |
| <span data-ttu-id="3bdcb-120">Operações unidirecionais</span><span class="sxs-lookup"><span data-stu-id="3bdcb-120">One-way operations</span></span> | <span data-ttu-id="3bdcb-121">Streaming de cliente</span><span class="sxs-lookup"><span data-stu-id="3bdcb-121">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="3bdcb-122">Solicitação/resposta</span><span class="sxs-lookup"><span data-stu-id="3bdcb-122">Request/reply</span></span>

<span data-ttu-id="3bdcb-123">Para métodos simples de solicitação/resposta que levam e retornam pequenas quantidades de dados, use o padrão gRPC mais simples, o RPC unário.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-123">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

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

<span data-ttu-id="3bdcb-124">Como você pode ver, a implementação de um método de serviço RPC unário gRPC é muito semelhante à implementação de uma operação do WCF, exceto pelo fato de que com gRPC você substitui um método de classe base em vez de implementar uma interface.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-124">As you can see, implementing a gRPC unary RPC service method is very similar to implementing a WCF operation, except that with gRPC you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="3bdcb-125">Observe que, no servidor, os métodos de base gRPC sempre <xref:System.Threading.Tasks.Task%601>retornam um, embora o cliente forneça métodos assíncronos e de bloqueio para chamar o serviço.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-125">Note that on the server, gRPC base methods always return a <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="3bdcb-126">WCF duplex, unidirecional para cliente</span><span class="sxs-lookup"><span data-stu-id="3bdcb-126">WCF duplex, one-way to client</span></span>

<span data-ttu-id="3bdcb-127">Os aplicativos WCF (com determinadas associações) podem criar uma conexão persistente entre cliente e servidor, e o servidor pode enviar dados de forma assíncrona para o cliente até que a conexão seja fechada, usando uma interface <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> de retorno de *chamada* especificada no Propriedade.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-127">WCF applications (with certain bindings) can create a persistent connection between client and server, and the server can asynchronously send data to the client until the connection is closed, using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="3bdcb-128">os serviços gRPCs fornecem funcionalidade semelhante com fluxos de mensagens.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-128">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="3bdcb-129">Os fluxos não são mapeados *exatamente* para os serviços do WCF duplex em termos de implementação, mas os mesmos resultados podem ser obtidos.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-129">Streams don't map *exactly* to WCF duplex services in terms of implementation, but the same results can be achieved.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="3bdcb-130">streaming de gRPC</span><span class="sxs-lookup"><span data-stu-id="3bdcb-130">gRPC streaming</span></span>

<span data-ttu-id="3bdcb-131">o gRPC dá suporte à criação de fluxos persistentes do cliente para o servidor e do servidor para o cliente.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-131">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="3bdcb-132">Ambos os tipos de fluxo podem estar ativos simultaneamente; Isso é chamado de streaming bidirecional.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-132">Both types of stream may be active concurrently; this is called bidirectional streaming.</span></span> <span data-ttu-id="3bdcb-133">Os fluxos podem ser usados para mensagens assíncronas arbitrárias ao longo do tempo ou para passar grandes conjuntos de data que são muito grandes para gerar e enviar em uma única solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-133">Streams can be used for arbitrary, asynchronous messaging over time, or for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="3bdcb-134">O exemplo a seguir mostra um RPC de streaming de servidor.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-134">The following example shows a server streaming RPC.</span></span>

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

<span data-ttu-id="3bdcb-135">Esse fluxo de servidor pode ser consumido de um aplicativo cliente, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3bdcb-135">This server stream could be consumed from a client application as shown in the following code:</span></span>

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
> <span data-ttu-id="3bdcb-136">As RPCs de streaming de servidor são úteis para serviços de estilo de assinatura e também para enviar conjuntos de grandes volumes de banco de altos quando eles seriam ineficientes ou impossíveis de criar todo o conjunto de linhas na memória.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-136">Server streaming RPCs are useful for subscription-style services, and also for sending very large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="3bdcb-137">No entanto, as respostas de streaming não `repeated` são tão rápidas quanto enviar campos em uma única mensagem, portanto, como um streaming de regra não deve ser usado para pequenos conjuntos de valores.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-137">However, streaming responses isn't as fast as sending `repeated` fields in a single message, so as a rule streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-to-wcf"></a><span data-ttu-id="3bdcb-138">Diferenças no WCF</span><span class="sxs-lookup"><span data-stu-id="3bdcb-138">Differences to WCF</span></span>

<span data-ttu-id="3bdcb-139">Um serviço do WCF duplex usa uma interface de retorno de chamada do cliente que pode ter vários métodos.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-139">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="3bdcb-140">Um serviço de streaming do servidor gRPC pode enviar mensagens apenas por meio de um único fluxo.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-140">A gRPC server streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="3bdcb-141">Se você precisar de vários métodos, use um tipo de mensagem com [qualquer campo ou um campo](protobuf-any-oneof.md) para enviar mensagens diferentes e escreva o código no cliente para tratá-los.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-141">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="3bdcb-142">No WCF, a classe [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) com a sessão é mantida ativa até que a conexão seja fechada e vários métodos podem ser chamados dentro da sessão.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-142">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed, and multiple methods may be called within the session.</span></span> <span data-ttu-id="3bdcb-143">No gRPC, o `Task` retornado pelo método de implementação não deve ser concluído até que a conexão seja fechada.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-143">In gRPC, the `Task` returned by the implementation method shouldn't complete until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="3bdcb-144">Operações unidirecionais do WCF e streaming de cliente gRPC</span><span class="sxs-lookup"><span data-stu-id="3bdcb-144">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="3bdcb-145">O WCF fornece operações unidirecionais (marcadas com `[OperationContract(IsOneWay = true)]`) que retornam uma confirmação específica de transporte.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-145">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgement.</span></span> <span data-ttu-id="3bdcb-146">os métodos de serviço gRPC sempre retornam uma resposta, mesmo se estiverem vazios, e o cliente sempre deve esperar essa resposta.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-146">gRPC service methods always return a response, even if it's empty, and the client should always await that response.</span></span> <span data-ttu-id="3bdcb-147">Para mensagens de estilo "Fire-and-esqueça" no gRPC, você pode criar um serviço de streaming de cliente.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-147">For "fire-and-forget" style messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="3bdcb-148">thing_log. proto</span><span class="sxs-lookup"><span data-stu-id="3bdcb-148">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="3bdcb-149">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="3bdcb-149">ThingLogService.cs</span></span>

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

### <a name="thinglog-client-example"></a><span data-ttu-id="3bdcb-150">Exemplo de cliente ThingLog</span><span class="sxs-lookup"><span data-stu-id="3bdcb-150">ThingLog client example</span></span>

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

<span data-ttu-id="3bdcb-151">Novamente, as RPCs de streaming do cliente podem ser usadas para mensagens de incêndio e esquecer, conforme mostrado no exemplo anterior, mas também para enviar conjuntos de grandes volumes de clientes para o servidor.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-151">Again, client streaming RPCs can be used for fire-and-forget messaging as shown in the previous example, but also for sending very large datasets to the server.</span></span> <span data-ttu-id="3bdcb-152">O mesmo aviso sobre o desempenho se aplica: para conjuntos de valores `repeated` menores, use campos em mensagens regulares.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-152">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="3bdcb-153">Serviços Full duplex do WCF</span><span class="sxs-lookup"><span data-stu-id="3bdcb-153">WCF full duplex services</span></span>

<span data-ttu-id="3bdcb-154">A associação duplex do WCF dá suporte a várias operações unidirecionais na interface do serviço e na interface de retorno de chamada do cliente, permitindo conversas contínuas entre o cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-154">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface, allowing ongoing conversations between client and server.</span></span> <span data-ttu-id="3bdcb-155">o gRPC dá suporte a algo semelhante com RPCs de streaming bidirecional, em que ambos `stream` os parâmetros são marcados com o modificador.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-155">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="3bdcb-156">chat. proto</span><span class="sxs-lookup"><span data-stu-id="3bdcb-156">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="3bdcb-157">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="3bdcb-157">ChatterService.cs</span></span>

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

<span data-ttu-id="3bdcb-158">No exemplo anterior, você pode ver que o método de implementação recebe um fluxo de solicitação (`IAsyncStreamReader<MessageRequest>`) e um fluxo de resposta`IServerStreamWriter<MessageResponse>`() e pode ler e gravar mensagens até que a conexão seja fechada.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-158">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`), and can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="3bdcb-159">Cliente informativo</span><span class="sxs-lookup"><span data-stu-id="3bdcb-159">Chatter client</span></span>

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
><span data-ttu-id="3bdcb-160">[Anterior](wcf-bindings.md)
>[Próximo](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="3bdcb-160">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
