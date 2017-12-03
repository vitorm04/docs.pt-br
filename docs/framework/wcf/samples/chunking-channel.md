---
title: Canal de agrupamento
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2fe0ad62a55c6536b0054aa23ac556b896b02be4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="chunking-channel"></a>Canal de agrupamento
Ao enviar mensagens grandes usando [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], geralmente é desejável para limitar a quantidade de memória usada para armazenar em buffer as mensagens. É uma solução possível transmitir o corpo da mensagem (supondo que a maior parte dos dados está no corpo). No entanto, alguns protocolos exigem armazenamento em buffer da mensagem inteira. Mensagens confiáveis e segurança são dois exemplos como esse. Outra solução possível é dividir a mensagens grandes em mensagens menores chamado partes, enviar parte de um desses blocos em um momento e reconstituir a mensagem grande no lado de recepção. O próprio aplicativo poderia fazer esse agrupamento e eliminação de agrupamento ou use um canal personalizado para fazer isso. O exemplo de canal agrupamento mostra como um protocolo personalizado ou canal em camadas pode ser usado para fazer o agrupamento e a eliminação de agrupamento de mensagens arbitrariamente grandes.  
  
 Agrupamento sempre deve ser empregado somente após a envio da mensagem inteira foi construída. Um canal de agrupamento deve sempre ser colocadas em camadas abaixo de um canal de segurança e um canal de sessão confiável.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a>Limitações e considerações de canal de agrupamento  
  
### <a name="message-structure"></a>Estrutura de mensagens  
 O canal de agrupamento assume a seguinte estrutura de mensagem a ser em bloco de mensagens:  
  
```xml  
<soap:Envelope ...>  
  <!-- headers -->  
  <soap:Body>  
    <operationElement>  
      <paramElement>data to be chunked</paramElement>  
    </operationElement>  
  </soap:Body>  
</soap:Envelope>  
```  
  
 Ao usar o ServiceModel, operações de contrato que têm 1 parâmetro de entrada de acordo com essa forma de mensagem para a mensagem de entrada. Da mesma forma, as operações de contrato que têm 1 parâmetro de saída ou valor de retorno de acordo com essa forma de mensagem para a mensagem de saída. A seguir estão exemplos de tais operações:  
  
```  
[ServiceContract]  
interface ITestService  
{  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
  
    [OperationContract]  
    Stream DownloadStream();  
  
    [OperationContract(IsOneWay = true)]  
    void UploadStream(Stream stream);  
}  
```  
  
### <a name="sessions"></a>Sessões  
 O canal de agrupamento requer que as mensagens sejam entregues exatamente uma vez, na entrega ordenada de mensagens (blocos). Isso significa que a pilha de canais subjacente deve ser sessão. As sessões podem ser fornecidas pelo transporte (por exemplo, o transporte TCP) ou por um canal de protocolo de sessão (por exemplo, ReliableSession canal).  
  
### <a name="asynchronous-send-and-receive"></a>Assíncrono de envio e recebimento  
 Assíncrona enviar e receber métodos não está implementado nesta versão do exemplo das partes do canal.  
  
## <a name="chunking-protocol"></a>Protocolo de agrupamento  
 O canal de agrupamento define um protocolo que indica o início e término de uma série de blocos, bem como o número de sequência de cada parte. As mensagens de exemplo de três a seguir demonstram o início, mensagens de bloco e de término com comentários que descrevem os principais aspectos de cada um.  
  
### <a name="start-message"></a>Mensagem de início  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
<!—Original message action is replaced with a chunking-specific action. -->  
    <a:Action s:mustUnderstand="1">http://samples.microsoft.com/chunkingAction</a:Action>  
<!--  
Original message is assigned a unique id that is transmitted   
in a MessageId header. Note that this is different from the WS-Addressing MessageId header.  
-->  
    <MessageId s:mustUnderstand="1" xmlns="http://samples.microsoft.com/chunking">  
53f183ee-04aa-44a0-b8d3-e45224563109  
</MessageId>  
<!--  
ChunkingStart header signals the start of a chunked message.  
-->  
    <ChunkingStart s:mustUnderstand="1" i:nil="true" xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://samples.microsoft.com/chunking" />  
<!--  
Original message action is transmitted in OriginalAction.  
This is required to re-create the original message on the other side.  
-->  
    <OriginalAction xmlns="http://samples.microsoft.com/chunking">  
