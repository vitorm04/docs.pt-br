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
# <a name="types-of-rpc"></a><span data-ttu-id="2901a-103">Tipos de RPC</span><span class="sxs-lookup"><span data-stu-id="2901a-103">Types of RPC</span></span>

<span data-ttu-id="2901a-104">Como um desenvolvedor do Windows Communication Foundation (WCF), você provavelmente está acostumado a lidar com os seguintes tipos de chamada de procedimento remoto (RPC):</span><span class="sxs-lookup"><span data-stu-id="2901a-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of remote procedure call (RPC):</span></span>

- <span data-ttu-id="2901a-105">Solicitação/resposta</span><span class="sxs-lookup"><span data-stu-id="2901a-105">Request/reply</span></span>
- <span data-ttu-id="2901a-106">Duplex:</span><span class="sxs-lookup"><span data-stu-id="2901a-106">Duplex:</span></span>
  - <span data-ttu-id="2901a-107">Duplex unidirecional com sessão</span><span class="sxs-lookup"><span data-stu-id="2901a-107">One-way duplex with session</span></span>
  - <span data-ttu-id="2901a-108">Duplex completo com sessão</span><span class="sxs-lookup"><span data-stu-id="2901a-108">Full duplex with session</span></span>
- <span data-ttu-id="2901a-109">Unidirecional</span><span class="sxs-lookup"><span data-stu-id="2901a-109">One-way</span></span>

<span data-ttu-id="2901a-110">É possível mapear esses tipos de RPC de forma bastante natural aos conceitos de gRPC existentes.</span><span class="sxs-lookup"><span data-stu-id="2901a-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts.</span></span> <span data-ttu-id="2901a-111">Este capítulo analisará cada uma dessas áreas por sua vez.</span><span class="sxs-lookup"><span data-stu-id="2901a-111">This chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="2901a-112">[O capítulo 5](migrate-wcf-to-grpc.md) explorará exemplos semelhantes em maior profundidade.</span><span class="sxs-lookup"><span data-stu-id="2901a-112">[Chapter 5](migrate-wcf-to-grpc.md) will explore similar examples in greater depth.</span></span>

| <span data-ttu-id="2901a-113">WCF</span><span class="sxs-lookup"><span data-stu-id="2901a-113">WCF</span></span> | <span data-ttu-id="2901a-114">gRPC</span><span class="sxs-lookup"><span data-stu-id="2901a-114">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="2901a-115">Solicitação/resposta regular</span><span class="sxs-lookup"><span data-stu-id="2901a-115">Regular request/reply</span></span> | <span data-ttu-id="2901a-116">Unário</span><span class="sxs-lookup"><span data-stu-id="2901a-116">Unary</span></span> |
| <span data-ttu-id="2901a-117">Serviço duplex com sessão usando uma interface de retorno de chamada do cliente</span><span class="sxs-lookup"><span data-stu-id="2901a-117">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="2901a-118">Streaming de servidor</span><span class="sxs-lookup"><span data-stu-id="2901a-118">Server streaming</span></span> |
| <span data-ttu-id="2901a-119">Serviço full duplex com sessão</span><span class="sxs-lookup"><span data-stu-id="2901a-119">Full duplex service with session</span></span> | <span data-ttu-id="2901a-120">Streaming bidirecional</span><span class="sxs-lookup"><span data-stu-id="2901a-120">Bidirectional streaming</span></span> |
| <span data-ttu-id="2901a-121">Operações unidirecionais</span><span class="sxs-lookup"><span data-stu-id="2901a-121">One-way operations</span></span> | <span data-ttu-id="2901a-122">Streaming de clientes</span><span class="sxs-lookup"><span data-stu-id="2901a-122">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="2901a-123">Solicitação/resposta</span><span class="sxs-lookup"><span data-stu-id="2901a-123">Request/reply</span></span>

<span data-ttu-id="2901a-124">Para métodos simples de solicitação/resposta que pegam e devolvem pequenas quantidades de dados, use o padrão gRPC mais simples, o RPC unary.</span><span class="sxs-lookup"><span data-stu-id="2901a-124">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

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

<span data-ttu-id="2901a-125">Como você pode ver, a implementação de um método de serviço RPC unary gRPC é semelhante à implementação de uma operação WCF.</span><span class="sxs-lookup"><span data-stu-id="2901a-125">As you can see, implementing a gRPC unary RPC service method is similar to implementing a WCF operation.</span></span> <span data-ttu-id="2901a-126">A diferença é que, com o gRPC, você anula um método de classe base em vez de implementar uma interface.</span><span class="sxs-lookup"><span data-stu-id="2901a-126">The difference is that with gRPC, you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="2901a-127">No servidor, os métodos base <xref:System.Threading.Tasks.Task%601>gRPC sempre retornam, embora o cliente forneça métodos de sincronia e bloqueio para chamar o serviço.</span><span class="sxs-lookup"><span data-stu-id="2901a-127">On the server, gRPC base methods always return <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="2901a-128">WCF duplex, uma maneira de cliente</span><span class="sxs-lookup"><span data-stu-id="2901a-128">WCF duplex, one way to client</span></span>

