---
title: Canal de agrupamento
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 7b436e2ce708a122a7eae3b07ad01515fb2dce96
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463973"
---
# <a name="chunking-channel"></a>Canal de agrupamento

Ao enviar grandes mensagens usando o Windows Communication Foundation (WCF), muitas vezes é desejável limitar a quantidade de memória usada para tamponar essas mensagens. Uma solução possível é transmitir o corpo da mensagem (assumindo que a maior parte dos dados está no corpo). No entanto, alguns protocolos requerem o buffer de toda a mensagem. Mensagens confiáveis e segurança são dois exemplos. Outra solução possível é dividir a mensagem grande em mensagens menores chamadas pedaços, enviar esses pedaços um pedaço de cada vez e reconstituir a grande mensagem no lado receptor. O aplicativo em si poderia fazer esse emaque e desparcelamento ou poderia usar um canal personalizado para fazê-lo. A amostra do canal de emparcelamento mostra como um protocolo personalizado ou um canal em camadas podem ser usados para fazer o embigo e desparcelar mensagens arbitrariamente grandes.

O envoluso deve ser sempre empregado somente após a construção de toda a mensagem a ser enviada. Um canal de emparcelamento deve estar sempre em camadas abaixo de um canal de segurança e um canal de sessão confiável.

> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a>Ressupostos e limitações do canal de fatiamento

### <a name="message-structure"></a>Estrutura de mensagens

O canal de emparcelamento assume a seguinte estrutura de mensagem para que as mensagens sejam empedaços:

```xml
<soap:Envelope>
  <!-- headers -->
  <soap:Body>
    <operationElement>
      <paramElement>data to be chunked</paramElement>
    </operationElement>
  </soap:Body>
</soap:Envelope>
```

Ao usar o ServiceModel, as operações de contrato que tenham 1 parâmetro de entrada estão em conformidade com esta forma de mensagem para sua mensagem de entrada. Da mesma forma, as operações de contrato que tenham 1 parâmetro de saída ou valor de retorno cumprem esta forma de mensagem para sua mensagem de saída. A seguir, exemplos de tais operações:

```csharp
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

O canal de emparcelamento exige que as mensagens sejam entregues exatamente uma vez, na entrega ordenada de mensagens (pedaços). Isso significa que a pilha de canais subjacente deve ser sessão. As sessões podem ser fornecidas pelo transporte (por exemplo, transporte TCP) ou por um canal de protocolo de sessão (por exemplo, canal ReliableSession).

### <a name="asynchronous-send-and-receive"></a>Enviado e Receba Assíncrono

Os métodos assíncronos de envio e recebimento não são implementados nesta versão da amostra do canal de emada.

## <a name="chunking-protocol"></a>Protocolo de emada

O canal de emcomamento define um protocolo que indica o início e o fim de uma série de pedaços, bem como o número de seqüência de cada pedaço. As três mensagens de exemplo a seguir demonstram as mensagens de início, pedaço e fim com comentários que descrevem os principais aspectos de cada um.

### <a name="start-message"></a>Iniciar mensagem

```xml
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">
  <s:Header>
<!--Original message action is replaced with a chunking-specific action. -->
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

### <a name="chunk-message"></a>Mensagem de Pedaço

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

### <a name="end-message"></a>Mensagem final

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

## <a name="chunking-channel-architecture"></a>Arquitetura do canal de chunking

O canal de `IDuplexSessionChannel` emada é um que, em alto nível, segue a arquitetura típica do canal. Há um `ChunkingBindingElement` que pode `ChunkingChannelFactory` construir `ChunkingChannelListener`um e um . As `ChunkingChannelFactory` instâncias `ChunkingChannel` de cria de quando é solicitado. As `ChunkingChannelListener` instâncias `ChunkingChannel` de criação de quando um novo canal interno é aceito. O `ChunkingChannel` próprio é responsável pelo envio e recebimento de mensagens.

No próximo nível `ChunkingChannel` para baixo, conta com vários componentes para implementar o protocolo de emada. No lado de envio, o <xref:System.Xml.XmlDictionaryWriter> `ChunkingWriter` canal usa um personalizado chamado que faz o pedaço real. `ChunkingWriter`usa o canal interno diretamente para enviar pedaços. Usar um `XmlDictionaryWriter` costume nos permite enviar pedaços enquanto o grande corpo da mensagem original está sendo escrito. Isso significa que não tamponamos toda a mensagem original.