http://tempuri.org/ITestService/EchoStream  
    </OriginalAction>  
   <!--  
    All original message headers are included here.  
   -->  
  </s:Header>  
  <s:Body>  
<!--  
Chunking assumes this structure of Body content:  
<element>  
  <childelement>large data to be chunked<childelement>  
</element>  
The start message contains just <element> and <childelement> without  
the data to be chunked.  
-->  
    <EchoStream xmlns="http://tempuri.org/">  
      <stream />  
    </EchoStream>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="chunk-message"></a>O fragmento de mensagem  
  
```xml  
<s:Envelope   
  xmlns:a="http://www.w3.org/2005/08/addressing"   
  xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
   <!--  
    All chunking protocol messages have this action.  
   -->  
    <a:Action s:mustUnderstand="1">  
      http://samples.microsoft.com/chunkingAction  
    </a:Action>  
<!--  
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.  
-->  
    <MessageId s:mustUnderstand="1"   
               xmlns="http://samples.microsoft.com/chunking">  
      53f183ee-04aa-44a0-b8d3-e45224563109  
    </MessageId>  
<!--  
The sequence number of the chunk.  
This number restarts at 1 with each new sequence of chunks.  
-->  
    <ChunkNumber s:mustUnderstand="1"   
                 xmlns="http://samples.microsoft.com/chunking">  
      1096  
    </ChunkNumber>  
  </s:Header>  
  <s:Body>  
<!--  
The chunked data is wrapped in a chunk element.  
The encoding of this data (and the entire message)   
depends on the encoder used. The chunking channel does not mandate an encoding.  
-->  
    <chunk xmlns="http://samples.microsoft.com/chunking">  
kfSr2QcBlkHTvQ==  
    </chunk>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="end-message"></a>Mensagem de término  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://samples.microsoft.com/chunkingAction  
    </a:Action>  
<!--  
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.  
-->  
    <MessageId s:mustUnderstand="1"   
               xmlns="http://samples.microsoft.com/chunking">  
      53f183ee-04aa-44a0-b8d3-e45224563109  
    </MessageId>  
<!--  
ChunkingEnd header signals the end of a chunk sequence.  
-->  
    <ChunkingEnd s:mustUnderstand="1" i:nil="true"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance"   
                 xmlns="http://samples.microsoft.com/chunking" />  
<!--  
ChunkingEnd messages have a sequence number.  
-->  
    <ChunkNumber s:mustUnderstand="1"   
                 xmlns="http://samples.microsoft.com/chunking">  
      79  
    </ChunkNumber>  
  </s:Header>  
  <s:Body>  
<!--  
The ChunkingEnd message has the same <element><childelement> structure  
as the ChunkingStart message.  
-->  
    <EchoStream xmlns="http://tempuri.org/">  
      <stream />  
    </EchoStream>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="chunking-channel-architecture"></a>Arquitetura do canal de agrupamento  
 O canal de agrupamento é um `IDuplexSessionChannel` que, em um nível alto, segue a arquitetura típica do canal. Há um `ChunkingBindingElement` que pode criar um `ChunkingChannelFactory` e um `ChunkingChannelListener`. O `ChunkingChannelFactory` cria instâncias de `ChunkingChannel` quando ele é solicitado. O `ChunkingChannelListener` cria instâncias de `ChunkingChannel` quando um novo canal interno é aceito. O `ChunkingChannel` em si é responsável por enviar e receber mensagens.  
  
 No próximo nível inferior, `ChunkingChannel` depende de vários componentes para implementar o protocolo de agrupamento. No lado de envio, o canal usa um personalizado `XmlDictionaryWriter` chamado `ChunkingWriter` , que faz o agrupamento real. `ChunkingWriter`usa o canal interno diretamente para enviar partes. Usando um personalizado `XmlDictionaryWriter` permite enviar partes como corpo da mensagem original grande está sendo gravado. Isso significa que não armazenar em buffer toda a mensagem original.  
  
 ![Canal de agrupamento](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")  
  
 No lado de recebimento, `ChunkingChannel` recebe mensagens do canal interna e encaminha-os para um personalizado `XmlDictionaryReader` chamado `ChunkingReader`, que reconstitui a mensagem original de partes de entrada. `ChunkingChannel`encapsula isso `ChunkingReader` em um personalizado `Message` implementação chamado `ChunkingMessage` e retorna essa mensagem para a camada acima. Essa combinação de `ChunkingReader` e `ChunkingMessage` permite que a eliminação da parte do corpo da mensagem original que está sendo lido pela camada acima em vez de ter para armazenar em buffer o corpo da mensagem original inteiro. `ChunkingReader`tem uma fila onde ele armazena em buffer partes de entrada até um número configurável máximo das partes do buffer. Quando esse limite máximo for atingido, o leitor aguarda a ser descarregada da fila pela camada acima de mensagens (ou seja, apenas leitura do corpo da mensagem original) ou até que o máximo de receber o tempo limite for atingido.  
  
 ![Canal de agrupamento](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")  
  
## <a name="chunking-programming-model"></a>Modelo de programação de agrupamento  
 Desenvolvedores de serviço podem especificar quais mensagens devem ser em partes, aplicando o `ChunkingBehavior` atributo às operações no contrato. O atributo expõe um `AppliesTo` propriedade que permite ao desenvolvedor especificar se agrupamento aplica-se a mensagem de entrada, a mensagem de saída ou ambos. O exemplo a seguir mostra o uso de `ChunkingBehavior` atributo:  
  
```  
[ServiceContract]  
interface ITestService  
{  
    [OperationContract]  
    [ChunkingBehavior(ChunkingAppliesTo.Both)]  
    Stream EchoStream(Stream stream);  
  
