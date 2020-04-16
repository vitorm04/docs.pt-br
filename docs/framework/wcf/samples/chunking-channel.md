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
# <a name="chunking-channel"></a><span data-ttu-id="4fc8d-102">Canal de agrupamento</span><span class="sxs-lookup"><span data-stu-id="4fc8d-102">Chunking Channel</span></span>

<span data-ttu-id="4fc8d-103">Ao enviar grandes mensagens usando o Windows Communication Foundation (WCF), muitas vezes é desejável limitar a quantidade de memória usada para tamponar essas mensagens.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="4fc8d-104">Uma solução possível é transmitir o corpo da mensagem (assumindo que a maior parte dos dados está no corpo).</span><span class="sxs-lookup"><span data-stu-id="4fc8d-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="4fc8d-105">No entanto, alguns protocolos requerem o buffer de toda a mensagem.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="4fc8d-106">Mensagens confiáveis e segurança são dois exemplos.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="4fc8d-107">Outra solução possível é dividir a mensagem grande em mensagens menores chamadas pedaços, enviar esses pedaços um pedaço de cada vez e reconstituir a grande mensagem no lado receptor.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="4fc8d-108">O aplicativo em si poderia fazer esse emaque e desparcelamento ou poderia usar um canal personalizado para fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="4fc8d-109">A amostra do canal de emparcelamento mostra como um protocolo personalizado ou um canal em camadas podem ser usados para fazer o embigo e desparcelar mensagens arbitrariamente grandes.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>

<span data-ttu-id="4fc8d-110">O envoluso deve ser sempre empregado somente após a construção de toda a mensagem a ser enviada.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="4fc8d-111">Um canal de emparcelamento deve estar sempre em camadas abaixo de um canal de segurança e um canal de sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>

> [!NOTE]
> <span data-ttu-id="4fc8d-112">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4fc8d-113">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4fc8d-114">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="4fc8d-115">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="4fc8d-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4fc8d-116">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="4fc8d-117">Ressupostos e limitações do canal de fatiamento</span><span class="sxs-lookup"><span data-stu-id="4fc8d-117">Chunking Channel Assumptions and Limitations</span></span>

### <a name="message-structure"></a><span data-ttu-id="4fc8d-118">Estrutura de mensagens</span><span class="sxs-lookup"><span data-stu-id="4fc8d-118">Message Structure</span></span>

<span data-ttu-id="4fc8d-119">O canal de emparcelamento assume a seguinte estrutura de mensagem para que as mensagens sejam empedaços:</span><span class="sxs-lookup"><span data-stu-id="4fc8d-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>

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

<span data-ttu-id="4fc8d-120">Ao usar o ServiceModel, as operações de contrato que tenham 1 parâmetro de entrada estão em conformidade com esta forma de mensagem para sua mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="4fc8d-121">Da mesma forma, as operações de contrato que tenham 1 parâmetro de saída ou valor de retorno cumprem esta forma de mensagem para sua mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="4fc8d-122">A seguir, exemplos de tais operações:</span><span class="sxs-lookup"><span data-stu-id="4fc8d-122">The following are examples of such operations:</span></span>

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

### <a name="sessions"></a><span data-ttu-id="4fc8d-123">Sessões</span><span class="sxs-lookup"><span data-stu-id="4fc8d-123">Sessions</span></span>

<span data-ttu-id="4fc8d-124">O canal de emparcelamento exige que as mensagens sejam entregues exatamente uma vez, na entrega ordenada de mensagens (pedaços).</span><span class="sxs-lookup"><span data-stu-id="4fc8d-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="4fc8d-125">Isso significa que a pilha de canais subjacente deve ser sessão.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="4fc8d-126">As sessões podem ser fornecidas pelo transporte (por exemplo, transporte TCP) ou por um canal de protocolo de sessão (por exemplo, canal ReliableSession).</span><span class="sxs-lookup"><span data-stu-id="4fc8d-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>

### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="4fc8d-127">Enviado e Receba Assíncrono</span><span class="sxs-lookup"><span data-stu-id="4fc8d-127">Asynchronous Send and Receive</span></span>

<span data-ttu-id="4fc8d-128">Os métodos assíncronos de envio e recebimento não são implementados nesta versão da amostra do canal de emada.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>

## <a name="chunking-protocol"></a><span data-ttu-id="4fc8d-129">Protocolo de emada</span><span class="sxs-lookup"><span data-stu-id="4fc8d-129">Chunking Protocol</span></span>