<span data-ttu-id="2901a-129">Os aplicativos WCF (com certas vinculações) podem criar uma conexão persistente entre cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="2901a-129">WCF applications (with certain bindings) can create a persistent connection between client and server.</span></span> <span data-ttu-id="2901a-130">O servidor pode enviar dados assíncronamente ao cliente até que a conexão <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> seja fechada, usando uma interface de retorno de *chamada* especificada na propriedade.</span><span class="sxs-lookup"><span data-stu-id="2901a-130">The server can asynchronously send data to the client until the connection is closed, by using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="2901a-131">Os serviços gRPC fornecem funcionalidade semelhante com fluxos de mensagens.</span><span class="sxs-lookup"><span data-stu-id="2901a-131">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="2901a-132">Os fluxos não mapeiam *exatamente* os serviços duplex wcf em termos de implementação, mas você pode alcançar os mesmos resultados.</span><span class="sxs-lookup"><span data-stu-id="2901a-132">Streams don't map *exactly* to WCF duplex services in terms of implementation, but you can achieve the same results.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="2901a-133">streaming gRPC</span><span class="sxs-lookup"><span data-stu-id="2901a-133">gRPC streaming</span></span>

<span data-ttu-id="2901a-134">O gRPC suporta a criação de fluxos persistentes de cliente para servidor e de servidor para cliente.</span><span class="sxs-lookup"><span data-stu-id="2901a-134">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="2901a-135">Ambos os tipos de fluxo podem estar ativos simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="2901a-135">Both types of stream can be active concurrently.</span></span> <span data-ttu-id="2901a-136">Essa habilidade é chamada de streaming bidirecional.</span><span class="sxs-lookup"><span data-stu-id="2901a-136">This ability is called bidirectional streaming.</span></span>

<span data-ttu-id="2901a-137">Você pode usar fluxos para mensagens arbitrárias e assíncronas ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="2901a-137">You can use streams for arbitrary, asynchronous messaging over time.</span></span> <span data-ttu-id="2901a-138">Ou você pode usá-los para passar grandes conjuntos de dados que são grandes demais para gerar e enviar uma única solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="2901a-138">Or you can use them for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="2901a-139">O exemplo a seguir mostra um RPC de streaming de servidor.</span><span class="sxs-lookup"><span data-stu-id="2901a-139">The following example shows a server-streaming RPC.</span></span>

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

<span data-ttu-id="2901a-140">Esse fluxo de servidor pode ser consumido a partir de um aplicativo cliente, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="2901a-140">This server stream can be consumed from a client application, as shown in the following code:</span></span>

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
> <span data-ttu-id="2901a-141">Os RPCs de streaming de servidor são úteis para serviços de estilo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="2901a-141">Server-streaming RPCs are useful for subscription-style services.</span></span> <span data-ttu-id="2901a-142">Eles também são úteis para o envio de grandes conjuntos de dados quando seria ineficiente ou impossível construir todo o conjunto de dados na memória.</span><span class="sxs-lookup"><span data-stu-id="2901a-142">They're also useful for sending large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="2901a-143">No entanto, as respostas de `repeated` streaming não são tão rápidas quanto enviar campos em uma única mensagem.</span><span class="sxs-lookup"><span data-stu-id="2901a-143">However, streaming responses isn't as fast as sending `repeated` fields in a single message.</span></span> <span data-ttu-id="2901a-144">Como regra geral, o streaming não deve ser usado para pequenos conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="2901a-144">As a rule, streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-from-wcf"></a><span data-ttu-id="2901a-145">Diferenças em relação ao WCF</span><span class="sxs-lookup"><span data-stu-id="2901a-145">Differences from WCF</span></span>

