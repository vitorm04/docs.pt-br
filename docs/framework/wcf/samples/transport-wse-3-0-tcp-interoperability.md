---
title: 'Transporte: interoperabilidade de TCP de WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: b727da998736944afd23f7dcfbf45a1f6049d1d0
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085960"
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="a9501-102">Transporte: interoperabilidade de TCP de WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="a9501-102">Transport: WSE 3.0 TCP Interoperability</span></span>
<span data-ttu-id="a9501-103">O transporte de interoperabilidade de TCP do WSE 3.0 que demonstra como implementar uma sessão duplex do TCP como um transporte personalizado do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a9501-103">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="a9501-104">Ele também demonstra como você pode usar a extensibilidade da camada do canal a interface durante a transmissão com sistemas implantados existentes.</span><span class="sxs-lookup"><span data-stu-id="a9501-104">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="a9501-105">As etapas a seguir mostram como criar esse transporte WCF personalizado:</span><span class="sxs-lookup"><span data-stu-id="a9501-105">The following steps show how to build this custom WCF transport:</span></span>  
  
1.  <span data-ttu-id="a9501-106">Começando com um soquete TCP, criar implementações de cliente e servidor de <xref:System.ServiceModel.Channels.IDuplexSessionChannel> DIME delimitação de quadros que usam para delinear os limites das mensagens.</span><span class="sxs-lookup"><span data-stu-id="a9501-106">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2.  <span data-ttu-id="a9501-107">Criar uma fábrica de canais que se conecta a um serviço WSE TCP e envia mensagens são enquadradas por cliente <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span><span class="sxs-lookup"><span data-stu-id="a9501-107">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3.  <span data-ttu-id="a9501-108">Crie um ouvinte de canais para aceitar conexões TCP de entrada e produzir canais correspondentes.</span><span class="sxs-lookup"><span data-stu-id="a9501-108">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4.  <span data-ttu-id="a9501-109">Certifique-se de que todas as exceções específicas de rede são normalizadas para a classe derivada apropriada de <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="a9501-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5.  <span data-ttu-id="a9501-110">Adicione um elemento de associação que adiciona o transporte personalizado a uma pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="a9501-110">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="a9501-111">Para obter mais informações, consulte [adicionando um elemento de associação].</span><span class="sxs-lookup"><span data-stu-id="a9501-111">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="a9501-112">Criando IDuplexSessionChannel</span><span class="sxs-lookup"><span data-stu-id="a9501-112">Creating IDuplexSessionChannel</span></span>  
 <span data-ttu-id="a9501-113">A primeira etapa ao escrever o transporte de interoperabilidade de TCP do WSE 3.0 é criar uma implementação de <xref:System.ServiceModel.Channels.IDuplexSessionChannel> na parte superior de um <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="a9501-113">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="a9501-114">`WseTcpDuplexSessionChannel` deriva de <xref:System.ServiceModel.Channels.ChannelBase>.</span><span class="sxs-lookup"><span data-stu-id="a9501-114">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="a9501-115">A lógica de enviar uma mensagem consiste em duas partes principais: (1) codificação de mensagem em bytes e (2) esses bytes de delimitação de quadros e enviá-los durante a transmissão.</span><span class="sxs-lookup"><span data-stu-id="a9501-115">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="a9501-116">Além disso, um bloqueio é utilizado para que as chamadas de Send () preservam a garantia de em ordem IDuplexSessionChannel e para que as chamadas para o soquete subjacente são sincronizadas corretamente.</span><span class="sxs-lookup"><span data-stu-id="a9501-116">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="a9501-117">`WseTcpDuplexSessionChannel` usa um <xref:System.ServiceModel.Channels.MessageEncoder> para converter um <xref:System.ServiceModel.Channels.Message> para e de byte [].</span><span class="sxs-lookup"><span data-stu-id="a9501-117">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="a9501-118">Porque ele é um transporte `WseTcpDuplexSessionChannel` também é responsável por aplicar o que o canal foi configurado com o endereço remoto.</span><span class="sxs-lookup"><span data-stu-id="a9501-118">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="a9501-119">`EncodeMessage` encapsula a lógica para essa conversão.</span><span class="sxs-lookup"><span data-stu-id="a9501-119">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="a9501-120">Uma vez o <xref:System.ServiceModel.Channels.Message> é codificado em bytes, ele deve ser transmitido durante a transmissão.</span><span class="sxs-lookup"><span data-stu-id="a9501-120">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="a9501-121">Isso requer um sistema para definir os limites das mensagens.</span><span class="sxs-lookup"><span data-stu-id="a9501-121">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="a9501-122">O WSE 3.0 usa uma versão do [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) como seu protocolo de enquadramento.</span><span class="sxs-lookup"><span data-stu-id="a9501-122">WSE 3.0 uses a version of [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) as its framing protocol.</span></span> <span data-ttu-id="a9501-123">`WriteData` encapsula a lógica de enquadramento para encapsular um byte [] em um conjunto de registros DIME.</span><span class="sxs-lookup"><span data-stu-id="a9501-123">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="a9501-124">A lógica para receber mensagens é muito semelhante.</span><span class="sxs-lookup"><span data-stu-id="a9501-124">The logic for receiving messages is very similar.</span></span> <span data-ttu-id="a9501-125">A complexidade principal está manipulando o fato de que um soquete de leitura pode retornar menos bytes que foram solicitadas.</span><span class="sxs-lookup"><span data-stu-id="a9501-125">The main complexity is handling the fact that a socket read can return less bytes than were requested.</span></span> <span data-ttu-id="a9501-126">Para receber uma mensagem `WseTcpDuplexSessionChannel` lê bytes de transmissão, decodifica o enquadramento DIME e, em seguida, usa o <xref:System.ServiceModel.Channels.MessageEncoder> para ativar o byte [] em um <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="a9501-126">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="a9501-127">A base `WseTcpDuplexSessionChannel` pressupõe que ele recebe um soquete conectado.</span><span class="sxs-lookup"><span data-stu-id="a9501-127">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="a9501-128">A classe base manipula o desligamento do soquete.</span><span class="sxs-lookup"><span data-stu-id="a9501-128">The base class handles socket shutdown.</span></span> <span data-ttu-id="a9501-129">Há três locais que têm interface com o fechamento de soquete:</span><span class="sxs-lookup"><span data-stu-id="a9501-129">There are three places that interface with socket closure:</span></span>  
  
