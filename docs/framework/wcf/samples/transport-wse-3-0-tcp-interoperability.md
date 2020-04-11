---
title: 'Transporte: interoperabilidade de TCP de WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 55c59fe3a677d3aea8de62ae714e1007cfcbb86a
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121293"
---
# <a name="transport-wse-30-tcp-interoperability"></a>Transporte: interoperabilidade de TCP de WSE 3.0
A amostra wse 3.0 TCP Interoperability Transport demonstra como implementar uma sessão duplex TCP como um transporte personalizado da Windows Communication Foundation (WCF). Ele também demonstra como você pode usar a extensibilidade da camada de canal para interagir sobre o fio com sistemas implantados existentes. As etapas a seguir mostram como construir este transporte WCF personalizado:  
  
1. Começando com um soquete TCP, <xref:System.ServiceModel.Channels.IDuplexSessionChannel> crie implementações de cliente e servidor desse uso de enquadramento DIME para delinear limites de mensagens.  
  
2. Crie uma fábrica de canais que se conecte a um serviço <xref:System.ServiceModel.Channels.IDuplexSessionChannel>WSE TCP e envie mensagens emolduradas sobre o cliente.  
  
3. Crie um ouvinte de canal para aceitar conexões TCP recebidas e produzir canais correspondentes.  
  
4. Certifique-se de que quaisquer exceções específicas da rede <xref:System.ServiceModel.CommunicationException>sejam normalizadas para a classe derivada apropriada de .  
  
5. Adicione um elemento de vinculação que adiciona o transporte personalizado a uma pilha de canais. Para obter mais informações, consulte [Adicionar um elemento de vinculação].  
  
