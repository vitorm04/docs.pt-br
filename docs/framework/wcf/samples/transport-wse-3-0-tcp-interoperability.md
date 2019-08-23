---
title: 'Transporte: interoperabilidade de TCP de WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 9b73f9ef93ebfabf2b1c39363bd64785e2892956
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941026"
---
# <a name="transport-wse-30-tcp-interoperability"></a>Transporte: interoperabilidade de TCP de WSE 3.0
O exemplo de transporte de interoperabilidade TCP do WSE 3,0 demonstra como implementar uma sessão TCP duplex como um transporte de Windows Communication Foundation (WCF) personalizado. Ele também demonstra como você pode usar a extensibilidade da camada de canal para a interface sobre a conexão com os sistemas implantados existentes. As etapas a seguir mostram como criar esse transporte do WCF personalizado:  
  
1. Começando com um soquete TCP, crie implementações de cliente e <xref:System.ServiceModel.Channels.IDuplexSessionChannel> servidor do que usam o enquadramento Dime para delinear os limites da mensagem.  
  
2. Criar uma fábrica de canais que se conecta a um serviço do WSE TCP e envia mensagens em <xref:System.ServiceModel.Channels.IDuplexSessionChannel>quadros por meio dos s do cliente.  
  
3. Crie um ouvinte de canal para aceitar conexões TCP de entrada e produzir canais correspondentes.  
  
4. Certifique-se de que qualquer exceção específica de rede seja normalizada para a classe <xref:System.ServiceModel.CommunicationException>derivada apropriada do.  
  
5. Adicione um elemento Binding que adiciona o transporte personalizado a uma pilha de canais. Para obter mais informações, consulte [adicionando um elemento de associação].  
  