-   <span data-ttu-id="a9501-130">OnAbort – fechar o soquete de maneira brusca (disco rígido fechamento).</span><span class="sxs-lookup"><span data-stu-id="a9501-130">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
-   <span data-ttu-id="a9501-131">Em [Iniciar] Fechar – fecha o soquete normalmente (reversível fechamento).</span><span class="sxs-lookup"><span data-stu-id="a9501-131">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
-   <span data-ttu-id="a9501-132">sessão. CloseOutputSession – desligamento o fluxo de dados de saída (metade fechamento).</span><span class="sxs-lookup"><span data-stu-id="a9501-132">session.CloseOutputSession -- shutdown the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="a9501-133">Fábrica de canais</span><span class="sxs-lookup"><span data-stu-id="a9501-133">Channel Factory</span></span>  
 <span data-ttu-id="a9501-134">A próxima etapa ao escrever o transporte TCP é criar uma implementação de <xref:System.ServiceModel.Channels.IChannelFactory> para canais de cliente.</span><span class="sxs-lookup"><span data-stu-id="a9501-134">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
-   <span data-ttu-id="a9501-135">`WseTcpChannelFactory` deriva <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >.</span><span class="sxs-lookup"><span data-stu-id="a9501-135">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="a9501-136">É uma fábrica que substitui `OnCreateChannel` para produzir canais de cliente.</span><span class="sxs-lookup"><span data-stu-id="a9501-136">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   <span data-ttu-id="a9501-137">`ClientWseTcpDuplexSessionChannel` Adiciona a lógica para a base `WseTcpDuplexSessionChannel` para se conectar a um servidor TCP em `channel.Open` tempo.</span><span class="sxs-lookup"><span data-stu-id="a9501-137">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="a9501-138">Primeiro, o nome do host é resolvido para um endereço IP, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a9501-138">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   <span data-ttu-id="a9501-139">Em seguida, o nome do host está conectado ao primeiro endereço IP disponível em um loop, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a9501-139">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   <span data-ttu-id="a9501-140">Como parte do contrato de canal, todas as exceções específicas de domínio são encapsuladas, tais como `SocketException` em <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="a9501-140">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="a9501-141">Ouvinte de canais</span><span class="sxs-lookup"><span data-stu-id="a9501-141">Channel Listener</span></span>  
 <span data-ttu-id="a9501-142">A próxima etapa ao escrever o transporte TCP é criar uma implementação de <xref:System.ServiceModel.Channels.IChannelListener> para aceitar canais de servidor.</span><span class="sxs-lookup"><span data-stu-id="a9501-142">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