<span data-ttu-id="4fc8d-130">O canal de emcomamento define um protocolo que indica o início e o fim de uma série de pedaços, bem como o número de seqüência de cada pedaço.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="4fc8d-131">As três mensagens de exemplo a seguir demonstram as mensagens de início, pedaço e fim com comentários que descrevem os principais aspectos de cada um.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>

### <a name="start-message"></a><span data-ttu-id="4fc8d-132">Iniciar mensagem</span><span class="sxs-lookup"><span data-stu-id="4fc8d-132">Start Message</span></span>

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

### <a name="chunk-message"></a><span data-ttu-id="4fc8d-133">Mensagem de Pedaço</span><span class="sxs-lookup"><span data-stu-id="4fc8d-133">Chunk Message</span></span>

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

### <a name="end-message"></a><span data-ttu-id="4fc8d-134">Mensagem final</span><span class="sxs-lookup"><span data-stu-id="4fc8d-134">End Message</span></span>

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

## <a name="chunking-channel-architecture"></a><span data-ttu-id="4fc8d-135">Arquitetura do canal de chunking</span><span class="sxs-lookup"><span data-stu-id="4fc8d-135">Chunking Channel Architecture</span></span>

<span data-ttu-id="4fc8d-136">O canal de `IDuplexSessionChannel` emada é um que, em alto nível, segue a arquitetura típica do canal.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="4fc8d-137">Há um `ChunkingBindingElement` que pode `ChunkingChannelFactory` construir `ChunkingChannelListener`um e um .</span><span class="sxs-lookup"><span data-stu-id="4fc8d-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="4fc8d-138">As `ChunkingChannelFactory` instâncias `ChunkingChannel` de cria de quando é solicitado.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="4fc8d-139">As `ChunkingChannelListener` instâncias `ChunkingChannel` de criação de quando um novo canal interno é aceito.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="4fc8d-140">O `ChunkingChannel` próprio é responsável pelo envio e recebimento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>

<span data-ttu-id="4fc8d-141">No próximo nível `ChunkingChannel` para baixo, conta com vários componentes para implementar o protocolo de emada.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="4fc8d-142">No lado de envio, o <xref:System.Xml.XmlDictionaryWriter> `ChunkingWriter` canal usa um personalizado chamado que faz o pedaço real.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-142">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="4fc8d-143">`ChunkingWriter`usa o canal interno diretamente para enviar pedaços.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="4fc8d-144">Usar um `XmlDictionaryWriter` costume nos permite enviar pedaços enquanto o grande corpo da mensagem original está sendo escrito.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="4fc8d-145">Isso significa que não tamponamos toda a mensagem original.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-145">This means we do not buffer the entire original message.</span></span>

![Diagrama que mostra a arquitetura de envio de canal de blocos.](./media/chunking-channel/chunking-channel-send.gif)

<span data-ttu-id="4fc8d-147">No lado de `ChunkingChannel` recebimento, puxa mensagens do canal interno <xref:System.Xml.XmlDictionaryReader> `ChunkingReader`e as entrega a um costume chamado , que reconstitui a mensagem original dos pedaços recebidos.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="4fc8d-148">`ChunkingChannel`envolve isso `ChunkingReader` em `Message` uma `ChunkingMessage` implementação personalizada chamada e retorna esta mensagem para a camada acima.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="4fc8d-149">Essa combinação `ChunkingReader` `ChunkingMessage` e nos permite desmembarar o corpo da mensagem original enquanto ele está sendo lido pela camada acima em vez de ter que tamponar todo o corpo de mensagem original.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="4fc8d-150">`ChunkingReader`tem uma fila onde ele tampona os pedaços de entrada até um número máximo configurável de pedaços tamponados.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="4fc8d-151">Quando esse limite máximo é atingido, o leitor espera que as mensagens sejam drenadas da fila pela camada acima (ou seja, apenas lendo do corpo da mensagem original) ou até que o tempo máximo de recebimento seja atingido.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>

