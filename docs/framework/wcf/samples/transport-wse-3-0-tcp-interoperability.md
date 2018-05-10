---
title: 'Transporte: interoperabilidade de TCP de WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 8cdd88b354f2e07c84ccfda85c8552d37ca2f519
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="transport-wse-30-tcp-interoperability"></a>Transporte: interoperabilidade de TCP de WSE 3.0
O transporte de interoperabilidade do WSE 3.0 TCP demonstra como implementar uma sessão duplex TCP como um transporte personalizado do Windows Communication Foundation (WCF). Ele também demonstra como você pode usar a extensibilidade da camada do canal para interface eletronicamente com sistemas implantados existentes. As etapas a seguir mostram como criar esse transporte WCF personalizado:  
  
1.  Começando com um soquete TCP, criar implementações de cliente e servidor de <xref:System.ServiceModel.Channels.IDuplexSessionChannel> que usam DIME quadros para delimitar os limites da mensagem.  
  
2.  Criar uma fábrica de canais que se conecta a um serviço WSE TCP e envia mensagens de enquadramento por cliente <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.  
  
3.  Crie um ouvinte de canal para aceitar conexões TCP de entrada e produzir canais correspondentes.  
  
4.  Certifique-se de que todas as exceções específicas de rede são normalizadas para a classe derivada apropriada de <xref:System.ServiceModel.CommunicationException>.  
  
5.  Adicione um elemento de associação que adiciona o transporte personalizado para uma pilha de canais. Para obter mais informações, consulte [adicionando um elemento de associação].  
  
