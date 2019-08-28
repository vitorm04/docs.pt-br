---
title: Canal de agrupamento
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: b59f5c42f5a0f81f666bc5d22924f14c678a60e1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045709"
---
# <a name="chunking-channel"></a><span data-ttu-id="95229-102">Canal de agrupamento</span><span class="sxs-lookup"><span data-stu-id="95229-102">Chunking Channel</span></span>

<span data-ttu-id="95229-103">Ao enviar mensagens grandes usando Windows Communication Foundation (WCF), geralmente é desejável limitar a quantidade de memória usada para armazenar em buffer essas mensagens.</span><span class="sxs-lookup"><span data-stu-id="95229-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="95229-104">Uma solução possível é transmitir o corpo da mensagem (supondo que a massa dos dados esteja no corpo).</span><span class="sxs-lookup"><span data-stu-id="95229-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="95229-105">No entanto, alguns protocolos exigem o armazenamento em buffer de toda a mensagem.</span><span class="sxs-lookup"><span data-stu-id="95229-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="95229-106">As mensagens e a segurança confiáveis são dois exemplos.</span><span class="sxs-lookup"><span data-stu-id="95229-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="95229-107">Outra solução possível é dividir a mensagem grande em mensagens menores chamadas de partes, enviar as partes uma parte por vez e reconstituir a mensagem grande no lado de recebimento.</span><span class="sxs-lookup"><span data-stu-id="95229-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="95229-108">O próprio aplicativo poderia fazer esse agrupamento e desagrupamento ou usar um canal personalizado para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="95229-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="95229-109">O exemplo de canal de agrupamento mostra como um protocolo personalizado ou canal em camadas pode ser usado para fazer agrupamentos e desagrupamento de mensagens arbitrariamente grandes.</span><span class="sxs-lookup"><span data-stu-id="95229-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>

<span data-ttu-id="95229-110">O agrupamento deve ser sempre empregado somente depois que a mensagem inteira a ser enviada tiver sido construída.</span><span class="sxs-lookup"><span data-stu-id="95229-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="95229-111">Um canal de agrupamento deve estar sempre em camadas abaixo de um canal de segurança e um canal de sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="95229-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>

> [!NOTE]
> <span data-ttu-id="95229-112">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="95229-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="95229-113">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="95229-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="95229-114">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="95229-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="95229-115">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="95229-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="95229-116">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="95229-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="95229-117">Trechos de considerações e limitações de canal</span><span class="sxs-lookup"><span data-stu-id="95229-117">Chunking Channel Assumptions and Limitations</span></span>

### <a name="message-structure"></a><span data-ttu-id="95229-118">Estrutura da mensagem</span><span class="sxs-lookup"><span data-stu-id="95229-118">Message Structure</span></span>

<span data-ttu-id="95229-119">O canal de agrupamento assume a seguinte estrutura de mensagem para que as mensagens sejam fragmentadas:</span><span class="sxs-lookup"><span data-stu-id="95229-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>

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

<span data-ttu-id="95229-120">Ao usar o ServiceModel, as operações de contrato que têm um parâmetro de entrada são compatíveis com essa forma de mensagem para sua mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="95229-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="95229-121">Da mesma forma, as operações de contrato que têm 1 parâmetro de saída ou valor de retorno estão em conformidade com essa forma de mensagem para sua mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="95229-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="95229-122">Veja a seguir exemplos de tais operações:</span><span class="sxs-lookup"><span data-stu-id="95229-122">The following are examples of such operations:</span></span>

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

### <a name="sessions"></a><span data-ttu-id="95229-123">Sessões</span><span class="sxs-lookup"><span data-stu-id="95229-123">Sessions</span></span>

<span data-ttu-id="95229-124">O canal de agrupamento exige que as mensagens sejam entregues exatamente uma vez, na entrega ordenada de mensagens (partes).</span><span class="sxs-lookup"><span data-stu-id="95229-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="95229-125">Isso significa que a pilha de canais subjacente deve ser sessão.</span><span class="sxs-lookup"><span data-stu-id="95229-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="95229-126">As sessões podem ser fornecidas pelo transporte (por exemplo, transporte TCP) ou por um canal de protocolo de sessão (por exemplo, canal ReliableSession).</span><span class="sxs-lookup"><span data-stu-id="95229-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>

### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="95229-127">Envio e recebimento assíncronos</span><span class="sxs-lookup"><span data-stu-id="95229-127">Asynchronous Send and Receive</span></span>

