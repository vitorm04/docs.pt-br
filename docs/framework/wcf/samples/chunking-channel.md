---
title: Canal de agrupamento
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 9572ad6f88786af34252cea1f3c62d5067257b8b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43470084"
---
# <a name="chunking-channel"></a>Canal de agrupamento
Ao enviar mensagens grandes usando o Windows Communication Foundation (WCF), geralmente é desejável para limitar a quantidade de memória usada para armazenar em buffer as mensagens. Uma solução possível é transmitir o corpo da mensagem (supondo que a maior parte dos dados está no corpo). No entanto, alguns protocolos exigem armazenamento em buffer da mensagem inteira. Sistema de mensagens confiável e segurança são dois exemplos de tais. Outra solução possível é dividir a mensagem grande em mensagens menores chamado partes, enviar partes de uma dessas partes por vez e reconstituir a mensagem grande no lado de recepção. O aplicativo em si pode fazer esse agrupamento e desprovisionamento de agrupamento ou use um canal personalizado para fazê-lo. O exemplo de agrupamento de canal mostra como um protocolo personalizado ou o canal em camadas pode ser usado para fazer a eliminação da divisão de mensagens arbitrariamente grandes e o agrupamento.  
  
 Agrupamento sempre deve ser empregada somente depois que a mensagem inteira seja enviado foi construída. Um canal de agrupamento deve sempre ser colocado em camadas abaixo de um canal de segurança e um canal de sessão confiável.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a>Agrupamento de canal suposições e restrições  
  
### <a name="message-structure"></a>Estrutura de mensagens  
 O canal de agrupamento pressupõe que a seguinte estrutura de mensagem a ser em bloco de mensagens:  
  
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
  
 Ao usar o ServiceModel, operações de contrato que têm um parâmetro de entrada 1 está em conformidade com esta forma de mensagem à mensagem de entrada. Da mesma forma, operações de contrato que tem um parâmetro de saída 1 ou valor de retorno estão em conformidade com esta forma de mensagem à mensagem de saída. A seguir estão exemplos de tais operações:  
  
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
 O canal de agrupamento requer que mensagens sejam entregues exatamente uma vez, na entrega ordenada das mensagens (partes). Isso significa que a pilha de canais subjacente deve ser de sessão. As sessões podem ser fornecidas pelo transporte (por exemplo, o transporte TCP) ou por um canal de protocolo de sessão (por exemplo, ReliableSession canal).  
  
### <a name="asynchronous-send-and-receive"></a>Assíncrona enviar e receber  
 Assíncrona enviar e receber métodos não são implementados nesta versão do exemplo de agrupamento de canal.  
  