-   <span data-ttu-id="a9501-143">`WseTcpChannelListener` deriva <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > e substituições abrir [Iniciar] e [Iniciar] Fechar para controlam o tempo de vida do seu soquete de escuta.</span><span class="sxs-lookup"><span data-stu-id="a9501-143">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="a9501-144">OnOpen, um soquete é criado para escutar em IP_ANY.</span><span class="sxs-lookup"><span data-stu-id="a9501-144">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="a9501-145">Implementações mais avançadas podem criar um soquete de segundo para escutar em IPv6 também.</span><span class="sxs-lookup"><span data-stu-id="a9501-145">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="a9501-146">Eles também podem permitir que o endereço IP a ser especificado no nome do host.</span><span class="sxs-lookup"><span data-stu-id="a9501-146">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="a9501-147">Quando um novo soquete é aceito, um canal de servidor é inicializado com este soquete.</span><span class="sxs-lookup"><span data-stu-id="a9501-147">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="a9501-148">Entrada e saída já é implementado na classe base, portanto, esse canal é responsável por inicializar o soquete.</span><span class="sxs-lookup"><span data-stu-id="a9501-148">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="a9501-149">Adicionando um elemento de associação</span><span class="sxs-lookup"><span data-stu-id="a9501-149">Adding a Binding Element</span></span>  
 <span data-ttu-id="a9501-150">Agora que os canais e fábricas são criados, eles devem ser expostos no tempo de execução de ServiceModel por meio de uma associação.</span><span class="sxs-lookup"><span data-stu-id="a9501-150">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="a9501-151">Uma associação é uma coleção de elementos de associação que representa a pilha de comunicação associada com um endereço de serviço.</span><span class="sxs-lookup"><span data-stu-id="a9501-151">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="a9501-152">Cada elemento da pilha é representado por um elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="a9501-152">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="a9501-153">No exemplo, é o elemento de associação `WseTcpTransportBindingElement`, que é derivada de <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="a9501-153">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="a9501-154">Ele dá suporte a <xref:System.ServiceModel.Channels.IDuplexSessionChannel> e substitui os seguintes métodos para compilar as fábricas associadas à nossa associação.</span><span class="sxs-lookup"><span data-stu-id="a9501-154">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="a9501-155">Ele também contém membros para clonagem de `BindingElement` e retornando o nosso esquema (wse.tcp).</span><span class="sxs-lookup"><span data-stu-id="a9501-155">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="a9501-156">O Console de teste do TCP do WSE</span><span class="sxs-lookup"><span data-stu-id="a9501-156">The WSE TCP Test Console</span></span>  
 <span data-ttu-id="a9501-157">Código de teste para usar esse transporte de exemplo está disponível no TestCode.cs.</span><span class="sxs-lookup"><span data-stu-id="a9501-157">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="a9501-158">As instruções a seguir mostram como configurar o WSE `TcpSyncStockService` exemplo.</span><span class="sxs-lookup"><span data-stu-id="a9501-158">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="a9501-159">O código de teste cria uma associação personalizada que usa o MTOM como a codificação e `WseTcpTransport` como o transporte.</span><span class="sxs-lookup"><span data-stu-id="a9501-159">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="a9501-160">Ele também configura o AddressingVersion em conformidade com o WSE 3.0, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a9501-160">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="a9501-161">Ele consiste em dois testes — um teste configura um cliente com tipo usando o código gerado a partir de WSDL WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="a9501-161">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="a9501-162">O segundo teste usa o WCF como o cliente e o servidor ao enviar mensagens diretamente sobre o canal de APIs.</span><span class="sxs-lookup"><span data-stu-id="a9501-162">The second test uses WCF as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="a9501-163">Ao executar o exemplo, a seguinte saída é esperada.</span><span class="sxs-lookup"><span data-stu-id="a9501-163">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="a9501-164">Cliente:</span><span class="sxs-lookup"><span data-stu-id="a9501-164">Client:</span></span>  
  