<span data-ttu-id="95229-128">Os métodos de envio e recebimento assíncronos não são implementados nesta versão do exemplo de canal de agrupamento.</span><span class="sxs-lookup"><span data-stu-id="95229-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>

## <a name="chunking-protocol"></a><span data-ttu-id="95229-129">Protocolo de agrupamento</span><span class="sxs-lookup"><span data-stu-id="95229-129">Chunking Protocol</span></span>

<span data-ttu-id="95229-130">O canal de agrupamento define um protocolo que indica o início e o término de uma série de partes, bem como o número de sequência de cada parte.</span><span class="sxs-lookup"><span data-stu-id="95229-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="95229-131">As três mensagens de exemplo a seguir demonstram as mensagens de início, bloco e fim com comentários que descrevem os principais aspectos de cada um.</span><span class="sxs-lookup"><span data-stu-id="95229-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>

### <a name="start-message"></a><span data-ttu-id="95229-132">Mensagem de início</span><span class="sxs-lookup"><span data-stu-id="95229-132">Start Message</span></span>

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

### <a name="chunk-message"></a><span data-ttu-id="95229-133">Mensagem de bloco</span><span class="sxs-lookup"><span data-stu-id="95229-133">Chunk Message</span></span>

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

### <a name="end-message"></a><span data-ttu-id="95229-134">Mensagem final</span><span class="sxs-lookup"><span data-stu-id="95229-134">End Message</span></span>

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

## <a name="chunking-channel-architecture"></a><span data-ttu-id="95229-135">Arquitetura de canal de agrupamento</span><span class="sxs-lookup"><span data-stu-id="95229-135">Chunking Channel Architecture</span></span>

<span data-ttu-id="95229-136">O canal de agrupamento é um `IDuplexSessionChannel` que, em um alto nível, segue a arquitetura de canal típica.</span><span class="sxs-lookup"><span data-stu-id="95229-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="95229-137">Há um `ChunkingBindingElement` que pode criar um `ChunkingChannelFactory` e um `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="95229-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="95229-138">O `ChunkingChannelFactory` cria instâncias de `ChunkingChannel` quando é solicitado.</span><span class="sxs-lookup"><span data-stu-id="95229-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="95229-139">O `ChunkingChannelListener` cria instâncias do `ChunkingChannel` quando um novo canal interno é aceito.</span><span class="sxs-lookup"><span data-stu-id="95229-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="95229-140">O `ChunkingChannel` próprio é responsável por enviar e receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="95229-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>

<span data-ttu-id="95229-141">No próximo nível abaixo, `ChunkingChannel` o depende de vários componentes para implementar o protocolo de agrupamento.</span><span class="sxs-lookup"><span data-stu-id="95229-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="95229-142">No lado do envio, o canal usa um chamado <xref:System.Xml.XmlDictionaryWriter> `ChunkingWriter` personalizado que faz o agrupamento real.</span><span class="sxs-lookup"><span data-stu-id="95229-142">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="95229-143">`ChunkingWriter`usa o canal interno diretamente para enviar partes.</span><span class="sxs-lookup"><span data-stu-id="95229-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="95229-144">O uso de `XmlDictionaryWriter` um personalizado nos permite enviar partes, já que o corpo grande da mensagem original está sendo gravado.</span><span class="sxs-lookup"><span data-stu-id="95229-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="95229-145">Isso significa que não armazenamos em buffer toda a mensagem original.</span><span class="sxs-lookup"><span data-stu-id="95229-145">This means we do not buffer the entire original message.</span></span>

![Diagrama que mostra a arquitetura de envio do canal de agrupamento.](./media/chunking-channel/chunking-channel-send.gif)