## <a name="chunking-protocol"></a>Agrupamento de protocolo  
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
 O canal de agrupamento é um `IDuplexSessionChannel` que, em um alto nível, segue a arquitetura típica de canal. Há um `ChunkingBindingElement` que pode criar um `ChunkingChannelFactory` e um `ChunkingChannelListener`. O `ChunkingChannelFactory` cria instâncias de `ChunkingChannel` quando for solicitado a. O `ChunkingChannelListener` cria instâncias de `ChunkingChannel` quando um novo canal interno é aceito. O `ChunkingChannel` por si só é responsável por enviar e receber mensagens.  
  
 No próximo nível inferior, `ChunkingChannel` depende de vários componentes para implementar o protocolo de agrupamento. No lado do envio, o canal usa um personalizado `XmlDictionaryWriter` chamado `ChunkingWriter` que faz o agrupamento real. `ChunkingWriter` usa o canal interno diretamente para enviar partes. Usando um personalizado `XmlDictionaryWriter` nos permite enviar partes como o corpo da mensagem original grande está sendo gravado. Isso significa que podemos não armazenar em buffer toda a mensagem original.  
  
 ![Canal de agrupamento](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")  
  
 No lado do recebimento, `ChunkingChannel` efetua pull das mensagens do canal interno e passa-os para um personalizado `XmlDictionaryReader` chamado `ChunkingReader`, qual reconstitui a mensagem original das partes de entrada. `ChunkingChannel` resume isso `ChunkingReader` em um personalizado `Message` implementação chamado `ChunkingMessage` e retorna essa mensagem para a camada acima. Essa combinação de `ChunkingReader` e `ChunkingMessage` permite dividir desprovisionar o corpo da mensagem original como ele está sendo lido pela camada acima em vez de precisar armazenar em buffer o corpo da mensagem original inteira. `ChunkingReader` tem uma fila em que ele armazena em buffer partes de entrada até um máximo número configurável de partes em buffer. Quando esse limite máximo for atingido, o leitor aguarda a ser extraído da fila pela camada acima de mensagens (ou seja, lendo apenas do corpo da mensagem original) ou até que receba o máximo tempo limite for atingido.  
  
 ![Canal de agrupamento](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")  
  
## <a name="chunking-programming-model"></a>Modelo de programação de agrupamento  
 Os desenvolvedores de serviço podem especificar quais mensagens devem ser em partes, aplicando o `ChunkingBehavior` de atributo para operações no contrato. O atributo expõe um `AppliesTo` propriedade que permite que o desenvolvedor Especifique se agrupamento se aplica a mensagem de entrada, a mensagem de saída ou ambos. O exemplo a seguir mostra o uso de `ChunkingBehavior` atributo:  
  
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
  
 Do modelo de programação, o `ChunkingBindingElement` compila uma lista de URIs que identificam as mensagens para ser em partes de ação. A ação de cada mensagem de saída é comparada com essa lista para determinar se a mensagem deve ser em partes ou enviada diretamente.  
  
## <a name="implementing-the-send-operation"></a>Implementando a operação de envio  
 Em um alto nível, a operação de envio primeiro verifica se a mensagem de saída deve ser em bloco e, se não, envia a mensagem diretamente usando o canal interno.  
  
 Se a mensagem deve ser em bloco, envio cria um novo `ChunkingWriter` e chama `WriteBodyContents` na mensagem de saída passá-lo isso `ChunkingWriter`. O `ChunkingWriter` e em seguida, faz a divisão de mensagem (incluindo copiar cabeçalhos da mensagem original para a mensagem de bloco de início) e envia partes usando o canal interno.  
  
 Alguns detalhes que vale a pena observar:  
  
-   Enviar primeiro chama `ThrowIfDisposedOrNotOpened` para garantir que o `CommunicationState` é aberto.  
  
-   Enviando é sincronizada para que somente uma mensagem possa ser enviada por vez para cada sessão. Há um `ManualResetEvent` chamado `sendingDone` que é redefinido quando uma mensagem em partes que está sendo enviada. Depois que a mensagem de bloco final é enviada, esse evento é definido. O método de envio aguarda para este evento a ser definido antes de tentar enviar a mensagem de saída.  
  
-   Bloqueios de enviar o `CommunicationObject.ThisLock` evitar sincronizado as alterações de estado durante o envio. Consulte a <xref:System.ServiceModel.Channels.CommunicationObject> documentação para obter mais informações sobre <xref:System.ServiceModel.Channels.CommunicationObject> estados e a máquina de estado.  
  
-   O tempo limite passado para o envio é usado como o tempo limite para a operação de envio inteira que inclui o envio de todos os fragmentos.  
  
-   Personalizado `XmlDictionaryWriter` design foi escolhido para evitar o armazenamento em buffer o corpo da mensagem original inteira. Se tivéssemos uma `XmlDictionaryReader` sobre como usar o corpo `message.GetReaderAtBodyContents` buffer de todo o corpo. Em vez disso, temos um personalizado `XmlDictionaryWriter` que é passado para `message.WriteBodyContents`. Como a mensagem chamadas WriteBase64 no gravador, o gravador de partes em mensagens de pacotes e as envia usando o canal interno. Blocos de WriteBase64 até que a parte seja enviada.  
  
## <a name="implementing-the-receive-operation"></a>Implementando a operação de recebimento  
 Em um alto nível, a operação de recebimento primeiro verifica se a mensagem de entrada não é `null` e que sua ação é o `ChunkingAction`. Se ele não atender a ambos os critérios, a mensagem é retornada inalterada de recebimento. Caso contrário, o recebimento cria um novo `ChunkingReader` e uma nova `ChunkingMessage` encapsulado em torno dele (chamando `GetNewChunkingMessage`). Antes de retornar que novos `ChunkingMessage`, Receive usa um thread de pool de threads para executar `ReceiveChunkLoop`, que chama `innerChannel.Receive` em um loop e entrega o partes para o `ChunkingReader` até que a mensagem de bloco final é recebida ou o tempo limite de recebimento for atingido.  
  
 Alguns detalhes que vale a pena observar:  
  
-   Como enviar, receber chamadas primeiro `ThrowIfDisposedOrNotOepned` para garantir que o `CommunicationState` é aberto.  
  
-   Receba também são sincronizados para que somente uma mensagem pode ser recebida por vez da sessão. Isso é especialmente importante, porque depois que uma mensagem de bloco de início for recebida, todas as mensagens recebidas subsequentes devem ser partes dentro essa nova sequência de bloco até que uma mensagem de bloco final seja recebida. Receber não pode extrair mensagens do canal interno até que todas as partes que pertencem à mensagem atualmente desprovisionar sendo em partes são recebidas. Para fazer isso, receber usa um `ManualResetEvent` denominado `currentMessageCompleted`, que é definido quando a mensagem de bloco final é recebida e redefinir quando uma nova mensagem de bloco de início é recebida.  
  
-   Ao contrário de envio, recebimento não impede que as transições de estado sincronizado durante a recepção. Por exemplo, fechar pode ser chamado durante o recebimento e aguarda até que o recebimento pendente da mensagem original é concluído ou o valor de tempo limite especificado for atingido.  
  
-   O tempo limite passado para o recebimento é usado como o tempo limite para toda a operação, que inclui o recebimento de todas as partes de recebimento.  
  
-   Se a camada que consome a mensagem está consumindo o corpo da mensagem a uma taxa menor do que a taxa de bloco de mensagens de entrada, o `ChunkingReader` buffers essas partes de entrada até o limite especificado pela `ChunkingBindingElement.MaxBufferedChunks`. Quando esse limite é atingido, não há mais blocos são extraídos da camada inferior até que uma parte em buffer é consumida ou o tempo limite de recebimento for atingido.  
  
## <a name="communicationobject-overrides"></a>Substituições de CommunicationObject  
  
### <a name="onopen"></a>AoAbrir  
 `OnOpen` chamadas `innerChannel.Open` para abrir o canal interno.  
  
### <a name="onclose"></a>OnClose  
 `OnClose` primeiro define `stopReceive` à `true` para sinalizar o pendente `ReceiveChunkLoop` para parar. Ele aguarda até que o `receiveStopped``ManualResetEvent`, que é definido quando `ReceiveChunkLoop` para. Supondo que o `ReceiveChunkLoop` para de dentro do tempo limite especificado, `OnClose` chamadas `innerChannel.Close` com o tempo limite restante.  
  
### <a name="onabort"></a>OnAbort  
 `OnAbort` chamadas `innerChannel.Abort` para anular o canal interno. Se não houver um pendente `ReceiveChunkLoop` ele obtém uma exceção a partir de pendente `innerChannel.Receive` chamar.  
  
### <a name="onfaulted"></a>OnFaulted  
 O `ChunkingChannel` não exige um comportamento especial quando o canal está com defeito isso `OnFaulted` não for substituído.  
  
## <a name="implementing-channel-factory"></a>Implementação de fábrica de canais  
 O `ChunkingChannelFactory` é responsável pela criação de instâncias de `ChunkingDuplexSessionChannel` e para as transições de estado em cascata para a fábrica de canais interna.  
  
 `OnCreateChannel` usa a fábrica de canais interna para criar um `IDuplexSessionChannel` canal interno. Em seguida, cria um novo `ChunkingDuplexSessionChannel` passá-lo neste canal interno juntamente com a lista de ações de mensagem a ser em bloco e o número máximo de blocos para armazenar em buffer após o recebimento. A lista de ações de mensagem a ser em bloco e o número máximo de blocos para armazenar em buffer são dois parâmetros passados para `ChunkingChannelFactory` em seu construtor. A seção sobre `ChunkingBindingElement` descreve de onde vêm esses valores.  
  
 O `OnOpen`, `OnClose`, `OnAbort` e seus equivalentes assíncronos chame o método de transição de estado correspondente na fábrica de canais interna.  
  
## <a name="implementing-channel-listener"></a>Implementando o ouvinte de canais  
 O `ChunkingChannelListener` é um wrapper em torno de um ouvinte de canais interna. Sua função principal, além de chamadas de delegados para esse ouvinte de canais interna, é encapsular novo `ChunkingDuplexSessionChannels` em torno de canais aceitos de ouvinte de canais interno. Isso é feito no `OnAcceptChannel` e `OnEndAcceptChannel`. Recém-criado `ChunkingDuplexSessionChannel` é passado o canal interno juntamente com os outros parâmetros descritos anteriormente.  
  
## <a name="implementing-binding-element-and-binding"></a>Implementando o elemento de associação e associação  
 `ChunkingBindingElement` é responsável por criar a `ChunkingChannelFactory` e `ChunkingChannelListener`. O `ChunkingBindingElement` verifica se T no `CanBuildChannelFactory` \<T > e `CanBuildChannelListener` \<T > é do tipo `IDuplexSessionChannel` (o único canal com suporte pelo canal de agrupamento) e que os outros elementos de associação na associação de dar suporte a isso tipo de canal.  
  
 `BuildChannelFactory`\<T > primeiro verifica se o tipo de canal solicitada pode ser compilado e, em seguida, obtém uma lista de ações de mensagem a ser em bloco. Para obter mais informações, consulte a seção a seguir. Em seguida, cria uma nova `ChunkingChannelFactory` passá-lo a fábrica de canais interna (como retornado pelo `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), a lista de ações de mensagem e o número máximo de blocos para armazenar em buffer. O número máximo de partes vem de uma propriedade chamada `MaxBufferedChunks` expostos pelo `ChunkingBindingElement`.  
  
 `BuildChannelListener<T>` tem uma implementação semelhante para a criação de `ChunkingChannelListener` e passando-o ouvinte de canais interna.  
  
 Há uma associação de exemplo incluída neste exemplo denominado `TcpChunkingBinding`. Essa ligação consiste em dois elementos de associação: `TcpTransportBindingElement` e `ChunkingBindingElement`. Além de expor a `MaxBufferedChunks` propriedade, a associação também define algumas da `TcpTransportBindingElement` propriedades, como `MaxReceivedMessageSize` (define como `ChunkingUtils.ChunkSize` + 100 KB bytes para os cabeçalhos).  
  
 `TcpChunkingBinding` também implementa `IBindingRuntimePreferences` e retorna true do `ReceiveSynchronously` método que indica que apenas as receber chamadas síncronas são implementadas.  
  
### <a name="determining-which-messages-to-chunk"></a>Determinando quais mensagens para o fragmento  
 O canal de agrupamento reparte apenas as mensagens identificadas por meio de `ChunkingBehavior` atributo. O `ChunkingBehavior` classe implementa `IOperationBehavior` e é implementado por meio da chamada a `AddBindingParameter` método. Nesse método, o `ChunkingBehavior` examina o valor do seu `AppliesTo` propriedade (`InMessage`, `OutMessage` ou ambos) para determinar quais mensagens devem ser em bloco. Então obtém a ação de cada uma dessas mensagens (da coleção de mensagens no `OperationDescription`) e o adiciona a uma coleção de cadeia de caracteres contida em uma instância do `ChunkingBindingParameter`. Em seguida, adiciona esses `ChunkingBindingParameter` nas `BindingParameterCollection`.  
  
 Isso `BindingParameterCollection` é passado dentro do `BindingContext` a cada elemento de associação na associação quando esse elemento de associação cria a fábrica de canais ou o ouvinte de canais. O `ChunkingBindingElement`da implementação de `BuildChannelFactory<T>` e `BuildChannelListener<T>` puxar isto `ChunkingBindingParameter` fora dos `BindingContext’`s `BindingParameterCollection`. A coleção de ações contidas dentro de `ChunkingBindingParameter` é então passado para o `ChunkingChannelFactory` ou `ChunkingChannelListener`, que por sua vez o passa para o `ChunkingDuplexSessionChannel`.  
  
## <a name="running-the-sample"></a>A execução do exemplo  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Executar Service.exe primeiro, execute Client.exe e assista a ambas as janelas do console de saída.  
  
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