    [OperationContract]  
    [ChunkingBehavior(ChunkingAppliesTo.OutMessage)]  
    Stream DownloadStream();  
  
    [OperationContract(IsOneWay=true)]  
    [ChunkingBehavior(ChunkingAppliesTo.InMessage)]  
    void UploadStream(Stream stream);  
  
}  
```  
  
 Este modelo de programação, o `ChunkingBindingElement` compila uma lista de URIs que identificam as mensagens para ser em partes da ação. A ação de cada mensagem de saída é comparada com essa lista para determinar se a mensagem deve ser em partes ou enviada diretamente.  
  
## <a name="implementing-the-send-operation"></a>Implementando a operação de envio  
 Em um nível alto, a operação de envio primeiro verifica se a mensagem de saída deve ser em bloco e, se não, envia a mensagem diretamente usando o canal interno.  
  
 Se a mensagem deve ser em bloco, enviar cria um novo `ChunkingWriter` e chamadas `WriteBodyContents` na mensagem de saída passando isso `ChunkingWriter`. O `ChunkingWriter` e não o agrupamento de mensagem (incluindo copiando os cabeçalhos da mensagem original para o início de bloco) e envia partes usando o canal interno.  
  
 Alguns detalhes vale a pena observar:  
  
-   Enviar primeiro chama `ThrowIfDisposedOrNotOpened` para garantir que o `CommunicationState` é aberto.  
  
-   Enviar é sincronizado para que apenas uma mensagem possa ser enviada de uma vez para cada sessão. Há um `ManualResetEvent` chamado `sendingDone` que é redefinido quando uma mensagem em partes está sendo enviada. Quando a mensagem de bloco final é enviada, esse evento é definido. O método de envio aguarda para este evento a ser definido antes de tentar enviar a mensagem de saída.  
  
-   Bloqueios de enviar o `CommunicationObject.ThisLock` evitar sincronizadas as alterações de estado durante o envio. Consulte o <xref:System.ServiceModel.Channels.CommunicationObject> documentação para obter mais informações sobre <xref:System.ServiceModel.Channels.CommunicationObject> estados e máquina de estado.  
  
-   O tempo limite transmitido para envio é usado como o tempo limite para a operação de envio inteira que inclui o envio de todas as partes.  
  
-   Personalizado `XmlDictionaryWriter` design foi escolhido para evitar armazenamento em buffer o corpo da mensagem original inteira. Se tivéssemos um `XmlDictionaryReader` no corpo usando `message.GetReaderAtBodyContents` buffer de todo o corpo. Em vez disso, temos um personalizado `XmlDictionaryWriter` que é passado para `message.WriteBodyContents`. Como a mensagem chamadas WriteBase64 no gravador, o gravador empacota partes em mensagens e envia-os usando o canal interno. Blocos de WriteBase64 até que o fragmento é enviado.  
  
## <a name="implementing-the-receive-operation"></a>Implementando a operação de recebimento  
 Em um nível alto, a operação de recebimento primeiro verifica se a mensagem de entrada não é `null` e que a ação é o `ChunkingAction`. Se ele não atender a ambos os critérios, a mensagem é retornada inalterada do recebimento. Caso contrário, cria um novo recebimento `ChunkingReader` e um novo `ChunkingMessage` envolvem (chamando `GetNewChunkingMessage`). Antes de retornar que novos `ChunkingMessage`, Receive usa um thread de pool de threads para executar `ReceiveChunkLoop`, que chama `innerChannel.Receive` em um loop e entrega partes para o `ChunkingReader` até que a mensagem de bloco final é recebida ou o tempo limite de recebimento for atingido.  
  
 Alguns detalhes vale a pena observar:  
  
-   Como enviar, receber chamadas primeiro `ThrowIfDisposedOrNotOepned` para garantir que o `CommunicationState` é aberto.  
  
-   Receber é sincronizada para que apenas uma mensagem pode ser recebida por vez da sessão. Isso é especialmente importante porque quando é recebida uma mensagem de bloco de início, todas as mensagens recebidas subsequentes devem ser partes nesta nova sequência de bloco até receber uma mensagem de bloco final. Receber não pode extrair mensagens do canal interna até que todas as partes que pertencem à mensagem atualmente sendo eliminação bloco sejam recebidas. Para fazer isso, receber usa um `ManualResetEvent` chamado `currentMessageCompleted`, que é definido quando a mensagem de bloco final é recebida e redefinir quando uma nova mensagem de bloco de início é recebida.  
  
-   Ao contrário de envio, Receive não impede que as transições de estado sincronizado durante a recepção. Por exemplo, fechar pode ser chamado durante o recebimento e aguarda até que o recebimento pendente da mensagem original é concluído ou o valor de tempo limite especificado for atingido.  
  
-   O tempo limite transmitido para receber é usado como o tempo limite para toda a operação, que inclui o recebimento de todas as partes de recebimento.  
  
-   Se a camada que consome a mensagem está consumindo o corpo da mensagem a uma taxa menor do que a taxa de bloco de mensagens de entrada, o `ChunkingReader` armazena em buffer os blocos de entrada até o limite especificado pela `ChunkingBindingElement.MaxBufferedChunks`. Quando esse limite é atingido, não há mais blocos são extraídos da camada inferior até que uma parte em buffer é consumida ou o tempo limite de recebimento for atingido.  
  
## <a name="communicationobject-overrides"></a>Substituições de CommunicationObject  
  
### <a name="onopen"></a>AoAbrir  
 `OnOpen`chamadas `innerChannel.Open` para abrir o canal interno.  
  
### <a name="onclose"></a>OnClose  
 `OnClose`primeiro define `stopReceive` para `true` para sinalizar o pendente `ReceiveChunkLoop` para parar. Em seguida, aguarda o `receiveStopped``ManualResetEvent`, que é definido quando `ReceiveChunkLoop` para. Supondo que o `ReceiveChunkLoop` para de dentro do tempo limite especificado, `OnClose` chamadas `innerChannel.Close` com o tempo limite restante.  
  
### <a name="onabort"></a>OnAbort  
 `OnAbort`chamadas `innerChannel.Abort` para anular o canal interno. Se houver um pendente `ReceiveChunkLoop` obtém uma exceção do pendente `innerChannel.Receive` chamar.  
  
### <a name="onfaulted"></a>OnFaulted  
 O `ChunkingChannel` não exige um comportamento especial quando o canal está com defeito isso `OnFaulted` não será substituído.  
  
## <a name="implementing-channel-factory"></a>Implementação de fábrica de canais  
 O `ChunkingChannelFactory` é responsável por criar instâncias de `ChunkingDuplexSessionChannel` e para as transições de estado em cascata para a fábrica interna de canais.  
  
 `OnCreateChannel`usa a fábrica interna de canais para criar um `IDuplexSessionChannel` interna de canais. Em seguida, cria um novo `ChunkingDuplexSessionChannel` passando esse canal interna junto com a lista de ações de mensagem a ser em partes e o número máximo de blocos para armazenar em buffer após o recebimento. A lista de ações de mensagem a ser em partes e o número máximo de blocos para armazenar em buffer são dois parâmetros passados para `ChunkingChannelFactory` em seu construtor. A seção sobre `ChunkingBindingElement` descreve de onde vêm esses valores.  
  
 O `OnOpen`, `OnClose`, `OnAbort` e seus equivalentes assíncronas chamar o método de transição de estado correspondente na fábrica de canais interna.  
  
## <a name="implementing-channel-listener"></a>Implementação de escuta de canal  
 O `ChunkingChannelListener` é um wrapper em torno de um ouvinte de canal interna. Sua função, além de chamadas de delegado para esse ouvinte de canal interna, é usada incluir novos `ChunkingDuplexSessionChannels` em torno de canais aceitos do ouvinte de canal interna. Isso é feito no `OnAcceptChannel` e `OnEndAcceptChannel`. Recém-criado `ChunkingDuplexSessionChannel` é passado interna de canais junto com os outros parâmetros descrito anteriormente.  
  
## <a name="implementing-binding-element-and-binding"></a>Elemento de associação de implementação e associação  
 `ChunkingBindingElement`é responsável pela criação de `ChunkingChannelFactory` e `ChunkingChannelListener`. O `ChunkingBindingElement` verifica se T no `CanBuildChannelFactory` \<T > e `CanBuildChannelListener` \<T > é do tipo `IDuplexSessionChannel` (o canal somente tem suportado pelo canal de agrupamento) e que os outros elementos de associação na associação oferece suporte a isso tipo de canal.  
  
 `BuildChannelFactory`\<T > primeiro verifica se o tipo de canal solicitado pode ser criado e, em seguida, obtém uma lista de ações de mensagem a ser em partes. Para obter mais informações, consulte a seção a seguir. Em seguida, cria um novo `ChunkingChannelFactory` passando a fábrica de canais interna (como retornado pelo `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), a lista de ações de mensagem e o número máximo de blocos para armazenar em buffer. O número máximo de partes vem de uma propriedade chamada `MaxBufferedChunks` exposto pelo `ChunkingBindingElement`.  
  
 `BuildChannelListener<T>`tem uma implementação semelhante para a criação de `ChunkingChannelListener` e passá-lo a escuta de canal interna.  
  
 Há uma associação de exemplo incluída neste exemplo denominada `TcpChunkingBinding`. Essa associação consiste em dois elementos de associação: `TcpTransportBindingElement` e `ChunkingBindingElement`. Além de expor o `MaxBufferedChunks` propriedade, a associação também define alguns do `TcpTransportBindingElement` propriedades como `MaxReceivedMessageSize` (define como `ChunkingUtils.ChunkSize` + 100 KB bytes para cabeçalhos).  
  
 `TcpChunkingBinding`também implementa `IBindingRuntimePreferences` e retorna true do `ReceiveSynchronously` método que indica que apenas as receber chamadas síncronas são implementadas.  
  
