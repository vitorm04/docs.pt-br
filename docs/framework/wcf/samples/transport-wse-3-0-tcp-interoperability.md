---
title: 'Transporte: interoperabilidade de TCP de WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 9b2fcc2e7d96d2cfbb3b55934fa19ec24487bce7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162163"
---
# <a name="transport-wse-30-tcp-interoperability"></a>Transporte: interoperabilidade de TCP de WSE 3.0
O transporte de interoperabilidade de TCP do WSE 3.0 que demonstra como implementar uma sessão duplex do TCP como um transporte personalizado do Windows Communication Foundation (WCF). Ele também demonstra como você pode usar a extensibilidade da camada do canal a interface durante a transmissão com sistemas implantados existentes. As etapas a seguir mostram como criar esse transporte WCF personalizado:  
  
1.  Começando com um soquete TCP, criar implementações de cliente e servidor de <xref:System.ServiceModel.Channels.IDuplexSessionChannel> DIME delimitação de quadros que usam para delinear os limites das mensagens.  
  
2.  Criar uma fábrica de canais que se conecta a um serviço WSE TCP e envia mensagens são enquadradas por cliente <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.  
  
3.  Crie um ouvinte de canais para aceitar conexões TCP de entrada e produzir canais correspondentes.  
  
4.  Certifique-se de que todas as exceções específicas de rede são normalizadas para a classe derivada apropriada de <xref:System.ServiceModel.CommunicationException>.  
  
5.  Adicione um elemento de associação que adiciona o transporte personalizado a uma pilha de canais. Para obter mais informações, consulte [adicionando um elemento de associação].  
  
## <a name="creating-iduplexsessionchannel"></a>Criando IDuplexSessionChannel  
 A primeira etapa ao escrever o transporte de interoperabilidade de TCP do WSE 3.0 é criar uma implementação de <xref:System.ServiceModel.Channels.IDuplexSessionChannel> na parte superior de um <xref:System.Net.Sockets.Socket>. `WseTcpDuplexSessionChannel` Deriva de <xref:System.ServiceModel.Channels.ChannelBase>. A lógica de enviar uma mensagem consiste em duas partes principais: (1) codificar a mensagem em bytes e (2) esses bytes de delimitação de quadros e enviá-los durante a transmissão.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Além disso, um bloqueio é utilizado para que as chamadas de Send () preservam a garantia de em ordem IDuplexSessionChannel e para que as chamadas para o soquete subjacente são sincronizadas corretamente.  
  
 `WseTcpDuplexSessionChannel` usa um <xref:System.ServiceModel.Channels.MessageEncoder> para converter um <xref:System.ServiceModel.Channels.Message> para e de byte []. Porque ele é um transporte `WseTcpDuplexSessionChannel` também é responsável por aplicar o que o canal foi configurado com o endereço remoto. `EncodeMessage` encapsula a lógica para essa conversão.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 Uma vez o <xref:System.ServiceModel.Channels.Message> é codificado em bytes, ele deve ser transmitido durante a transmissão. Isso requer um sistema para definir os limites das mensagens. O WSE 3.0 usa uma versão do [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) como seu protocolo de enquadramento. `WriteData` encapsula a lógica de enquadramento para encapsular um byte [] em um conjunto de registros DIME.  
  
 A lógica para receber mensagens é muito semelhante. A complexidade principal está manipulando o fato de que um soquete de leitura pode retornar menos bytes que foram solicitadas. Para receber uma mensagem `WseTcpDuplexSessionChannel` lê bytes de transmissão, decodifica o enquadramento DIME e, em seguida, usa o <xref:System.ServiceModel.Channels.MessageEncoder> para ativar o byte [] em um <xref:System.ServiceModel.Channels.Message>.  
  
 A base `WseTcpDuplexSessionChannel` pressupõe que ele recebe um soquete conectado. A classe base manipula o desligamento do soquete. Há três locais que têm interface com o fechamento de soquete:  
  
-   OnAbort – fechar o soquete de maneira brusca (disco rígido fechamento).  
  
-   Em [Iniciar] Fechar – fecha o soquete normalmente (reversível fechamento).  
  
-   sessão. CloseOutputSession – desligamento o fluxo de dados de saída (metade fechamento).  
  
## <a name="channel-factory"></a>Fábrica de canais  
 A próxima etapa ao escrever o transporte TCP é criar uma implementação de <xref:System.ServiceModel.Channels.IChannelFactory> para canais de cliente.  
  