```  
Calling soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Symbol: FABRIKAM  
        Name: Fabrikam, Inc.  
        Last Price: 120  
  
Symbol: CONTOSO  
        Name: Contoso Corp.  
        Last Price: 50.07  
Press enter.  
  
Received Action: http://SayHello  
Received Body: to you.  
Hello to you.  
Press enter.  
  
Received Action: http://NotHello  
Received Body: to me.  
Press enter.  
```  
  
 <span data-ttu-id="a9501-165">Servidor:</span><span class="sxs-lookup"><span data-stu-id="a9501-165">Server:</span></span>  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a9501-166">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="a9501-166">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a9501-167">Para executar este exemplo, você deve ter o WSE 3.0 e o WSE `TcpSyncStockService` exemplo instalado.</span><span class="sxs-lookup"><span data-stu-id="a9501-167">To run this sample, you must have WSE 3.0 and the WSE `TcpSyncStockService` sample installed.</span></span> <span data-ttu-id="a9501-168">Você pode baixar [WSE 3.0 do MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).</span><span class="sxs-lookup"><span data-stu-id="a9501-168">You can download [WSE 3.0 from MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9501-169">Porque o WSE 3.0 não é compatível com [!INCLUDE[lserver](../../../../includes/lserver-md.md)], você não pode instalar ou executar o `TcpSyncStockService` exemplo nesse sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="a9501-169">Because WSE 3.0 is not supported on [!INCLUDE[lserver](../../../../includes/lserver-md.md)], you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1.  <span data-ttu-id="a9501-170">Depois de instalar o `TcpSyncStockService` de exemplo, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a9501-170">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1.  <span data-ttu-id="a9501-171">Abra o `TcpSyncStockService` no Visual Studio (Observe que o exemplo de TcpSyncStockService é instalado com o WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="a9501-171">Open the `TcpSyncStockService` in Visual Studio (Note that the TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="a9501-172">Não é parte do código de trabalho deste exemplo).</span><span class="sxs-lookup"><span data-stu-id="a9501-172">It is not part of this sample's code).</span></span>  
  
    2.  <span data-ttu-id="a9501-173">Defina o projeto de StockService como o projeto de inicialização.</span><span class="sxs-lookup"><span data-stu-id="a9501-173">Set the StockService project as the start up project.</span></span>  
  
    3.  <span data-ttu-id="a9501-174">Abra StockService.cs no projeto StockService e comente o atributo [política] no `StockService` classe.</span><span class="sxs-lookup"><span data-stu-id="a9501-174">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="a9501-175">Isso desabilita a segurança do exemplo.</span><span class="sxs-lookup"><span data-stu-id="a9501-175">This disables security from the sample.</span></span> <span data-ttu-id="a9501-176">Enquanto o WCF pode interoperar com pontos de extremidade seguros do WSE 3.0, a segurança é desabilitada para manter esse exemplo enfoca o transporte TCP personalizado.</span><span class="sxs-lookup"><span data-stu-id="a9501-176">While WCF can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4.  <span data-ttu-id="a9501-177">Pressione F5 para iniciar o `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="a9501-177">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="a9501-178">O serviço é iniciado em uma nova janela do console.</span><span class="sxs-lookup"><span data-stu-id="a9501-178">The service starts in a new console window.</span></span>  
  
    5.  <span data-ttu-id="a9501-179">Abra esse exemplo de transporte TCP no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9501-179">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6.  <span data-ttu-id="a9501-180">Atualizar a variável "hostname" em TestCode.cs para coincidir com a execução de nome de máquina a `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="a9501-180">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7.  <span data-ttu-id="a9501-181">Pressione F5 para iniciar a amostra de transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="a9501-181">Press F5 to start the TCP transport sample.</span></span>  
  
    8.  <span data-ttu-id="a9501-182">O cliente de teste do transporte TCP é iniciado em um novo console.</span><span class="sxs-lookup"><span data-stu-id="a9501-182">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="a9501-183">O cliente solicita cotações de ações do serviço e, em seguida, exibe os resultados na sua janela de console.</span><span class="sxs-lookup"><span data-stu-id="a9501-183">The client requests stock quotes from the service and then displays the results in its console window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9501-184">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9501-184">See Also</span></span>