## <a name="creating-iduplexsessionchannel"></a>Criando IDuplexSessionChannel  
 A primeira etapa na escrita do transporte de interoperabilidade de TCP 3,0 do WSE é criar <xref:System.ServiceModel.Channels.IDuplexSessionChannel> uma implementação do no <xref:System.Net.Sockets.Socket>topo de um. `WseTcpDuplexSessionChannel` deriva de <xref:System.ServiceModel.Channels.ChannelBase>. A lógica de envio de uma mensagem consiste em duas partes principais: (1) codificar a mensagem em bytes e (2) enquadramento desses bytes e enviá-los pela conexão.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Além disso, um bloqueio é usado para que as chamadas de envio () preservem a garantia em ordem de IDuplexSessionChannel e que as chamadas para o soquete subjacente sejam sincronizadas corretamente.  
  
 `WseTcpDuplexSessionChannel`usa um <xref:System.ServiceModel.Channels.MessageEncoder> para converter um <xref:System.ServiceModel.Channels.Message> de para e de byte []. Por ser um transporte, `WseTcpDuplexSessionChannel` o também é responsável por aplicar o endereço remoto com o qual o canal foi configurado. `EncodeMessage`encapsula a lógica para essa conversão.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 Depois que <xref:System.ServiceModel.Channels.Message> o é codificado em bytes, ele deve ser transmitido na conexão. Isso requer um sistema para definir limites de mensagens. O WSE 3,0 usa uma versão de [Dime](https://go.microsoft.com/fwlink/?LinkId=94999) como seu protocolo de enquadramento. `WriteData`encapsula a lógica de enquadramento para encapsular um byte [] em um conjunto de registros DIME.  
  
 A lógica para receber mensagens é muito semelhante. A principal complexidade é lidar com o fato de que uma leitura de soquete pode retornar menos bytes do que o necessário. Para receber uma mensagem, `WseTcpDuplexSessionChannel` o lê os bytes de transmissão, decodifica o enquadramento Dime e, em seguida <xref:System.ServiceModel.Channels.MessageEncoder> , usa o para transformar o byte [ <xref:System.ServiceModel.Channels.Message>] em um.  
  
 A base `WseTcpDuplexSessionChannel` pressupõe que ele recebe um Soquete conectado. A classe base lida com o desligamento de soquete. Há três locais que fazem interface com o fechamento de soquete:  
  
- OnAbort--feche o soquete de intensamente (fechamento inadequado).  
  
- Em [início] fechar--fecha o soquete normalmente (fechamento suave).  
  
- sessão. CloseOutputSession ter--desligar o fluxo de dados de saída (metade de perto).  
  
## <a name="channel-factory"></a>Fábrica de canais  
 A próxima etapa na escrita do transporte TCP é criar uma implementação do <xref:System.ServiceModel.Channels.IChannelFactory> para canais de cliente.  
  
- `WseTcpChannelFactory`deriva de <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >. É um alocador que substitui `OnCreateChannel` para produzir canais de cliente.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- `ClientWseTcpDuplexSessionChannel`Adiciona lógica à base `WseTcpDuplexSessionChannel` para se conectar a um servidor TCP no `channel.Open` momento. Primeiro, o nome do host é resolvido para um endereço IP, conforme mostrado no código a seguir.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- Em seguida, o nome do host é conectado ao primeiro endereço IP disponível em um loop, conforme mostrado no código a seguir.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- Como parte do contrato de canal, todas as exceções específicas de domínio são encapsuladas, `SocketException` como <xref:System.ServiceModel.CommunicationException>em.  
  
## <a name="channel-listener"></a>Ouvinte de canal  
 A próxima etapa na escrita do transporte TCP é criar uma implementação do <xref:System.ServiceModel.Channels.IChannelListener> para aceitar canais de servidor.  
  
- `WseTcpChannelListener`deriva de <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > e substituições em [begin] Open e on [begin] Close para controlar o tempo de vida de seu soquete de escuta. Em OnOpen, um soquete é criado para escutar em IP_ANY. Implementações mais avançadas também podem criar um segundo soquete para escutar no IPv6. Eles também podem permitir que o endereço IP seja especificado no nome do host.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Quando um novo soquete é aceito, um canal de servidor é inicializado com esse soquete. Todas as entradas e saídas já estão implementadas na classe base, portanto, esse canal é responsável por inicializar o soquete.  
  
## <a name="adding-a-binding-element"></a>Adicionando um elemento de associação  
 Agora que as fábricas e os canais são criados, eles devem ser expostos ao tempo de execução de ServiceModel por meio de uma associação. Uma associação é uma coleção de elementos de associação que representa a pilha de comunicação associada a um endereço de serviço. Cada elemento na pilha é representado por um elemento de associação.  
  
 No exemplo, o elemento de associação é `WseTcpTransportBindingElement`, que deriva de. <xref:System.ServiceModel.Channels.TransportBindingElement> Ele dá <xref:System.ServiceModel.Channels.IDuplexSessionChannel> suporte e substitui os seguintes métodos para criar as fábricas associadas à nossa associação.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Ele também contém membros para clonar `BindingElement` o e retornar nosso esquema (WSE. TCP).  
  
## <a name="the-wse-tcp-test-console"></a>O console de teste do WSE TCP  
 O código de teste para usar esse transporte de exemplo está disponível em TestCode.cs. As instruções a seguir mostram como configurar o exemplo do `TcpSyncStockService` WSE.  
  
 O código de teste cria uma associação personalizada que usa MTOM como a codificação `WseTcpTransport` e como o transporte. Ele também configura o AddressingVersion para estar em conformidade com o WSE 3,0, conforme mostrado no código a seguir.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 Ele consiste em dois testes – um teste configura um cliente digitado usando o código gerado pelo WSDL do WSE 3,0. O segundo teste usa o WCF como o cliente e o servidor enviando mensagens diretamente sobre as APIs do canal.  
  
 Ao executar o exemplo, a saída a seguir é esperada.  
  
 Cliente:  
  
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
  
 Servidor  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Para executar este exemplo, você deve ter o WSE 3,0 e o `TcpSyncStockService` exemplo do WSE instalados. Você pode baixar o [WSE 3,0 no MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).  
  
> [!NOTE]
> Como o WSE 3,0 não tem suporte [!INCLUDE[lserver](../../../../includes/lserver-md.md)]no, não é possível instalar ou `TcpSyncStockService` executar o exemplo nesse sistema operacional.  
  
1. Depois de instalar o `TcpSyncStockService` exemplo, faça o seguinte:  
  
    1. Abra o `TcpSyncStockService` no Visual Studio (Observe que o exemplo TcpSyncStockService é instalado com o WSE 3,0. Ele não faz parte do código deste exemplo.  
  
    2. Defina o projeto StockService como o projeto de inicialização.  
  
    3. Abra StockService.cs no projeto StockService e comente o atributo [Policy] na `StockService` classe. Isso desabilita a segurança do exemplo. Embora o WCF possa interoperar com pontos de extremidade seguros do WSE 3,0, a segurança está desabilitada para manter este exemplo focado no transporte TCP personalizado.  
  
    4. Pressione F5 para iniciar o `TcpSyncStockService`. O serviço é iniciado em uma nova janela do console.  
  
    5. Abra este exemplo de transporte TCP no Visual Studio.  
  
    6. Atualize a variável "hostname" em TestCode.cs para corresponder ao nome do computador que `TcpSyncStockService`executa o.  
  
    7. Pressione F5 para iniciar o exemplo de transporte TCP.  
  
    8. O cliente de teste de transporte TCP é iniciado em um novo console. O cliente solicita Cotações de ações do serviço e, em seguida, exibe os resultados em sua janela de console.  