![Diagrama que mostra o canal de chunking receber arquitetura.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a><span data-ttu-id="4fc8d-153">Modelo de programação de fatias</span><span class="sxs-lookup"><span data-stu-id="4fc8d-153">Chunking Programming Model</span></span>

<span data-ttu-id="4fc8d-154">Os desenvolvedores de serviços podem especificar quais `ChunkingBehavior` mensagens devem ser emretoadas aplicando o atributo às operações dentro do contrato.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="4fc8d-155">O atributo `AppliesTo` expõe uma propriedade que permite ao desenvolvedor especificar se o pedaço se aplica à mensagem de entrada, à mensagem de saída ou ambos.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="4fc8d-156">O exemplo a seguir `ChunkingBehavior` mostra o uso do atributo:</span><span class="sxs-lookup"><span data-stu-id="4fc8d-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>

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

<span data-ttu-id="4fc8d-157">A partir deste modelo `ChunkingBindingElement` de programação, o compila uma lista de URIs de ação que identificam mensagens a serem emretaladas.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="4fc8d-158">A ação de cada mensagem de saída é comparada com esta lista para determinar se a mensagem deve ser empedaços ou enviada diretamente.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>

## <a name="implementing-the-send-operation"></a><span data-ttu-id="4fc8d-159">Implementando a Operação Enviar</span><span class="sxs-lookup"><span data-stu-id="4fc8d-159">Implementing the Send Operation</span></span>

<span data-ttu-id="4fc8d-160">Em um nível alto, a operação Enviar primeiro verifica se a mensagem de saída deve ser empedaços e, se não, envia a mensagem diretamente usando o canal interno.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>

<span data-ttu-id="4fc8d-161">Se a mensagem deve ser empedaços, Enviar cria uma nova `ChunkingWriter` e chama `WriteBodyContents` a mensagem de saída passando-a isso `ChunkingWriter`.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="4fc8d-162">Em `ChunkingWriter` seguida, faz o pedaço de mensagem (incluindo copiar cabeçalhos de mensagem originais para a mensagem de inicialização) e envia pedaços usando o canal interno.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>

<span data-ttu-id="4fc8d-163">Alguns detalhes que merecem ser notados:</span><span class="sxs-lookup"><span data-stu-id="4fc8d-163">A few details worth noting:</span></span>

- <span data-ttu-id="4fc8d-164">Envie as `ThrowIfDisposedOrNotOpened` primeiras `CommunicationState` chamadas para garantir que a abertura seja aberta.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>

- <span data-ttu-id="4fc8d-165">O envio é sincronizado para que apenas uma mensagem possa ser enviada de cada vez para cada sessão.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="4fc8d-166">Há um `ManualResetEvent` `sendingDone` nome que é redefinido quando uma mensagem em pedaços está sendo enviada.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="4fc8d-167">Uma vez que a mensagem de bloco final é enviada, este evento é definido.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="4fc8d-168">O método Enviar espera que este evento seja definido antes de tentar enviar a mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>

- <span data-ttu-id="4fc8d-169">Envie bloqueios `CommunicationObject.ThisLock` para evitar alterações de estado sincronizadas durante o envio.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="4fc8d-170">Consulte <xref:System.ServiceModel.Channels.CommunicationObject> a documentação <xref:System.ServiceModel.Channels.CommunicationObject> para obter mais informações sobre estados e máquinas estaduais.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>

- <span data-ttu-id="4fc8d-171">O tempo de tempo passado para Enviar é usado como o tempo máximo para toda a operação de envio, que inclui o envio de todos os blocos.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>

- <span data-ttu-id="4fc8d-172">O <xref:System.Xml.XmlDictionaryWriter> design personalizado foi escolhido para evitar o buffer de todo o corpo de mensagem original.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-172">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="4fc8d-173">Se tivéssemos <xref:System.Xml.XmlDictionaryReader> um no `message.GetReaderAtBodyContents` corpo usando todo o corpo seria tampão.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-173">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="4fc8d-174">Em vez disso, <xref:System.Xml.XmlDictionaryWriter> temos um `message.WriteBodyContents`costume que é passado para .</span><span class="sxs-lookup"><span data-stu-id="4fc8d-174">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="4fc8d-175">Como a mensagem chama WriteBase64 no escritor, o escritor empacota pedaços em mensagens e as envia usando o canal interno.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="4fc8d-176">WriteBase64 blocos até que o pedaço seja enviado.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-176">WriteBase64 blocks until the chunk is sent.</span></span>

## <a name="implementing-the-receive-operation"></a><span data-ttu-id="4fc8d-177">Implementando a Operação Receber</span><span class="sxs-lookup"><span data-stu-id="4fc8d-177">Implementing the Receive Operation</span></span>

<span data-ttu-id="4fc8d-178">Em alto nível, a operação Receber primeiro verifica `null` se a mensagem `ChunkingAction`recebida não é e que sua ação é a .</span><span class="sxs-lookup"><span data-stu-id="4fc8d-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="4fc8d-179">Se não atender a ambos os critérios, a mensagem é devolvida inalterada de Receber.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="4fc8d-180">Caso contrário, Receive `ChunkingReader` cria um `ChunkingMessage` novo e um `GetNewChunkingMessage`novo emvolta dele (chamando ).</span><span class="sxs-lookup"><span data-stu-id="4fc8d-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="4fc8d-181">Antes de retornar `ChunkingMessage`esse novo , O `ReceiveChunkLoop`Receive usa `innerChannel.Receive` um threadpool para executar `ChunkingReader` , que chama em um loop e entrega pedaços para o até que a mensagem de bloco final seja recebida ou o tempo de recebimento seja atingido.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>

<span data-ttu-id="4fc8d-182">Alguns detalhes que merecem ser notados:</span><span class="sxs-lookup"><span data-stu-id="4fc8d-182">A few details worth noting:</span></span>

- <span data-ttu-id="4fc8d-183">Como Enviar, receber `ThrowIfDisposedOrNotOepned` as `CommunicationState` primeiras chamadas para garantir que a abertura seja aberta.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>

- <span data-ttu-id="4fc8d-184">O recebimento também é sincronizado para que apenas uma mensagem possa ser recebida por vez da sessão.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="4fc8d-185">Isso é especialmente importante porque, uma vez que uma mensagem de bloco inicial é recebida, espera-se que todas as mensagens recebidas subseqüentes sejam em pedaços dentro desta nova seqüência de blocos até que uma mensagem de bloco final seja recebida.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="4fc8d-186">O receive não pode retirar mensagens do canal interno até que todos os pedaços que pertencem à mensagem que estão sendo desparceladas sejam recebidos.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="4fc8d-187">Para isso, o `ManualResetEvent` Receive `currentMessageCompleted`usa um nome , que é definido quando a mensagem de bloco final é recebida e redefinida quando uma nova mensagem de bloco de inicialé é recebida.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>

- <span data-ttu-id="4fc8d-188">Ao contrário do Send, o Receive não impede transições de estado sincronizadas durante o recebimento.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="4fc8d-189">Por exemplo, Fechar pode ser chamado enquanto recebe e espera até que o recebimento pendente da mensagem original seja concluído ou o valor de tempo definido especificado seja atingido.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>

- <span data-ttu-id="4fc8d-190">O tempo de tempo passado para Receber é usado como o tempo máximo para toda a operação de recebimento, o que inclui o recebimento de todos os blocos.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>

- <span data-ttu-id="4fc8d-191">Se a camada que consome a mensagem estiver consumindo o corpo de mensagem `ChunkingReader` a uma taxa menor do que a `ChunkingBindingElement.MaxBufferedChunks`taxa de mensagens de bloco recebidas, os buffers serão os blocos de entrada até o limite especificado por .</span><span class="sxs-lookup"><span data-stu-id="4fc8d-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="4fc8d-192">Uma vez que esse limite é atingido, não são mais retirados os pedaços da camada inferior até que um pedaço tamponado seja consumido ou o tempo limite de recebimento seja atingido.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>

## <a name="communicationobject-overrides"></a><span data-ttu-id="4fc8d-193">Substituições de objetos de comunicação</span><span class="sxs-lookup"><span data-stu-id="4fc8d-193">CommunicationObject Overrides</span></span>

### <a name="onopen"></a><span data-ttu-id="4fc8d-194">Onopen</span><span class="sxs-lookup"><span data-stu-id="4fc8d-194">OnOpen</span></span>

<span data-ttu-id="4fc8d-195">`OnOpen`chamadas `innerChannel.Open` para abrir o canal interno.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>

### <a name="onclose"></a><span data-ttu-id="4fc8d-196">Onclose</span><span class="sxs-lookup"><span data-stu-id="4fc8d-196">OnClose</span></span>

<span data-ttu-id="4fc8d-197">`OnClose`os `stopReceive` primeiros `true` conjuntos `ReceiveChunkLoop` para sinalizar a pendência de parar.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="4fc8d-198">Em seguida, espera `receiveStopped` <xref:System.Threading.ManualResetEvent>pelo , `ReceiveChunkLoop` que é definido quando pára.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-198">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="4fc8d-199">Assumindo `ReceiveChunkLoop` as paradas dentro do `OnClose` `innerChannel.Close` intervalo especificado, chamadas com o tempo restante.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>

### <a name="onabort"></a><span data-ttu-id="4fc8d-200">Onabort</span><span class="sxs-lookup"><span data-stu-id="4fc8d-200">OnAbort</span></span>

<span data-ttu-id="4fc8d-201">`OnAbort`chamadas `innerChannel.Abort` para abortar o canal interno.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="4fc8d-202">Se houver uma `ReceiveChunkLoop` pendência, ele `innerChannel.Receive` recebe uma exceção da chamada pendente.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>

### <a name="onfaulted"></a><span data-ttu-id="4fc8d-203">OnFaulted</span><span class="sxs-lookup"><span data-stu-id="4fc8d-203">OnFaulted</span></span>

<span data-ttu-id="4fc8d-204">O `ChunkingChannel` não requer comportamento especial quando o `OnFaulted` canal é defeituoso, portanto não é substituído.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>

## <a name="implementing-channel-factory"></a><span data-ttu-id="4fc8d-205">Fábrica de canais de implementação</span><span class="sxs-lookup"><span data-stu-id="4fc8d-205">Implementing Channel Factory</span></span>

<span data-ttu-id="4fc8d-206">O `ChunkingChannelFactory` é responsável por `ChunkingDuplexSessionChannel` criar instâncias de e para transições de estado em cascata para a fábrica de canais internos.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>

<span data-ttu-id="4fc8d-207">`OnCreateChannel`usa a fábrica de `IDuplexSessionChannel` canais internos para criar um canal interno.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="4fc8d-208">Em seguida, `ChunkingDuplexSessionChannel` ele cria um novo passe este canal interno, juntamente com a lista de ações de mensagem a serem emretaladas e o número máximo de pedaços a serem tamponados ao receber.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="4fc8d-209">A lista de ações de mensagem a serem redobradas e `ChunkingChannelFactory` o número máximo de pedaços para buffer são dois parâmetros passados em seu construtor.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="4fc8d-210">A seção em descreve `ChunkingBindingElement` de onde esses valores vêm.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>

<span data-ttu-id="4fc8d-211">Os `OnOpen` `OnClose`, `OnAbort` e seus equivalentes assíncronos chamam o método de transição de estado correspondente na fábrica do canal interno.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>

## <a name="implementing-channel-listener"></a><span data-ttu-id="4fc8d-212">Implementando ouvinte de canal</span><span class="sxs-lookup"><span data-stu-id="4fc8d-212">Implementing Channel Listener</span></span>

<span data-ttu-id="4fc8d-213">O `ChunkingChannelListener` é um invólucro em torno de um ouvinte de canal interno.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="4fc8d-214">Sua principal função, além de delegar chamadas para `ChunkingDuplexSessionChannels` aquele ouvinte de canal interno, é envolver novos canais aceitos do ouvinte do canal interno.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="4fc8d-215">Isso é `OnAcceptChannel` feito `OnEndAcceptChannel`em e .</span><span class="sxs-lookup"><span data-stu-id="4fc8d-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="4fc8d-216">O recém-criado `ChunkingDuplexSessionChannel` é passado pelo canal interno junto com os outros parâmetros descritos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>

## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="4fc8d-217">Implementando elemento de vinculação e vinculação</span><span class="sxs-lookup"><span data-stu-id="4fc8d-217">Implementing Binding Element and Binding</span></span>

<span data-ttu-id="4fc8d-218">`ChunkingBindingElement`é responsável pela `ChunkingChannelFactory` `ChunkingChannelListener`criação do e .</span><span class="sxs-lookup"><span data-stu-id="4fc8d-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="4fc8d-219">A `ChunkingBindingElement` verifica se `CanBuildChannelFactory` \<T `CanBuildChannelListener` \<em T> `IDuplexSessionChannel` e T> é do tipo (o único canal suportado pelo canal de emada) e se os outros elementos de ligação na vinculação suportam este tipo de canal.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>

<span data-ttu-id="4fc8d-220">`BuildChannelFactory`\<T> primeiro verifica se o tipo de canal solicitado pode ser construído e, em seguida, recebe uma lista de ações de mensagem a serem empedaços.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="4fc8d-221">Para saber mais, veja a seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-221">For more information, see the following section.</span></span> <span data-ttu-id="4fc8d-222">Em seguida, `ChunkingChannelFactory` cria uma nova passagem da fábrica `context.BuildInnerChannelFactory<IDuplexSessionChannel>`do canal interno (como retornado), a lista de ações de mensagem e o número máximo de pedaços para buffer.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="4fc8d-223">O número máximo de pedaços vem `MaxBufferedChunks` de uma `ChunkingBindingElement`propriedade chamada exposta pelo .</span><span class="sxs-lookup"><span data-stu-id="4fc8d-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>

<span data-ttu-id="4fc8d-224">`BuildChannelListener<T>`tem uma implementação `ChunkingChannelListener` semelhante para criar e passar o ouvinte do canal interno.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>

<span data-ttu-id="4fc8d-225">Há um exemplo de vinculação `TcpChunkingBinding`incluído nesta amostra denominada .</span><span class="sxs-lookup"><span data-stu-id="4fc8d-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="4fc8d-226">Esta ligação consiste em dois `TcpTransportBindingElement` `ChunkingBindingElement`elementos de ligação: e .</span><span class="sxs-lookup"><span data-stu-id="4fc8d-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="4fc8d-227">Além de expor `MaxBufferedChunks` a propriedade, a vinculação `TcpTransportBindingElement` também `MaxReceivedMessageSize` define algumas `ChunkingUtils.ChunkSize` das propriedades, tais como (define-o para + 100KB bytes para cabeçalhos).</span><span class="sxs-lookup"><span data-stu-id="4fc8d-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>

<span data-ttu-id="4fc8d-228">`TcpChunkingBinding`também implementa `IBindingRuntimePreferences` e retorna `ReceiveSynchronously` verdadeiro do método indicando que apenas as chamadas recebidas síncronas são implementadas.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>

### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="4fc8d-229">Determinando quais mensagens para emrepassar</span><span class="sxs-lookup"><span data-stu-id="4fc8d-229">Determining Which Messages To Chunk</span></span>

<span data-ttu-id="4fc8d-230">O canal de emparcelamento parte apenas `ChunkingBehavior` as mensagens identificadas através do atributo.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="4fc8d-231">A `ChunkingBehavior` classe `IOperationBehavior` implementa e é `AddBindingParameter` implementada chamando o método.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="4fc8d-232">Neste método, `ChunkingBehavior` examina-se o `AppliesTo` valor`InMessage`de `OutMessage` sua propriedade ( ou ambos) para determinar quais mensagens devem ser emrecadas.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="4fc8d-233">Em seguida, ele recebe a ação de cada uma `OperationDescription`dessas mensagens (da coleção Mensagens `ChunkingBindingParameter`em ) e adiciona-as a uma coleção de cordas contida em uma instância de .</span><span class="sxs-lookup"><span data-stu-id="4fc8d-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="4fc8d-234">Em seguida, `ChunkingBindingParameter` adiciona isso `BindingParameterCollection`ao fornecido.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>

<span data-ttu-id="4fc8d-235">Isso `BindingParameterCollection` é passado `BindingContext` dentro do elemento de ligação para cada elemento de ligação na ligação quando esse elemento de ligação constrói a fábrica do canal ou o ouvinte do canal.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="4fc8d-236">A `ChunkingBindingElement`implementação `BuildChannelFactory<T>` e `BuildChannelListener<T>` a `ChunkingBindingParameter` retirada `BindingContext’`disso `BindingParameterCollection`do s.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="4fc8d-237">A coleta de ações `ChunkingBindingParameter` contidas dentro `ChunkingChannelFactory` `ChunkingChannelListener`do é então passada `ChunkingDuplexSessionChannel`para o ou , que por sua vez passa para o .</span><span class="sxs-lookup"><span data-stu-id="4fc8d-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>

## <a name="running-the-sample"></a><span data-ttu-id="4fc8d-238">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="4fc8d-238">Running the Sample</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4fc8d-239">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4fc8d-239">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="4fc8d-240">Instale ASP.NET 4.0 usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-240">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="4fc8d-241">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8d-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="4fc8d-242">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8d-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="4fc8d-243">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8d-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

5. <span data-ttu-id="4fc8d-244">Execute Service.exe primeiro, depois execute Client.exe e assista as duas janelas do console para saída.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>

<span data-ttu-id="4fc8d-245">Ao executar a amostra, espera-se a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="4fc8d-245">When running the sample, the following output is expected.</span></span>

<span data-ttu-id="4fc8d-246">Cliente:</span><span class="sxs-lookup"><span data-stu-id="4fc8d-246">Client:</span></span>

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

<span data-ttu-id="4fc8d-247">Servidor: </span><span class="sxs-lookup"><span data-stu-id="4fc8d-247">Server:</span></span>

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