## <a name="creating-iduplexsessionchannel"></a>Criando IDuplexSessionChannel  
 A primeira etapa na composição o transporte de interoperabilidade do WSE 3.0 TCP é criar uma implementação de <xref:System.ServiceModel.Channels.IDuplexSessionChannel> na parte superior de um <xref:System.Net.Sockets.Socket>. `WseTcpDuplexSessionChannel` deriva de <xref:System.ServiceModel.Channels.ChannelBase>. A lógica de enviar uma mensagem consiste em duas partes principais: (1) codificação da mensagem em bytes e (2) bytes de enquadramento e enviá-los na conexão.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Além disso, um bloqueio é usado para que o Send () chama preserva a garantia de em ordem IDuplexSessionChannel e para que as chamadas para o soquete subjacente estão sincronizadas corretamente.  
  
 `WseTcpDuplexSessionChannel` usa um <xref:System.ServiceModel.Channels.MessageEncoder> para transferir um <xref:System.ServiceModel.Channels.Message> para e de byte []. Porque ele é um transporte `WseTcpDuplexSessionChannel` também é responsável por aplicar o endereço remoto que o canal foi configurado com. `EncodeMessage` encapsula a lógica para essa conversão.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 Uma vez o <xref:System.ServiceModel.Channels.Message> é codificado em bytes, ele deve ser transmitido na conexão. Isso requer um sistema para definir os limites da mensagem. WSE 3.0 usa uma versão do [DIME](http://go.microsoft.com/fwlink/?LinkId=94999) como seu protocolo de enquadramento. `WriteData` encapsula a lógica de quadros para encapsular um byte [] em um conjunto de registros DIME.  
  
 A lógica de recebimento de mensagens é muito semelhante. A complexidade principal está tratando o fato de que um soquete de leitura pode retornar menos bytes que foram solicitadas. Para receber uma mensagem, `WseTcpDuplexSessionChannel` lê bytes na rede, decodifica o enquadramento DIME e, em seguida, usa o <xref:System.ServiceModel.Channels.MessageEncoder> para ativar o byte [] em um <xref:System.ServiceModel.Channels.Message>.  
  
 A base `WseTcpDuplexSessionChannel` pressupõe que ele recebe um soquete conectado. A classe base manipula o desligamento do soquete. Há três locais que têm interface com o fechamento de soquete:  
  
-   OnAbort – fechar o soquete de maneira brusca (disco rígido fechamento).  
  
-   Em [Begin] Fechar – fechar o soquete normalmente (flexível fechamento).  
  
-   sessão. CloseOutputSession – desligamento o fluxo de dados de saída (metade fechamento).  
  
## <a name="channel-factory"></a>Fábrica de canais  
 Gravando o transporte TCP a próxima etapa é criar uma implementação de <xref:System.ServiceModel.Channels.IChannelFactory> de canais de cliente.  
  
-   `WseTcpChannelFactory` deriva <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >. É uma fábrica que substitui `OnCreateChannel` para produzir canais de cliente.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   `ClientWseTcpDuplexSessionChannel` adiciona lógica para a base de `WseTcpDuplexSessionChannel` para se conectar a um servidor TCP em `channel.Open` tempo. Primeiro, o nome do host é resolvido para um endereço IP, conforme mostrado no código a seguir.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   Em seguida, o nome do host está conectado ao primeiro endereço IP disponível em um loop, conforme mostrado no código a seguir.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   Como parte do contrato de canal, todas as exceções específicas de domínio são encapsuladas, como `SocketException` em <xref:System.ServiceModel.CommunicationException>.  
  
## <a name="channel-listener"></a>Ouvinte de canal  
 Gravando o transporte TCP a próxima etapa é criar uma implementação de <xref:System.ServiceModel.Channels.IChannelListener> para aceitar os canais de servidor.  
  
-   `WseTcpChannelListener` deriva <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > e substituições abrir [Begin] e [Begin] Fechar para controlam o tempo de vida de soquete de escuta. OnOpen, um soquete é criado para escutar em IP_ANY. Implementações mais avançadas podem criar um soquete de segundo para escutar em IPv6 também. Eles também podem permitir que o endereço IP seja especificado no nome do host.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Quando um novo soquete é aceito, um canal do servidor é inicializado com este soquete. Todas as entradas e saídas já foi implementado na classe base, portanto, esse canal é responsável por inicializar o soquete.  
  
## <a name="adding-a-binding-element"></a>Adicionando um elemento de associação  
 Agora que fábricas de canais são criados, eles devem ser expostos para o tempo de execução de ServiceModel por meio de uma associação. Uma associação é uma coleção de elementos de associação que representa a pilha de comunicação associada com um endereço de serviço. Cada elemento na pilha é representado por um elemento de associação.  
  
 No exemplo, o elemento de associação é `WseTcpTransportBindingElement`, que é derivado de <xref:System.ServiceModel.Channels.TransportBindingElement>. Ele dá suporte a <xref:System.ServiceModel.Channels.IDuplexSessionChannel> e substitui os seguintes métodos para criar as fábricas associadas nossa associação.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Ele também contém membros para clonagem de `BindingElement` e retornando nosso esquema (wse.tcp).  
  
## <a name="the-wse-tcp-test-console"></a>O Console de teste TCP de WSE  
 Código de teste para usar esse transporte de exemplo está disponível em TestCode.cs. As instruções a seguir mostram como configurar o WSE `TcpSyncStockService` exemplo.  
  
 O código de teste cria uma associação personalizada que usa MTOM como a codificação e `WseTcpTransport` como o transporte. Ele também configura a AddressingVersion para ser compatível com WSE 3.0, conforme mostrado no código a seguir.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 Ele consiste em dois testes — um teste configura um cliente tipado usando o código gerado a partir de WSE 3.0 WSDL. O segundo teste usa o WCF como o cliente e o servidor, enviando mensagens diretamente sobre o canal de APIs.  
  
 Ao executar o exemplo, a seguinte saída é esperada.  
  
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
  
 Servidor:  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Para executar este exemplo, você deve ter WSE 3.0 e o WSE `TcpSyncStockService` exemplo instalado. Você pode baixar [WSE 3.0 do MSDN](http://go.microsoft.com/fwlink/?LinkId=95000).  
  
> [!NOTE]
>  Porque não há suporte para WSE 3.0 em [!INCLUDE[lserver](../../../../includes/lserver-md.md)], você não pode instalar ou executar o `TcpSyncStockService` exemplo nesse sistema operacional.  
  
1.  Depois de instalar o `TcpSyncStockService` de exemplo, faça o seguinte:  
  
    1.  Abra o `TcpSyncStockService` no Visual Studio (Observe que o exemplo TcpSyncStockService é instalado com o WSE 3.0. Não é parte do código neste exemplo).  
  
    2.  Defina o projeto de StockService como o projeto de inicialização.  
  
    3.  Abra StockService.cs no projeto StockService e comente o atributo [política] no `StockService` classe. Isso desabilita a segurança do exemplo. Enquanto o WCF pode interoperar com pontos de extremidade seguros WSE 3.0, a segurança está desabilitada para manter este exemplo voltado para o transporte TCP personalizado.  
  
    4.  Pressione F5 para iniciar o `TcpSyncStockService`. O serviço é iniciado em uma nova janela de console.  
  
    5.  Abra este exemplo de transporte TCP no Visual Studio.  
  
    6.  Atualizar a variável de "nome do host" no TestCode.cs para coincidir com a execução de nome de máquina a `TcpSyncStockService`.  
  
    7.  Pressione F5 para iniciar o exemplo de transporte TCP.  
  
    8.  O cliente de teste de transporte TCP inicia em um novo console. O cliente solicita cotações de ações do serviço e, em seguida, exibe os resultados em sua janela de console.  
  
## <a name="see-also"></a>Consulte também