-   `WseTcpChannelFactory` deriva <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >. É uma fábrica que substitui `OnCreateChannel` para produzir canais de cliente.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   `ClientWseTcpDuplexSessionChannel` Adiciona a lógica para a base `WseTcpDuplexSessionChannel` para se conectar a um servidor TCP em `channel.Open` tempo. Primeiro, o nome do host é resolvido para um endereço IP, conforme mostrado no código a seguir.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   Em seguida, o nome do host está conectado ao primeiro endereço IP disponível em um loop, conforme mostrado no código a seguir.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   Como parte do contrato de canal, todas as exceções específicas de domínio são encapsuladas, tais como `SocketException` em <xref:System.ServiceModel.CommunicationException>.  
  
## <a name="channel-listener"></a>Ouvinte de canais  
 A próxima etapa ao escrever o transporte TCP é criar uma implementação de <xref:System.ServiceModel.Channels.IChannelListener> para aceitar canais de servidor.  
  
-   `WseTcpChannelListener` deriva <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > e substituições abrir [Iniciar] e [Iniciar] Fechar para controlam o tempo de vida do seu soquete de escuta. OnOpen, um soquete é criado para escutar em IP_ANY. Implementações mais avançadas podem criar um soquete de segundo para escutar em IPv6 também. Eles também podem permitir que o endereço IP a ser especificado no nome do host.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Quando um novo soquete é aceito, um canal de servidor é inicializado com este soquete. Entrada e saída já é implementado na classe base, portanto, esse canal é responsável por inicializar o soquete.  
  
## <a name="adding-a-binding-element"></a>Adicionando um elemento de associação  
 Agora que os canais e fábricas são criados, eles devem ser expostos no tempo de execução de ServiceModel por meio de uma associação. Uma associação é uma coleção de elementos de associação que representa a pilha de comunicação associada com um endereço de serviço. Cada elemento da pilha é representado por um elemento de associação.  
  
 No exemplo, é o elemento de associação `WseTcpTransportBindingElement`, que é derivada de <xref:System.ServiceModel.Channels.TransportBindingElement>. Ele dá suporte a <xref:System.ServiceModel.Channels.IDuplexSessionChannel> e substitui os seguintes métodos para compilar as fábricas associadas à nossa associação.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Ele também contém membros para clonagem de `BindingElement` e retornando o nosso esquema (wse.tcp).  
  
## <a name="the-wse-tcp-test-console"></a>O Console de teste do TCP do WSE  
 Código de teste para usar esse transporte de exemplo está disponível no TestCode.cs. As instruções a seguir mostram como configurar o WSE `TcpSyncStockService` exemplo.  
  
 O código de teste cria uma associação personalizada que usa o MTOM como a codificação e `WseTcpTransport` como o transporte. Ele também configura o AddressingVersion em conformidade com o WSE 3.0, conforme mostrado no código a seguir.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 Ele consiste em dois testes — um teste configura um cliente com tipo usando o código gerado a partir de WSDL WSE 3.0. O segundo teste usa o WCF como o cliente e o servidor ao enviar mensagens diretamente sobre o canal de APIs.  
  
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
  
1.  Para executar este exemplo, você deve ter o WSE 3.0 e o WSE `TcpSyncStockService` exemplo instalado. Você pode baixar [WSE 3.0 do MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).  
  
> [!NOTE]
>  Porque o WSE 3.0 não é compatível com [!INCLUDE[lserver](../../../../includes/lserver-md.md)], você não pode instalar ou executar o `TcpSyncStockService` exemplo nesse sistema operacional.  
  
1.  Depois de instalar o `TcpSyncStockService` de exemplo, faça o seguinte:  
  
    1.  Abra o `TcpSyncStockService` no Visual Studio (Observe que o exemplo de TcpSyncStockService é instalado com o WSE 3.0. Não é parte do código de trabalho deste exemplo).  
  
    2.  Defina o projeto de StockService como o projeto de inicialização.  
  
    3.  Abra StockService.cs no projeto StockService e comente o atributo [política] no `StockService` classe. Isso desabilita a segurança do exemplo. Enquanto o WCF pode interoperar com pontos de extremidade seguros do WSE 3.0, a segurança é desabilitada para manter esse exemplo enfoca o transporte TCP personalizado.  
  
    4.  Pressione F5 para iniciar o `TcpSyncStockService`. O serviço é iniciado em uma nova janela do console.  
  
    5.  Abra esse exemplo de transporte TCP no Visual Studio.  
  
    6.  Atualizar a variável "hostname" em TestCode.cs para coincidir com a execução de nome de máquina a `TcpSyncStockService`.  
  
    7.  Pressione F5 para iniciar a amostra de transporte TCP.  
  
    8.  O cliente de teste do transporte TCP é iniciado em um novo console. O cliente solicita cotações de ações do serviço e, em seguida, exibe os resultados na sua janela de console.  