## <a name="creating-iduplexsessionchannel"></a>Criando IDuplexSessionChannel  
 O primeiro passo para escrever o WSE 3.0 TCP Interoperability Transport é criar uma implementação em <xref:System.ServiceModel.Channels.IDuplexSessionChannel> cima de um <xref:System.Net.Sockets.Socket>. `WseTcpDuplexSessionChannel` deriva de <xref:System.ServiceModel.Channels.ChannelBase>. A lógica de enviar uma mensagem consiste em duas peças principais: (1) Codificar a mensagem em bytes, e (2) enquadrar esses bytes e enviá-los no fio.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Além disso, um bloqueio é feito para que as chamadas Send() preservem a garantia de ordem Do IDuplexSessionChannel e, de modo que as chamadas para o soquete subjacente sejam sincronizadas corretamente.  
  
 `WseTcpDuplexSessionChannel`usa <xref:System.ServiceModel.Channels.MessageEncoder> um para <xref:System.ServiceModel.Channels.Message> traduzir a e de byte[]. Por se tratar `WseTcpDuplexSessionChannel` de um transporte, também é responsável pela aplicação do endereço remoto com o que o canal foi configurado. `EncodeMessage`encapsula a lógica para essa conversão.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <xref:System.ServiceModel.Channels.Message> Uma vez codificado em bytes, ele deve ser transmitido no fio. Isso requer um sistema para definir limites de mensagens. O WSE 3.0 usa uma versão do [DIME](https://docs.microsoft.com/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) como seu protocolo de enquadramento. `WriteData`encapsula a lógica de enquadramento para envolver um byte[] em um conjunto de discos DIME.  
  
 A lógica para receber mensagens é muito semelhante. A principal complexidade é lidar com o fato de que uma leitura de soquete pode retornar menos bytes do que foi solicitado. Para receber uma `WseTcpDuplexSessionChannel` mensagem, leia bytes fora do fio, decodifica <xref:System.ServiceModel.Channels.MessageEncoder> o enquadramento DIME e, em seguida, usa o para transformar o byte[] em um <xref:System.ServiceModel.Channels.Message>.  
  
 A `WseTcpDuplexSessionChannel` base pressupõe que recebe um soquete conectado. A classe base lida com o desligamento do soquete. Existem três lugares que interagem com o fechamento do soquete:  
  
- OnAbort - feche o soquete sem graça (fechar com força).  
  
- Em [Start]Close - feche o soquete graciosamente (fechar suave).  
  
- Sessão. CloseOutputSession -- desligue o fluxo de dados de saída (metade perto).  
  
## <a name="channel-factory"></a>Fábrica de canais  
 O próximo passo na redação do transporte <xref:System.ServiceModel.Channels.IChannelFactory> TCP é criar uma implementação para canais de clientes.  
  
- `WseTcpChannelFactory`deriva de <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel>. É uma fábrica que `OnCreateChannel` se sobrepõe à produção de canais clientes.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- `ClientWseTcpDuplexSessionChannel`adiciona lógica à `WseTcpDuplexSessionChannel` base para se conectar `channel.Open` a um servidor TCP no momento. Primeiro, o nome do host é resolvido em um endereço IP, conforme mostrado no código a seguir.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- Em seguida, o nome do host é conectado ao primeiro endereço IP disponível em um loop, conforme mostrado no código a seguir.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- Como parte do contrato de canal, quaisquer exceções `SocketException` específicas <xref:System.ServiceModel.CommunicationException>de domínio são embrulhadas, como em .  
  
## <a name="channel-listener"></a>Ouvinte do Canal  
 O próximo passo na redação do transporte <xref:System.ServiceModel.Channels.IChannelListener> TCP é criar uma implementação para aceitar canais de servidor.  
  
- `WseTcpChannelListener`deriva do <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel> e substitui On[Begin]Open e On[Begin]Close para controlar a vida útil de seu soquete de escuta. No OnOpen, um soquete é criado para ouvir IP_ANY. Implementações mais avançadas podem criar um segundo soquete para ouvir no IPv6 também. Eles também podem permitir que o endereço IP seja especificado no nome do host.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Quando um novo soquete é aceito, um canal de servidor é inicializado com este soquete. Toda a entrada e saída já está implementada na classe base, por isso este canal é responsável pela inicialização do soquete.  
  
## <a name="adding-a-binding-element"></a>Adicionando um elemento de vinculação  
 Agora que as fábricas e canais são construídos, eles devem ser expostos ao tempo de execução serviceModel através de uma vinculação. Uma vinculação é uma coleção de elementos de ligação que representa a pilha de comunicação associada a um endereço de serviço. Cada elemento na pilha é representado por um elemento de ligação.  
  
 Na amostra, o elemento `WseTcpTransportBindingElement`de ligação <xref:System.ServiceModel.Channels.TransportBindingElement>é , que deriva de . Apoia e <xref:System.ServiceModel.Channels.IDuplexSessionChannel> substitui os seguintes métodos para construir as fábricas associadas à nossa vinculação.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Ele também contém membros `BindingElement` para clonagem e devolução do nosso esquema (wse.tcp).  
  
## <a name="the-wse-tcp-test-console"></a>O console de teste WSE TCP  
 O código de teste para o uso deste transporte de amostra está disponível em TestCode.cs. As instruções a seguir mostram `TcpSyncStockService` como configurar a amostra WSE.  
  
 O código de teste cria uma vinculação personalizada `WseTcpTransport` que usa o MTOM como codificação e como transporte. Ele também configura o AddressingVersion para ser conformado com o WSE 3.0, conforme mostrado no código a seguir.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 Ele consiste em dois testes — um teste configura um cliente digitado usando o código gerado a partir do WSE 3.0 WSDL. O segundo teste usa o WCF como cliente e o servidor enviando mensagens diretamente em cima das APIs do canal.  
  
 Ao executar a amostra, espera-se a seguinte saída.  
  
 Cliente:  
  
```console  
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
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Para executar esta amostra, você deve ter [O MSE (Web Services Enhancements) 3.0 para Microsoft .NET](https://www.microsoft.com/download/details.aspx?id=14089) e a amostra WSE `TcpSyncStockService` instalada.
  
> [!NOTE]
> Como o WSE 3.0 não é suportado no Windows Server `TcpSyncStockService` 2008, você não pode instalar ou executar a amostra nesse sistema operacional.  
  
1. Depois de `TcpSyncStockService` instalar a amostra, faça o seguinte:  
  
    1. Abra `TcpSyncStockService` o no Visual Studio (Observe que a amostra TcpSyncStockService está instalada com o WSE 3.0. Não faz parte do código desta amostra).  
  
    2. Defina o projeto StockService como o projeto de inicialinicial.  
  
    3. Abra StockService.cs no projeto StockService e comente o `StockService` atributo [Política] na classe. Isso desativa a segurança da amostra. Embora o WCF possa interoperar com pontos finais seguros do WSE 3.0, a segurança é desativada para manter essa amostra focada no transporte TCP personalizado.  
  
    4. Pressione F5 `TcpSyncStockService`para iniciar o . O serviço começa em uma nova janela do console.  
  
    5. Abra esta amostra de transporte TCP no Visual Studio.  
  
    6. Atualize a variável "hostname" em TestCode.cs `TcpSyncStockService`para corresponder ao nome da máquina executando o .  
  
    7. Pressione F5 para iniciar a amostra de transporte TCP.  
  
    8. O cliente de teste de transporte TCP começa em um novo console. O cliente solicita cotações de ações do serviço e, em seguida, exibe os resultados em sua janela de console.  