![Diagrama que mostra a arquitetura de envio de canal de blocos.](./media/chunking-channel/chunking-channel-send.gif)

No lado de `ChunkingChannel` recebimento, puxa mensagens do canal interno <xref:System.Xml.XmlDictionaryReader> `ChunkingReader`e as entrega a um costume chamado , que reconstitui a mensagem original dos pedaços recebidos. `ChunkingChannel`envolve isso `ChunkingReader` em `Message` uma `ChunkingMessage` implementação personalizada chamada e retorna esta mensagem para a camada acima. Essa combinação `ChunkingReader` `ChunkingMessage` e nos permite desmembarar o corpo da mensagem original enquanto ele está sendo lido pela camada acima em vez de ter que tamponar todo o corpo de mensagem original. `ChunkingReader`tem uma fila onde ele tampona os pedaços de entrada até um número máximo configurável de pedaços tamponados. Quando esse limite máximo é atingido, o leitor espera que as mensagens sejam drenadas da fila pela camada acima (ou seja, apenas lendo do corpo da mensagem original) ou até que o tempo máximo de recebimento seja atingido.

![Diagrama que mostra o canal de chunking receber arquitetura.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a>Modelo de programação de fatias

Os desenvolvedores de serviços podem especificar quais `ChunkingBehavior` mensagens devem ser emretoadas aplicando o atributo às operações dentro do contrato. O atributo `AppliesTo` expõe uma propriedade que permite ao desenvolvedor especificar se o pedaço se aplica à mensagem de entrada, à mensagem de saída ou ambos. O exemplo a seguir `ChunkingBehavior` mostra o uso do atributo:

```csharp
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

A partir deste modelo `ChunkingBindingElement` de programação, o compila uma lista de URIs de ação que identificam mensagens a serem emretaladas. A ação de cada mensagem de saída é comparada com esta lista para determinar se a mensagem deve ser empedaços ou enviada diretamente.

## <a name="implementing-the-send-operation"></a>Implementando a Operação Enviar

Em um nível alto, a operação Enviar primeiro verifica se a mensagem de saída deve ser empedaços e, se não, envia a mensagem diretamente usando o canal interno.

Se a mensagem deve ser empedaços, Enviar cria uma nova `ChunkingWriter` e chama `WriteBodyContents` a mensagem de saída passando-a isso `ChunkingWriter`. Em `ChunkingWriter` seguida, faz o pedaço de mensagem (incluindo copiar cabeçalhos de mensagem originais para a mensagem de inicialização) e envia pedaços usando o canal interno.

Alguns detalhes que merecem ser notados:

- Envie as `ThrowIfDisposedOrNotOpened` primeiras `CommunicationState` chamadas para garantir que a abertura seja aberta.

- O envio é sincronizado para que apenas uma mensagem possa ser enviada de cada vez para cada sessão. Há um `ManualResetEvent` `sendingDone` nome que é redefinido quando uma mensagem em pedaços está sendo enviada. Uma vez que a mensagem de bloco final é enviada, este evento é definido. O método Enviar espera que este evento seja definido antes de tentar enviar a mensagem de saída.

- Envie bloqueios `CommunicationObject.ThisLock` para evitar alterações de estado sincronizadas durante o envio. Consulte <xref:System.ServiceModel.Channels.CommunicationObject> a documentação <xref:System.ServiceModel.Channels.CommunicationObject> para obter mais informações sobre estados e máquinas estaduais.

- O tempo de tempo passado para Enviar é usado como o tempo máximo para toda a operação de envio, que inclui o envio de todos os blocos.

- O <xref:System.Xml.XmlDictionaryWriter> design personalizado foi escolhido para evitar o buffer de todo o corpo de mensagem original. Se tivéssemos <xref:System.Xml.XmlDictionaryReader> um no `message.GetReaderAtBodyContents` corpo usando todo o corpo seria tampão. Em vez disso, <xref:System.Xml.XmlDictionaryWriter> temos um `message.WriteBodyContents`costume que é passado para . Como a mensagem chama WriteBase64 no escritor, o escritor empacota pedaços em mensagens e as envia usando o canal interno. WriteBase64 blocos até que o pedaço seja enviado.

## <a name="implementing-the-receive-operation"></a>Implementando a Operação Receber

Em alto nível, a operação Receber primeiro verifica `null` se a mensagem `ChunkingAction`recebida não é e que sua ação é a . Se não atender a ambos os critérios, a mensagem é devolvida inalterada de Receber. Caso contrário, Receive `ChunkingReader` cria um `ChunkingMessage` novo e um `GetNewChunkingMessage`novo emvolta dele (chamando ). Antes de retornar `ChunkingMessage`esse novo , O `ReceiveChunkLoop`Receive usa `innerChannel.Receive` um threadpool para executar `ChunkingReader` , que chama em um loop e entrega pedaços para o até que a mensagem de bloco final seja recebida ou o tempo de recebimento seja atingido.

Alguns detalhes que merecem ser notados:

- Como Enviar, receber `ThrowIfDisposedOrNotOepned` as `CommunicationState` primeiras chamadas para garantir que a abertura seja aberta.

- O recebimento também é sincronizado para que apenas uma mensagem possa ser recebida por vez da sessão. Isso é especialmente importante porque, uma vez que uma mensagem de bloco inicial é recebida, espera-se que todas as mensagens recebidas subseqüentes sejam em pedaços dentro desta nova seqüência de blocos até que uma mensagem de bloco final seja recebida. O receive não pode retirar mensagens do canal interno até que todos os pedaços que pertencem à mensagem que estão sendo desparceladas sejam recebidos. Para isso, o `ManualResetEvent` Receive `currentMessageCompleted`usa um nome , que é definido quando a mensagem de bloco final é recebida e redefinida quando uma nova mensagem de bloco de inicialé é recebida.

- Ao contrário do Send, o Receive não impede transições de estado sincronizadas durante o recebimento. Por exemplo, Fechar pode ser chamado enquanto recebe e espera até que o recebimento pendente da mensagem original seja concluído ou o valor de tempo definido especificado seja atingido.

- O tempo de tempo passado para Receber é usado como o tempo máximo para toda a operação de recebimento, o que inclui o recebimento de todos os blocos.

- Se a camada que consome a mensagem estiver consumindo o corpo de mensagem `ChunkingReader` a uma taxa menor do que a `ChunkingBindingElement.MaxBufferedChunks`taxa de mensagens de bloco recebidas, os buffers serão os blocos de entrada até o limite especificado por . Uma vez que esse limite é atingido, não são mais retirados os pedaços da camada inferior até que um pedaço tamponado seja consumido ou o tempo limite de recebimento seja atingido.

## <a name="communicationobject-overrides"></a>Substituições de objetos de comunicação

### <a name="onopen"></a>Onopen

`OnOpen`chamadas `innerChannel.Open` para abrir o canal interno.

### <a name="onclose"></a>Onclose

`OnClose`os `stopReceive` primeiros `true` conjuntos `ReceiveChunkLoop` para sinalizar a pendência de parar. Em seguida, espera `receiveStopped` <xref:System.Threading.ManualResetEvent>pelo , `ReceiveChunkLoop` que é definido quando pára. Assumindo `ReceiveChunkLoop` as paradas dentro do `OnClose` `innerChannel.Close` intervalo especificado, chamadas com o tempo restante.

### <a name="onabort"></a>Onabort

`OnAbort`chamadas `innerChannel.Abort` para abortar o canal interno. Se houver uma `ReceiveChunkLoop` pendência, ele `innerChannel.Receive` recebe uma exceção da chamada pendente.

### <a name="onfaulted"></a>OnFaulted

O `ChunkingChannel` não requer comportamento especial quando o `OnFaulted` canal é defeituoso, portanto não é substituído.

## <a name="implementing-channel-factory"></a>Fábrica de canais de implementação

O `ChunkingChannelFactory` é responsável por `ChunkingDuplexSessionChannel` criar instâncias de e para transições de estado em cascata para a fábrica de canais internos.

`OnCreateChannel`usa a fábrica de `IDuplexSessionChannel` canais internos para criar um canal interno. Em seguida, `ChunkingDuplexSessionChannel` ele cria um novo passe este canal interno, juntamente com a lista de ações de mensagem a serem emretaladas e o número máximo de pedaços a serem tamponados ao receber. A lista de ações de mensagem a serem redobradas e `ChunkingChannelFactory` o número máximo de pedaços para buffer são dois parâmetros passados em seu construtor. A seção em descreve `ChunkingBindingElement` de onde esses valores vêm.

Os `OnOpen` `OnClose`, `OnAbort` e seus equivalentes assíncronos chamam o método de transição de estado correspondente na fábrica do canal interno.

## <a name="implementing-channel-listener"></a>Implementando ouvinte de canal

O `ChunkingChannelListener` é um invólucro em torno de um ouvinte de canal interno. Sua principal função, além de delegar chamadas para `ChunkingDuplexSessionChannels` aquele ouvinte de canal interno, é envolver novos canais aceitos do ouvinte do canal interno. Isso é `OnAcceptChannel` feito `OnEndAcceptChannel`em e . O recém-criado `ChunkingDuplexSessionChannel` é passado pelo canal interno junto com os outros parâmetros descritos anteriormente.

## <a name="implementing-binding-element-and-binding"></a>Implementando elemento de vinculação e vinculação

`ChunkingBindingElement`é responsável pela `ChunkingChannelFactory` `ChunkingChannelListener`criação do e . A `ChunkingBindingElement` verifica se `CanBuildChannelFactory` \<T `CanBuildChannelListener` \<em T> `IDuplexSessionChannel` e T> é do tipo (o único canal suportado pelo canal de emada) e se os outros elementos de ligação na vinculação suportam este tipo de canal.

`BuildChannelFactory`\<T> primeiro verifica se o tipo de canal solicitado pode ser construído e, em seguida, recebe uma lista de ações de mensagem a serem empedaços. Para saber mais, veja a seção a seguir. Em seguida, `ChunkingChannelFactory` cria uma nova passagem da fábrica `context.BuildInnerChannelFactory<IDuplexSessionChannel>`do canal interno (como retornado), a lista de ações de mensagem e o número máximo de pedaços para buffer. O número máximo de pedaços vem `MaxBufferedChunks` de uma `ChunkingBindingElement`propriedade chamada exposta pelo .

`BuildChannelListener<T>`tem uma implementação `ChunkingChannelListener` semelhante para criar e passar o ouvinte do canal interno.

Há um exemplo de vinculação `TcpChunkingBinding`incluído nesta amostra denominada . Esta ligação consiste em dois `TcpTransportBindingElement` `ChunkingBindingElement`elementos de ligação: e . Além de expor `MaxBufferedChunks` a propriedade, a vinculação `TcpTransportBindingElement` também `MaxReceivedMessageSize` define algumas `ChunkingUtils.ChunkSize` das propriedades, tais como (define-o para + 100KB bytes para cabeçalhos).

`TcpChunkingBinding`também implementa `IBindingRuntimePreferences` e retorna `ReceiveSynchronously` verdadeiro do método indicando que apenas as chamadas recebidas síncronas são implementadas.

### <a name="determining-which-messages-to-chunk"></a>Determinando quais mensagens para emrepassar

O canal de emparcelamento parte apenas `ChunkingBehavior` as mensagens identificadas através do atributo. A `ChunkingBehavior` classe `IOperationBehavior` implementa e é `AddBindingParameter` implementada chamando o método. Neste método, `ChunkingBehavior` examina-se o `AppliesTo` valor`InMessage`de `OutMessage` sua propriedade ( ou ambos) para determinar quais mensagens devem ser emrecadas. Em seguida, ele recebe a ação de cada uma `OperationDescription`dessas mensagens (da coleção Mensagens `ChunkingBindingParameter`em ) e adiciona-as a uma coleção de cordas contida em uma instância de . Em seguida, `ChunkingBindingParameter` adiciona isso `BindingParameterCollection`ao fornecido.

Isso `BindingParameterCollection` é passado `BindingContext` dentro do elemento de ligação para cada elemento de ligação na ligação quando esse elemento de ligação constrói a fábrica do canal ou o ouvinte do canal. A `ChunkingBindingElement`implementação `BuildChannelFactory<T>` e `BuildChannelListener<T>` a `ChunkingBindingParameter` retirada `BindingContext’`disso `BindingParameterCollection`do s. A coleta de ações `ChunkingBindingParameter` contidas dentro `ChunkingChannelFactory` `ChunkingChannelListener`do é então passada `ChunkingDuplexSessionChannel`para o ou , que por sua vez passa para o .

## <a name="running-the-sample"></a>Executando o exemplo

#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Instale ASP.NET 4.0 usando o seguinte comando.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

3. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

5. Execute Service.exe primeiro, depois execute Client.exe e assista as duas janelas do console para saída.

Ao executar a amostra, espera-se a seguinte saída.

Cliente:

```console
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

```console
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