<span data-ttu-id="2901a-146">Um serviço duplex WCF usa uma interface de retorno de chamada do cliente que pode ter vários métodos.</span><span class="sxs-lookup"><span data-stu-id="2901a-146">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="2901a-147">Um serviço de streaming de servidor gRPC só pode enviar mensagens por um único fluxo.</span><span class="sxs-lookup"><span data-stu-id="2901a-147">A gRPC server-streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="2901a-148">Se você precisar de vários métodos, use um tipo de mensagem com [um campo Qualquer ou um de campo](protobuf-any-oneof.md) para enviar mensagens diferentes e escreva código no cliente para manuseá-las.</span><span class="sxs-lookup"><span data-stu-id="2901a-148">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="2901a-149">No WCF, a classe [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) com a sessão é mantida viva até que a conexão seja encerrada.</span><span class="sxs-lookup"><span data-stu-id="2901a-149">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed.</span></span> <span data-ttu-id="2901a-150">Vários métodos podem ser chamados dentro da sessão.</span><span class="sxs-lookup"><span data-stu-id="2901a-150">Multiple methods can be called within the session.</span></span> <span data-ttu-id="2901a-151">No gRPC, `Task` o retorno do método de implementação não deve ser concluído até que a conexão seja fechada.</span><span class="sxs-lookup"><span data-stu-id="2901a-151">In gRPC, the `Task` that the implementation method returns shouldn't finish until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="2901a-152">Operações unidirecionais wcf e streaming de clientes gRPC</span><span class="sxs-lookup"><span data-stu-id="2901a-152">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="2901a-153">O WCF fornece operações `[OperationContract(IsOneWay = true)]`unidirecionais (marcadas com ) que retornam um reconhecimento específico do transporte.</span><span class="sxs-lookup"><span data-stu-id="2901a-153">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgment.</span></span> <span data-ttu-id="2901a-154">Os métodos de serviço gRPC sempre retornam uma resposta, mesmo que esteja vazia.</span><span class="sxs-lookup"><span data-stu-id="2901a-154">gRPC service methods always return a response, even if it's empty.</span></span> <span data-ttu-id="2901a-155">O cliente deve sempre aguardar essa resposta.</span><span class="sxs-lookup"><span data-stu-id="2901a-155">The client should always await that response.</span></span> <span data-ttu-id="2901a-156">Para o estilo "fogo e esquecimento" de mensagens no gRPC, você pode criar um serviço de streaming de clientes.</span><span class="sxs-lookup"><span data-stu-id="2901a-156">For the "fire-and-forget" style of messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="2901a-157">thing_log.proto</span><span class="sxs-lookup"><span data-stu-id="2901a-157">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="2901a-158">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="2901a-158">ThingLogService.cs</span></span>

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

### <a name="thinglog-client-example"></a><span data-ttu-id="2901a-159">Exemplo de cliente ThingLog</span><span class="sxs-lookup"><span data-stu-id="2901a-159">ThingLog client example</span></span>

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

<span data-ttu-id="2901a-160">Você pode usar RPCs de streaming de cliente para mensagens de fogo e esquecimento, como mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="2901a-160">You can use client-streaming RPCs for fire-and-forget messaging, as shown in the previous example.</span></span> <span data-ttu-id="2901a-161">Você também pode usá-los para enviar conjuntos de dados muito grandes para o servidor.</span><span class="sxs-lookup"><span data-stu-id="2901a-161">You can also use them for sending very large datasets to the server.</span></span> <span data-ttu-id="2901a-162">O mesmo aviso sobre desempenho se aplica: `repeated` para conjuntos de dados menores, use campos em mensagens regulares.</span><span class="sxs-lookup"><span data-stu-id="2901a-162">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="2901a-163">Serviços full-duplex wcf</span><span class="sxs-lookup"><span data-stu-id="2901a-163">WCF full-duplex services</span></span>

<span data-ttu-id="2901a-164">A vinculação duplex do WCF suporta várias operações unidirecionais tanto na interface de serviço quanto na interface de retorno de chamada do cliente.</span><span class="sxs-lookup"><span data-stu-id="2901a-164">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface.</span></span> <span data-ttu-id="2901a-165">Esse suporte permite conversas contínuas entre cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="2901a-165">This support allows ongoing conversations between client and server.</span></span> <span data-ttu-id="2901a-166">o gRPC suporta algo semelhante com RPCs de streaming bidirecional, onde ambos os parâmetros são marcados com o `stream` modificador.</span><span class="sxs-lookup"><span data-stu-id="2901a-166">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="2901a-167">chat.proto</span><span class="sxs-lookup"><span data-stu-id="2901a-167">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="2901a-168">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="2901a-168">ChatterService.cs</span></span>

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

<span data-ttu-id="2901a-169">No exemplo anterior, você pode ver que o método`IAsyncStreamReader<MessageRequest>`de implementação`IServerStreamWriter<MessageResponse>`recebe tanto um fluxo de solicitação ( ) quanto um fluxo de resposta ( ).</span><span class="sxs-lookup"><span data-stu-id="2901a-169">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`).</span></span> <span data-ttu-id="2901a-170">O método pode ler e escrever mensagens até que a conexão seja fechada.</span><span class="sxs-lookup"><span data-stu-id="2901a-170">The method can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="2901a-171">Cliente tagarela</span><span class="sxs-lookup"><span data-stu-id="2901a-171">Chatter client</span></span>

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
><span data-ttu-id="2901a-172">[Próximo](wcf-bindings.md)
>[anterior](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="2901a-172">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