<span data-ttu-id="95229-147">No lado do recebimento, `ChunkingChannel` o recebe as mensagens do canal interno e as passa para uma chamada <xref:System.Xml.XmlDictionaryReader> `ChunkingReader`personalizada, que reconstitui a mensagem original das partes de entrada.</span><span class="sxs-lookup"><span data-stu-id="95229-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="95229-148">`ChunkingChannel`encapsula isso `ChunkingReader` em uma implementação personalizada `Message` chamada `ChunkingMessage` e retorna essa mensagem para a camada acima.</span><span class="sxs-lookup"><span data-stu-id="95229-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="95229-149">Essa combinação de `ChunkingReader` e `ChunkingMessage` nos permite retirar a parte do corpo da mensagem original, pois ele está sendo lido pela camada acima, em vez de ter que armazenar em buffer todo o corpo da mensagem original.</span><span class="sxs-lookup"><span data-stu-id="95229-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="95229-150">`ChunkingReader`tem uma fila na qual ele armazena em buffer as partes de entrada até um número máximo configurável de partes em buffer.</span><span class="sxs-lookup"><span data-stu-id="95229-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="95229-151">Quando esse limite máximo é atingido, o leitor aguarda que as mensagens sejam descarregadas da fila pela camada acima (ou seja, apenas lendo do corpo da mensagem original) ou até que o tempo limite máximo de recebimento seja atingido.</span><span class="sxs-lookup"><span data-stu-id="95229-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>