### <a name="determining-which-messages-to-chunk"></a>Determinando quais mensagens serão parte  
 O canal de agrupamento blocos somente as mensagens identificadas por meio de `ChunkingBehavior` atributo. O `ChunkingBehavior` classe implementa `IOperationBehavior` e é implementado por chamar o `AddBindingParameter` método. Nesse método, o `ChunkingBehavior` examina o valor de seu `AppliesTo` propriedade (`InMessage`, `OutMessage` ou ambos) para determinar quais mensagens devem ser em partes. Em seguida, obtém a ação de cada uma dessas mensagens (da coleção de mensagens em `OperationDescription`) e adiciona-o a uma coleção de cadeias de caracteres dentro de uma instância do `ChunkingBindingParameter`. Em seguida, adiciona esses `ChunkingBindingParameter` nas `BindingParameterCollection`.  
  
 Isso `BindingParameterCollection` é passado dentro do `BindingContext` para cada elemento de associação na associação quando esse elemento de associação cria a fábrica de canais ou o ouvinte de canal. O `ChunkingBindingElement`da implementação de `BuildChannelFactory<T>` e `BuildChannelListener<T>` puxe `ChunkingBindingParameter` do `BindingContext’`s `BindingParameterCollection`. A coleção de ações contidos o `ChunkingBindingParameter` é então passado para o `ChunkingChannelFactory` ou `ChunkingChannelListener`, que por sua vez passá-lo para o `ChunkingDuplexSessionChannel`.  
  
## <a name="running-the-sample"></a>Executando o exemplo  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Primeiro execute Service.exe, executar Client.exe e assista a ambas as janelas do console de saída.  
  
 Ao executar o exemplo, a seguinte saída é esperada.  
  
 Cliente:  
  
```  
Press enter when service is available  
  
 > Sent chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
```  
  
 Servidor:  
  
```  
Service started, press enter to exit  
 < Received chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
```  
  
## <a name="see-also"></a>Consulte também