![Diagrama que mostra a arquitetura de recebimento do canal de agrupamento.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a><span data-ttu-id="95229-153">Modelo de programação de agrupamento</span><span class="sxs-lookup"><span data-stu-id="95229-153">Chunking Programming Model</span></span>

<span data-ttu-id="95229-154">Os desenvolvedores de serviço podem especificar quais mensagens devem ser fragmentadas aplicando `ChunkingBehavior` o atributo às operações no contrato.</span><span class="sxs-lookup"><span data-stu-id="95229-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="95229-155">O atributo expõe uma `AppliesTo` propriedade que permite ao desenvolvedor especificar se o agrupamento se aplica à mensagem de entrada, à mensagem de saída ou a ambas.</span><span class="sxs-lookup"><span data-stu-id="95229-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="95229-156">O exemplo a seguir mostra o uso `ChunkingBehavior` do atributo:</span><span class="sxs-lookup"><span data-stu-id="95229-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>

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

<span data-ttu-id="95229-157">A partir desse modelo de programação `ChunkingBindingElement` , o compila uma lista de URIs de ação que identificam as mensagens a serem fragmentadas.</span><span class="sxs-lookup"><span data-stu-id="95229-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="95229-158">A ação de cada mensagem de saída é comparada com essa lista para determinar se a mensagem deve ser colocada em bloco ou enviada diretamente.</span><span class="sxs-lookup"><span data-stu-id="95229-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>

## <a name="implementing-the-send-operation"></a><span data-ttu-id="95229-159">Implementando a operação de envio</span><span class="sxs-lookup"><span data-stu-id="95229-159">Implementing the Send Operation</span></span>

<span data-ttu-id="95229-160">Em um nível alto, a operação enviar primeiro verifica se a mensagem de saída deve ser colocada em bloco e, caso contrário, envia a mensagem diretamente usando o canal interno.</span><span class="sxs-lookup"><span data-stu-id="95229-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>

<span data-ttu-id="95229-161">Se a mensagem precisar ser enfileirada, Send criará `ChunkingWriter` uma nova `WriteBodyContents` e chamará a mensagem de `ChunkingWriter`saída que a transmite.</span><span class="sxs-lookup"><span data-stu-id="95229-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="95229-162">`ChunkingWriter` Em seguida, o faz a fragmentação da mensagem (incluindo copiar os cabeçalhos da mensagem original para a mensagem de início da parte) e envia partes usando o canal interno.</span><span class="sxs-lookup"><span data-stu-id="95229-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>

<span data-ttu-id="95229-163">Alguns detalhes vale A pena observar:</span><span class="sxs-lookup"><span data-stu-id="95229-163">A few details worth noting:</span></span>

- <span data-ttu-id="95229-164">Envie as primeiras `ThrowIfDisposedOrNotOpened` chamadas para garantir `CommunicationState` que o esteja aberto.</span><span class="sxs-lookup"><span data-stu-id="95229-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>

- <span data-ttu-id="95229-165">O envio é sincronizado para que apenas uma mensagem possa ser enviada por vez para cada sessão.</span><span class="sxs-lookup"><span data-stu-id="95229-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="95229-166">Há um `ManualResetEvent` nome `sendingDone` que é redefinido quando uma mensagem em partes é enviada.</span><span class="sxs-lookup"><span data-stu-id="95229-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="95229-167">Depois que a mensagem final da parte é enviada, esse evento é definido.</span><span class="sxs-lookup"><span data-stu-id="95229-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="95229-168">O método Send aguarda esse evento ser definido antes de tentar enviar a mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="95229-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>

- <span data-ttu-id="95229-169">Enviar bloqueia o `CommunicationObject.ThisLock` para evitar alterações de estado sincronizado ao enviar.</span><span class="sxs-lookup"><span data-stu-id="95229-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="95229-170">Consulte a <xref:System.ServiceModel.Channels.CommunicationObject> documentação para obter mais informações <xref:System.ServiceModel.Channels.CommunicationObject> sobre Estados e computador de estado.</span><span class="sxs-lookup"><span data-stu-id="95229-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>

- <span data-ttu-id="95229-171">O tempo limite passado para Send é usado como o tempo limite para toda a operação de envio, que inclui o envio de todas as partes.</span><span class="sxs-lookup"><span data-stu-id="95229-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>

- <span data-ttu-id="95229-172">O design <xref:System.Xml.XmlDictionaryWriter> personalizado foi escolhido para evitar o buffer de todo o corpo da mensagem original.</span><span class="sxs-lookup"><span data-stu-id="95229-172">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="95229-173">Se tivéssemos que obter um <xref:System.Xml.XmlDictionaryReader> no corpo usando `message.GetReaderAtBodyContents` o corpo inteiro seria armazenado em buffer.</span><span class="sxs-lookup"><span data-stu-id="95229-173">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="95229-174">Em vez disso, temos um <xref:System.Xml.XmlDictionaryWriter> personalizado que é passado `message.WriteBodyContents`para.</span><span class="sxs-lookup"><span data-stu-id="95229-174">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="95229-175">À medida que a mensagem chama WriteBase64 no gravador, o gravador empacota partes em mensagens e as envia usando o canal interno.</span><span class="sxs-lookup"><span data-stu-id="95229-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="95229-176">WriteBase64 blocos de bloqueio até que a parte seja enviada.</span><span class="sxs-lookup"><span data-stu-id="95229-176">WriteBase64 blocks until the chunk is sent.</span></span>

## <a name="implementing-the-receive-operation"></a><span data-ttu-id="95229-177">Implementando a operação de recebimento</span><span class="sxs-lookup"><span data-stu-id="95229-177">Implementing the Receive Operation</span></span>

<span data-ttu-id="95229-178">Em um alto nível, a operação de recebimento verifica primeiro se a mensagem de entrada `null` não é e se sua ação `ChunkingAction`é.</span><span class="sxs-lookup"><span data-stu-id="95229-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="95229-179">Se ele não atender aos dois critérios, a mensagem será retornada inalterada de Receive.</span><span class="sxs-lookup"><span data-stu-id="95229-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="95229-180">Caso contrário, Receive criará `ChunkingReader` um novo e `ChunkingMessage` um novo encapsulado em torno `GetNewChunkingMessage`dele (chamando).</span><span class="sxs-lookup"><span data-stu-id="95229-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="95229-181">Antes de retornar essa `ChunkingMessage`nova, Receive usa um thread de ThreadPool `ReceiveChunkLoop`a ser executado `innerChannel.Receive` , que chama em um loop e transfere partes `ChunkingReader` para o até que a mensagem de bloco final seja recebida ou o tempo limite de recebimento seja atingido.</span><span class="sxs-lookup"><span data-stu-id="95229-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>

<span data-ttu-id="95229-182">Alguns detalhes vale A pena observar:</span><span class="sxs-lookup"><span data-stu-id="95229-182">A few details worth noting:</span></span>

- <span data-ttu-id="95229-183">Como enviar, receba as primeiras `ThrowIfDisposedOrNotOepned` chamadas para garantir `CommunicationState` que o esteja aberto.</span><span class="sxs-lookup"><span data-stu-id="95229-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>

- <span data-ttu-id="95229-184">Receive também é sincronizado para que apenas uma mensagem possa ser recebida por vez da sessão.</span><span class="sxs-lookup"><span data-stu-id="95229-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="95229-185">Isso é especialmente importante porque depois que uma mensagem de início de bloco é recebida, todas as mensagens subsequentes recebidas devem ser partes nessa nova sequência de bloco até que uma mensagem de bloco final seja recebida.</span><span class="sxs-lookup"><span data-stu-id="95229-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="95229-186">O recebimento não pode efetuar pull de mensagens do canal interno até que todas as partes que pertencem à mensagem que está sendo desfragmentada no momento sejam recebidas.</span><span class="sxs-lookup"><span data-stu-id="95229-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="95229-187">Para fazer isso, Receive usa um `ManualResetEvent` nome `currentMessageCompleted`, que é definido quando a mensagem de parte final é recebida e redefinida quando uma nova mensagem de início de bloco é recebida.</span><span class="sxs-lookup"><span data-stu-id="95229-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>

- <span data-ttu-id="95229-188">Ao contrário de enviar, Receive não impede transições de estado sincronizadas durante o recebimento.</span><span class="sxs-lookup"><span data-stu-id="95229-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="95229-189">Por exemplo, Close pode ser chamado durante o recebimento e aguarda até que o recebimento pendente da mensagem original seja concluído ou o valor de tempo limite especificado seja atingido.</span><span class="sxs-lookup"><span data-stu-id="95229-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>

- <span data-ttu-id="95229-190">O tempo limite passado para Receive é usado como o tempo limite para a operação de recebimento inteira, que inclui o recebimento de todas as partes.</span><span class="sxs-lookup"><span data-stu-id="95229-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>

- <span data-ttu-id="95229-191">Se a camada que consome a mensagem estiver consumindo o corpo da mensagem em uma taxa menor do que a taxa de mensagens de `ChunkingReader` bloco de entrada, o armazenará em buffer essas partes de `ChunkingBindingElement.MaxBufferedChunks`entrada até o limite especificado por.</span><span class="sxs-lookup"><span data-stu-id="95229-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="95229-192">Depois que esse limite for atingido, nenhuma parte mais será extraída da camada inferior até que uma parte armazenada em buffer seja consumida ou o tempo limite de recebimento seja atingido.</span><span class="sxs-lookup"><span data-stu-id="95229-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>

## <a name="communicationobject-overrides"></a><span data-ttu-id="95229-193">Substituições de CommunicationObject</span><span class="sxs-lookup"><span data-stu-id="95229-193">CommunicationObject Overrides</span></span>

### <a name="onopen"></a><span data-ttu-id="95229-194">OnOpen</span><span class="sxs-lookup"><span data-stu-id="95229-194">OnOpen</span></span>

<span data-ttu-id="95229-195">`OnOpen`chamadas `innerChannel.Open` para abrir o canal interno.</span><span class="sxs-lookup"><span data-stu-id="95229-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>

### <a name="onclose"></a><span data-ttu-id="95229-196">Fechamento</span><span class="sxs-lookup"><span data-stu-id="95229-196">OnClose</span></span>

<span data-ttu-id="95229-197">`OnClose`o primeiro `stopReceive` define `true` como para sinalizar `ReceiveChunkLoop` o pendente para parar.</span><span class="sxs-lookup"><span data-stu-id="95229-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="95229-198">Em seguida, ele aguarda o `receiveStopped` <xref:System.Threading.ManualResetEvent>, que é definido quando `ReceiveChunkLoop` é interrompido.</span><span class="sxs-lookup"><span data-stu-id="95229-198">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="95229-199">Supondo `ReceiveChunkLoop` que as interrupções dentro do `OnClose` tempo `innerChannel.Close` limite especificado sejam chamadas com o tempo limite restante.</span><span class="sxs-lookup"><span data-stu-id="95229-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>

### <a name="onabort"></a><span data-ttu-id="95229-200">OnAbort</span><span class="sxs-lookup"><span data-stu-id="95229-200">OnAbort</span></span>

<span data-ttu-id="95229-201">`OnAbort`chamadas `innerChannel.Abort` para anular o canal interno.</span><span class="sxs-lookup"><span data-stu-id="95229-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="95229-202">Se houver um `ReceiveChunkLoop` , ele receberá uma exceção da chamada pendente `innerChannel.Receive` .</span><span class="sxs-lookup"><span data-stu-id="95229-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>

### <a name="onfaulted"></a><span data-ttu-id="95229-203">Com falha</span><span class="sxs-lookup"><span data-stu-id="95229-203">OnFaulted</span></span>

<span data-ttu-id="95229-204">O `ChunkingChannel` não requer comportamento especial quando o canal tem falha, portanto `OnFaulted` não é substituído.</span><span class="sxs-lookup"><span data-stu-id="95229-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>

## <a name="implementing-channel-factory"></a><span data-ttu-id="95229-205">Implementando a fábrica de canais</span><span class="sxs-lookup"><span data-stu-id="95229-205">Implementing Channel Factory</span></span>

<span data-ttu-id="95229-206">O `ChunkingChannelFactory` é responsável por criar instâncias do `ChunkingDuplexSessionChannel` e para transições de estado em cascata para a fábrica de canais interna.</span><span class="sxs-lookup"><span data-stu-id="95229-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>

<span data-ttu-id="95229-207">`OnCreateChannel`usa a fábrica de canais interna para criar `IDuplexSessionChannel` um canal interno.</span><span class="sxs-lookup"><span data-stu-id="95229-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="95229-208">Em seguida, ele cria `ChunkingDuplexSessionChannel` um novo passando esse canal interno junto com a lista de ações de mensagens a serem enfileiradas e o número máximo de partes para armazenar em buffer após o recebimento.</span><span class="sxs-lookup"><span data-stu-id="95229-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="95229-209">A lista de ações de mensagens a serem enfileiradas e o número máximo de partes para o buffer são dois parâmetros `ChunkingChannelFactory` passados para em seu construtor.</span><span class="sxs-lookup"><span data-stu-id="95229-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="95229-210">A seção sobre `ChunkingBindingElement` descreve de onde vêm esses valores.</span><span class="sxs-lookup"><span data-stu-id="95229-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>

<span data-ttu-id="95229-211">O `OnOpen`, `OnClose` ,`OnAbort` e seus equivalentes assíncronos chamam o método de transição de estado correspondente na fábrica de canais interna.</span><span class="sxs-lookup"><span data-stu-id="95229-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>

## <a name="implementing-channel-listener"></a><span data-ttu-id="95229-212">Implementando ouvinte de canal</span><span class="sxs-lookup"><span data-stu-id="95229-212">Implementing Channel Listener</span></span>

<span data-ttu-id="95229-213">O `ChunkingChannelListener` é um wrapper em um ouvinte de canal interno.</span><span class="sxs-lookup"><span data-stu-id="95229-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="95229-214">Sua função principal, além de chamadas delegadas para esse ouvinte de canal interno, `ChunkingDuplexSessionChannels` é encapsular o novo em volta dos canais aceitos do ouvinte de canal interno.</span><span class="sxs-lookup"><span data-stu-id="95229-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="95229-215">Isso é feito no `OnAcceptChannel` e `OnEndAcceptChannel`no.</span><span class="sxs-lookup"><span data-stu-id="95229-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="95229-216">O recém-criado `ChunkingDuplexSessionChannel` é passado para o canal interno junto com os outros parâmetros descritos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="95229-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>

## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="95229-217">Implementando elemento de associação e Associação</span><span class="sxs-lookup"><span data-stu-id="95229-217">Implementing Binding Element and Binding</span></span>

<span data-ttu-id="95229-218">`ChunkingBindingElement`é responsável por criar o `ChunkingChannelFactory` e `ChunkingChannelListener`o.</span><span class="sxs-lookup"><span data-stu-id="95229-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="95229-219">O `ChunkingBindingElement` verifica se t em `CanBuildChannelFactory` \<t > e `CanBuildChannelListener` \<t > é do tipo `IDuplexSessionChannel` (o único canal com suporte no canal de agrupamento) e se os outros elementos de ligação na associação dão suporte a isso tipo de canal.</span><span class="sxs-lookup"><span data-stu-id="95229-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>

<span data-ttu-id="95229-220">`BuildChannelFactory`\<T > primeiro verifica se o tipo de canal solicitado pode ser compilado e, em seguida, obtém uma lista de ações de mensagens a serem fragmentadas.</span><span class="sxs-lookup"><span data-stu-id="95229-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="95229-221">Para obter mais informações, consulte a seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="95229-221">For more information, see the following section.</span></span> <span data-ttu-id="95229-222">Em seguida, ele cria `ChunkingChannelFactory` um novo passando-o para o alocador de `context.BuildInnerChannelFactory<IDuplexSessionChannel>`canal interno (como retornado de), a lista de ações de mensagem e o número máximo de partes para armazenar em buffer.</span><span class="sxs-lookup"><span data-stu-id="95229-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="95229-223">O número máximo de partes vem de uma propriedade chamada `MaxBufferedChunks` exposta `ChunkingBindingElement`pelo.</span><span class="sxs-lookup"><span data-stu-id="95229-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>

<span data-ttu-id="95229-224">`BuildChannelListener<T>`o tem uma implementação semelhante para `ChunkingChannelListener` criar e passar o ouvinte de canal interno.</span><span class="sxs-lookup"><span data-stu-id="95229-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>

<span data-ttu-id="95229-225">Há uma associação de exemplo incluída neste exemplo denominada `TcpChunkingBinding`.</span><span class="sxs-lookup"><span data-stu-id="95229-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="95229-226">Essa associação consiste em dois elementos de ligação `TcpTransportBindingElement` : `ChunkingBindingElement`e.</span><span class="sxs-lookup"><span data-stu-id="95229-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="95229-227">Além de expor `MaxBufferedChunks` a propriedade, a associação também define algumas `TcpTransportBindingElement` das propriedades como `MaxReceivedMessageSize` (define para `ChunkingUtils.ChunkSize` + 100 KB bytes para cabeçalhos).</span><span class="sxs-lookup"><span data-stu-id="95229-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>

<span data-ttu-id="95229-228">`TcpChunkingBinding`também implementa `IBindingRuntimePreferences` e retorna true `ReceiveSynchronously` do método que indica que apenas as chamadas de recebimento síncronas são implementadas.</span><span class="sxs-lookup"><span data-stu-id="95229-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>

### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="95229-229">Determinando quais mensagens partes</span><span class="sxs-lookup"><span data-stu-id="95229-229">Determining Which Messages To Chunk</span></span>

<span data-ttu-id="95229-230">O canal de agrupamento fragmenta apenas as mensagens identificadas por meio `ChunkingBehavior` do atributo.</span><span class="sxs-lookup"><span data-stu-id="95229-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="95229-231">A `ChunkingBehavior` classe implementa `IOperationBehavior` e é implementada chamando o `AddBindingParameter` método.</span><span class="sxs-lookup"><span data-stu-id="95229-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="95229-232">Nesse `ChunkingBehavior` método, o examina o valor de sua `AppliesTo` Propriedade (`InMessage` `OutMessage` ou ambos) para determinar quais mensagens devem ser fragmentadas.</span><span class="sxs-lookup"><span data-stu-id="95229-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="95229-233">Em seguida, ele obtém a ação de cada uma dessas mensagens (da coleção messages em `OperationDescription`) e a adiciona a uma coleção de cadeia de caracteres contida em uma instância do. `ChunkingBindingParameter`</span><span class="sxs-lookup"><span data-stu-id="95229-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="95229-234">Em seguida, ele `ChunkingBindingParameter` adiciona isso ao `BindingParameterCollection`fornecido.</span><span class="sxs-lookup"><span data-stu-id="95229-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>

<span data-ttu-id="95229-235">Isso `BindingParameterCollection` é passado dentro de `BindingContext` cada elemento de ligação na associação quando esse elemento de ligação cria a fábrica de canais ou o ouvinte de canal.</span><span class="sxs-lookup"><span data-stu-id="95229-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="95229-236">A `ChunkingBindingElement` implementaçãodo`BuildChannelListener<T>` eretire`ChunkingBindingParameter` isso dos s`BindingContext’`. `BindingParameterCollection` `BuildChannelFactory<T>`</span><span class="sxs-lookup"><span data-stu-id="95229-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="95229-237">A `ChunkingBindingParameter` coleção de ações contidas no é passada para o `ChunkingChannelFactory` ou `ChunkingChannelListener`, que, por sua vez, passa para `ChunkingDuplexSessionChannel`o.</span><span class="sxs-lookup"><span data-stu-id="95229-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>

## <a name="running-the-sample"></a><span data-ttu-id="95229-238">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="95229-238">Running the Sample</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="95229-239">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="95229-239">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="95229-240">Instale o ASP.NET 4,0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="95229-240">Install ASP.NET 4.0 using the following command.</span></span>

    ```
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="95229-241">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95229-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="95229-242">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95229-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="95229-243">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95229-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

5. <span data-ttu-id="95229-244">Execute o Service. exe primeiro e execute Client. exe e observe as janelas do console para saída.</span><span class="sxs-lookup"><span data-stu-id="95229-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>

<span data-ttu-id="95229-245">Ao executar o exemplo, a saída a seguir é esperada.</span><span class="sxs-lookup"><span data-stu-id="95229-245">When running the sample, the following output is expected.</span></span>

<span data-ttu-id="95229-246">Cliente:</span><span class="sxs-lookup"><span data-stu-id="95229-246">Client:</span></span>

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

<span data-ttu-id="95229-247">Servidor</span><span class="sxs-lookup"><span data-stu-id="95229-247">Server:</span></span>

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
