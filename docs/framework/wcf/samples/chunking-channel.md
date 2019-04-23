---
title: Canal de agrupamento
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: a60cae7ad3dcfdaa139b8be974ed2d3996b5211d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302693"
---
# <a name="chunking-channel"></a><span data-ttu-id="4250c-102">Canal de agrupamento</span><span class="sxs-lookup"><span data-stu-id="4250c-102">Chunking Channel</span></span>
<span data-ttu-id="4250c-103">Ao enviar mensagens grandes usando o Windows Communication Foundation (WCF), geralmente é desejável para limitar a quantidade de memória usada para armazenar em buffer as mensagens.</span><span class="sxs-lookup"><span data-stu-id="4250c-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="4250c-104">Uma solução possível é transmitir o corpo da mensagem (supondo que a maior parte dos dados está no corpo).</span><span class="sxs-lookup"><span data-stu-id="4250c-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="4250c-105">No entanto, alguns protocolos exigem armazenamento em buffer da mensagem inteira.</span><span class="sxs-lookup"><span data-stu-id="4250c-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="4250c-106">Sistema de mensagens confiável e segurança são dois exemplos de tais.</span><span class="sxs-lookup"><span data-stu-id="4250c-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="4250c-107">Outra solução possível é dividir a mensagem grande em mensagens menores chamado partes, enviar partes de uma dessas partes por vez e reconstituir a mensagem grande no lado de recepção.</span><span class="sxs-lookup"><span data-stu-id="4250c-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="4250c-108">O aplicativo em si pode fazer esse agrupamento e desprovisionamento de agrupamento ou use um canal personalizado para fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="4250c-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="4250c-109">O exemplo de agrupamento de canal mostra como um protocolo personalizado ou o canal em camadas pode ser usado para fazer a eliminação da divisão de mensagens arbitrariamente grandes e o agrupamento.</span><span class="sxs-lookup"><span data-stu-id="4250c-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>  
  
 <span data-ttu-id="4250c-110">Agrupamento sempre deve ser empregada somente depois que a mensagem inteira seja enviado foi construída.</span><span class="sxs-lookup"><span data-stu-id="4250c-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="4250c-111">Um canal de agrupamento deve sempre ser colocado em camadas abaixo de um canal de segurança e um canal de sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="4250c-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4250c-112">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4250c-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4250c-113">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4250c-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4250c-114">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4250c-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4250c-115">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="4250c-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4250c-116">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4250c-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="4250c-117">Agrupamento de canal suposições e restrições</span><span class="sxs-lookup"><span data-stu-id="4250c-117">Chunking Channel Assumptions and Limitations</span></span>  
  
### <a name="message-structure"></a><span data-ttu-id="4250c-118">Estrutura de mensagens</span><span class="sxs-lookup"><span data-stu-id="4250c-118">Message Structure</span></span>  
 <span data-ttu-id="4250c-119">O canal de agrupamento pressupõe que a seguinte estrutura de mensagem a ser em bloco de mensagens:</span><span class="sxs-lookup"><span data-stu-id="4250c-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>  
  
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
  
 <span data-ttu-id="4250c-120">Ao usar o ServiceModel, operações de contrato que têm um parâmetro de entrada 1 está em conformidade com esta forma de mensagem à mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="4250c-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="4250c-121">Da mesma forma, operações de contrato que tem um parâmetro de saída 1 ou valor de retorno estão em conformidade com esta forma de mensagem à mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="4250c-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="4250c-122">A seguir estão exemplos de tais operações:</span><span class="sxs-lookup"><span data-stu-id="4250c-122">The following are examples of such operations:</span></span>  
  
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
  
### <a name="sessions"></a><span data-ttu-id="4250c-123">Sessões</span><span class="sxs-lookup"><span data-stu-id="4250c-123">Sessions</span></span>  
 <span data-ttu-id="4250c-124">O canal de agrupamento requer que mensagens sejam entregues exatamente uma vez, na entrega ordenada das mensagens (partes).</span><span class="sxs-lookup"><span data-stu-id="4250c-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="4250c-125">Isso significa que a pilha de canais subjacente deve ser de sessão.</span><span class="sxs-lookup"><span data-stu-id="4250c-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="4250c-126">As sessões podem ser fornecidas pelo transporte (por exemplo, o transporte TCP) ou por um canal de protocolo de sessão (por exemplo, ReliableSession canal).</span><span class="sxs-lookup"><span data-stu-id="4250c-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>  
  
### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="4250c-127">Assíncrona enviar e receber</span><span class="sxs-lookup"><span data-stu-id="4250c-127">Asynchronous Send and Receive</span></span>  
 <span data-ttu-id="4250c-128">Assíncrona enviar e receber métodos não são implementados nesta versão do exemplo de agrupamento de canal.</span><span class="sxs-lookup"><span data-stu-id="4250c-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>  
  
## <a name="chunking-protocol"></a><span data-ttu-id="4250c-129">Agrupamento de protocolo</span><span class="sxs-lookup"><span data-stu-id="4250c-129">Chunking Protocol</span></span>  
 <span data-ttu-id="4250c-130">O canal de agrupamento define um protocolo que indica o início e término de uma série de blocos, bem como o número de sequência de cada parte.</span><span class="sxs-lookup"><span data-stu-id="4250c-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="4250c-131">As mensagens de exemplo de três a seguir demonstram o início, mensagens de bloco e de término com comentários que descrevem os principais aspectos de cada um.</span><span class="sxs-lookup"><span data-stu-id="4250c-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>  
  
### <a name="start-message"></a><span data-ttu-id="4250c-132">Mensagem de início</span><span class="sxs-lookup"><span data-stu-id="4250c-132">Start Message</span></span>  
  
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
  
### <a name="chunk-message"></a><span data-ttu-id="4250c-133">O fragmento de mensagem</span><span class="sxs-lookup"><span data-stu-id="4250c-133">Chunk Message</span></span>  
  
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
  
### <a name="end-message"></a><span data-ttu-id="4250c-134">Mensagem de término</span><span class="sxs-lookup"><span data-stu-id="4250c-134">End Message</span></span>  
  
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
  
## <a name="chunking-channel-architecture"></a><span data-ttu-id="4250c-135">Arquitetura do canal de agrupamento</span><span class="sxs-lookup"><span data-stu-id="4250c-135">Chunking Channel Architecture</span></span>  
 <span data-ttu-id="4250c-136">O canal de agrupamento é um `IDuplexSessionChannel` que, em um alto nível, segue a arquitetura típica de canal.</span><span class="sxs-lookup"><span data-stu-id="4250c-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="4250c-137">Há um `ChunkingBindingElement` que pode criar um `ChunkingChannelFactory` e um `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="4250c-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="4250c-138">O `ChunkingChannelFactory` cria instâncias de `ChunkingChannel` quando for solicitado a.</span><span class="sxs-lookup"><span data-stu-id="4250c-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="4250c-139">O `ChunkingChannelListener` cria instâncias de `ChunkingChannel` quando um novo canal interno é aceito.</span><span class="sxs-lookup"><span data-stu-id="4250c-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="4250c-140">O `ChunkingChannel` por si só é responsável por enviar e receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="4250c-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>  
  
 <span data-ttu-id="4250c-141">No próximo nível inferior, `ChunkingChannel` depende de vários componentes para implementar o protocolo de agrupamento.</span><span class="sxs-lookup"><span data-stu-id="4250c-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="4250c-142">No lado do envio, o canal usa um personalizado <xref:System.Xml.XmlDictionaryWriter> chamado `ChunkingWriter` que faz o agrupamento real.</span><span class="sxs-lookup"><span data-stu-id="4250c-142">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="4250c-143">`ChunkingWriter` usa o canal interno diretamente para enviar partes.</span><span class="sxs-lookup"><span data-stu-id="4250c-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="4250c-144">Usando um personalizado `XmlDictionaryWriter` nos permite enviar partes como o corpo da mensagem original grande está sendo gravado.</span><span class="sxs-lookup"><span data-stu-id="4250c-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="4250c-145">Isso significa que podemos não armazenar em buffer toda a mensagem original.</span><span class="sxs-lookup"><span data-stu-id="4250c-145">This means we do not buffer the entire original message.</span></span>  
  
 ![Arquitetura de envio de diagrama que mostra o canal de agrupamento.](./media/chunking-channel/chunking-channel-send.gif)  
  
 <span data-ttu-id="4250c-147">No lado do recebimento, `ChunkingChannel` efetua pull das mensagens do canal interno e passa-os para um personalizado <xref:System.Xml.XmlDictionaryReader> chamado `ChunkingReader`, qual reconstitui a mensagem original das partes de entrada.</span><span class="sxs-lookup"><span data-stu-id="4250c-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="4250c-148">`ChunkingChannel` resume isso `ChunkingReader` em um personalizado `Message` implementação chamado `ChunkingMessage` e retorna essa mensagem para a camada acima.</span><span class="sxs-lookup"><span data-stu-id="4250c-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="4250c-149">Essa combinação de `ChunkingReader` e `ChunkingMessage` permite dividir desprovisionar o corpo da mensagem original como ele está sendo lido pela camada acima em vez de precisar armazenar em buffer o corpo da mensagem original inteira.</span><span class="sxs-lookup"><span data-stu-id="4250c-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="4250c-150">`ChunkingReader` tem uma fila em que ele armazena em buffer partes de entrada até um máximo número configurável de partes em buffer.</span><span class="sxs-lookup"><span data-stu-id="4250c-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="4250c-151">Quando esse limite máximo for atingido, o leitor aguarda a ser extraído da fila pela camada acima de mensagens (ou seja, lendo apenas do corpo da mensagem original) ou até que receba o máximo tempo limite for atingido.</span><span class="sxs-lookup"><span data-stu-id="4250c-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>  
  
 ![Diagrama que mostra o canal de agrupamento receber arquitetura.](./media/chunking-channel/chunking-channel-receive.gif)  
  
## <a name="chunking-programming-model"></a><span data-ttu-id="4250c-153">Modelo de programação de agrupamento</span><span class="sxs-lookup"><span data-stu-id="4250c-153">Chunking Programming Model</span></span>  
 <span data-ttu-id="4250c-154">Os desenvolvedores de serviço podem especificar quais mensagens devem ser em partes, aplicando o `ChunkingBehavior` de atributo para operações no contrato.</span><span class="sxs-lookup"><span data-stu-id="4250c-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="4250c-155">O atributo expõe um `AppliesTo` propriedade que permite que o desenvolvedor Especifique se agrupamento se aplica a mensagem de entrada, a mensagem de saída ou ambos.</span><span class="sxs-lookup"><span data-stu-id="4250c-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="4250c-156">O exemplo a seguir mostra o uso de `ChunkingBehavior` atributo:</span><span class="sxs-lookup"><span data-stu-id="4250c-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>  
  
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
  
 <span data-ttu-id="4250c-157">Do modelo de programação, o `ChunkingBindingElement` compila uma lista de URIs que identificam as mensagens para ser em partes de ação.</span><span class="sxs-lookup"><span data-stu-id="4250c-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="4250c-158">A ação de cada mensagem de saída é comparada com essa lista para determinar se a mensagem deve ser em partes ou enviada diretamente.</span><span class="sxs-lookup"><span data-stu-id="4250c-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>  
  
## <a name="implementing-the-send-operation"></a><span data-ttu-id="4250c-159">Implementando a operação de envio</span><span class="sxs-lookup"><span data-stu-id="4250c-159">Implementing the Send Operation</span></span>  
 <span data-ttu-id="4250c-160">Em um alto nível, a operação de envio primeiro verifica se a mensagem de saída deve ser em bloco e, se não, envia a mensagem diretamente usando o canal interno.</span><span class="sxs-lookup"><span data-stu-id="4250c-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>  
  
 <span data-ttu-id="4250c-161">Se a mensagem deve ser em bloco, envio cria um novo `ChunkingWriter` e chama `WriteBodyContents` na mensagem de saída passá-lo isso `ChunkingWriter`.</span><span class="sxs-lookup"><span data-stu-id="4250c-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="4250c-162">O `ChunkingWriter` e em seguida, faz a divisão de mensagem (incluindo copiar cabeçalhos da mensagem original para a mensagem de bloco de início) e envia partes usando o canal interno.</span><span class="sxs-lookup"><span data-stu-id="4250c-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>  
  
 <span data-ttu-id="4250c-163">Alguns detalhes que vale a pena observar:</span><span class="sxs-lookup"><span data-stu-id="4250c-163">A few details worth noting:</span></span>  
  
-   <span data-ttu-id="4250c-164">Enviar primeiro chama `ThrowIfDisposedOrNotOpened` para garantir que o `CommunicationState` é aberto.</span><span class="sxs-lookup"><span data-stu-id="4250c-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>  
  
-   <span data-ttu-id="4250c-165">Enviando é sincronizada para que somente uma mensagem possa ser enviada por vez para cada sessão.</span><span class="sxs-lookup"><span data-stu-id="4250c-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="4250c-166">Há um `ManualResetEvent` chamado `sendingDone` que é redefinido quando uma mensagem em partes que está sendo enviada.</span><span class="sxs-lookup"><span data-stu-id="4250c-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="4250c-167">Depois que a mensagem de bloco final é enviada, esse evento é definido.</span><span class="sxs-lookup"><span data-stu-id="4250c-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="4250c-168">O método de envio aguarda para este evento a ser definido antes de tentar enviar a mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="4250c-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>  
  
-   <span data-ttu-id="4250c-169">Bloqueios de enviar o `CommunicationObject.ThisLock` evitar sincronizado as alterações de estado durante o envio.</span><span class="sxs-lookup"><span data-stu-id="4250c-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="4250c-170">Consulte a <xref:System.ServiceModel.Channels.CommunicationObject> documentação para obter mais informações sobre <xref:System.ServiceModel.Channels.CommunicationObject> estados e a máquina de estado.</span><span class="sxs-lookup"><span data-stu-id="4250c-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>  
  
-   <span data-ttu-id="4250c-171">O tempo limite passado para o envio é usado como o tempo limite para a operação de envio inteira que inclui o envio de todos os fragmentos.</span><span class="sxs-lookup"><span data-stu-id="4250c-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>  
  
-   <span data-ttu-id="4250c-172">Personalizado <xref:System.Xml.XmlDictionaryWriter> design foi escolhido para evitar o armazenamento em buffer o corpo da mensagem original inteira.</span><span class="sxs-lookup"><span data-stu-id="4250c-172">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="4250c-173">Se tivéssemos uma <xref:System.Xml.XmlDictionaryReader> sobre como usar o corpo `message.GetReaderAtBodyContents` buffer de todo o corpo.</span><span class="sxs-lookup"><span data-stu-id="4250c-173">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="4250c-174">Em vez disso, temos um personalizado <xref:System.Xml.XmlDictionaryWriter> que é passado para `message.WriteBodyContents`.</span><span class="sxs-lookup"><span data-stu-id="4250c-174">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="4250c-175">Como a mensagem chamadas WriteBase64 no gravador, o gravador de partes em mensagens de pacotes e as envia usando o canal interno.</span><span class="sxs-lookup"><span data-stu-id="4250c-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="4250c-176">Blocos de WriteBase64 até que a parte seja enviada.</span><span class="sxs-lookup"><span data-stu-id="4250c-176">WriteBase64 blocks until the chunk is sent.</span></span>  
  
## <a name="implementing-the-receive-operation"></a><span data-ttu-id="4250c-177">Implementando a operação de recebimento</span><span class="sxs-lookup"><span data-stu-id="4250c-177">Implementing the Receive Operation</span></span>  
 <span data-ttu-id="4250c-178">Em um alto nível, a operação de recebimento primeiro verifica se a mensagem de entrada não é `null` e que sua ação é o `ChunkingAction`.</span><span class="sxs-lookup"><span data-stu-id="4250c-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="4250c-179">Se ele não atender a ambos os critérios, a mensagem é retornada inalterada de recebimento.</span><span class="sxs-lookup"><span data-stu-id="4250c-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="4250c-180">Caso contrário, o recebimento cria um novo `ChunkingReader` e uma nova `ChunkingMessage` encapsulado em torno dele (chamando `GetNewChunkingMessage`).</span><span class="sxs-lookup"><span data-stu-id="4250c-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="4250c-181">Antes de retornar que novos `ChunkingMessage`, Receive usa um thread de pool de threads para executar `ReceiveChunkLoop`, que chama `innerChannel.Receive` em um loop e entrega o partes para o `ChunkingReader` até que a mensagem de bloco final é recebida ou o tempo limite de recebimento for atingido.</span><span class="sxs-lookup"><span data-stu-id="4250c-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>  
  
 <span data-ttu-id="4250c-182">Alguns detalhes que vale a pena observar:</span><span class="sxs-lookup"><span data-stu-id="4250c-182">A few details worth noting:</span></span>  
  
-   <span data-ttu-id="4250c-183">Como enviar, receber chamadas primeiro `ThrowIfDisposedOrNotOepned` para garantir que o `CommunicationState` é aberto.</span><span class="sxs-lookup"><span data-stu-id="4250c-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>  
  
-   <span data-ttu-id="4250c-184">Receba também são sincronizados para que somente uma mensagem pode ser recebida por vez da sessão.</span><span class="sxs-lookup"><span data-stu-id="4250c-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="4250c-185">Isso é especialmente importante, porque depois que uma mensagem de bloco de início for recebida, todas as mensagens recebidas subsequentes devem ser partes dentro essa nova sequência de bloco até que uma mensagem de bloco final seja recebida.</span><span class="sxs-lookup"><span data-stu-id="4250c-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="4250c-186">Receber não pode extrair mensagens do canal interno até que todas as partes que pertencem à mensagem atualmente desprovisionar sendo em partes são recebidas.</span><span class="sxs-lookup"><span data-stu-id="4250c-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="4250c-187">Para fazer isso, receber usa um `ManualResetEvent` denominado `currentMessageCompleted`, que é definido quando a mensagem de bloco final é recebida e redefinir quando uma nova mensagem de bloco de início é recebida.</span><span class="sxs-lookup"><span data-stu-id="4250c-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>  
  
-   <span data-ttu-id="4250c-188">Ao contrário de envio, recebimento não impede que as transições de estado sincronizado durante a recepção.</span><span class="sxs-lookup"><span data-stu-id="4250c-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="4250c-189">Por exemplo, fechar pode ser chamado durante o recebimento e aguarda até que o recebimento pendente da mensagem original é concluído ou o valor de tempo limite especificado for atingido.</span><span class="sxs-lookup"><span data-stu-id="4250c-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>  
  
-   <span data-ttu-id="4250c-190">O tempo limite passado para o recebimento é usado como o tempo limite para toda a operação, que inclui o recebimento de todas as partes de recebimento.</span><span class="sxs-lookup"><span data-stu-id="4250c-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>  
  
-   <span data-ttu-id="4250c-191">Se a camada que consome a mensagem está consumindo o corpo da mensagem a uma taxa menor do que a taxa de bloco de mensagens de entrada, o `ChunkingReader` buffers essas partes de entrada até o limite especificado pela `ChunkingBindingElement.MaxBufferedChunks`.</span><span class="sxs-lookup"><span data-stu-id="4250c-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="4250c-192">Quando esse limite é atingido, não há mais blocos são extraídos da camada inferior até que uma parte em buffer é consumida ou o tempo limite de recebimento for atingido.</span><span class="sxs-lookup"><span data-stu-id="4250c-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>  
  
## <a name="communicationobject-overrides"></a><span data-ttu-id="4250c-193">Substituições de CommunicationObject</span><span class="sxs-lookup"><span data-stu-id="4250c-193">CommunicationObject Overrides</span></span>  
  
### <a name="onopen"></a><span data-ttu-id="4250c-194">OnOpen</span><span class="sxs-lookup"><span data-stu-id="4250c-194">OnOpen</span></span>  
 <span data-ttu-id="4250c-195">`OnOpen` chamadas `innerChannel.Open` para abrir o canal interno.</span><span class="sxs-lookup"><span data-stu-id="4250c-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>  
  
### <a name="onclose"></a><span data-ttu-id="4250c-196">OnClose</span><span class="sxs-lookup"><span data-stu-id="4250c-196">OnClose</span></span>  
 <span data-ttu-id="4250c-197">`OnClose` primeiro define `stopReceive` à `true` para sinalizar o pendente `ReceiveChunkLoop` para parar.</span><span class="sxs-lookup"><span data-stu-id="4250c-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="4250c-198">Ele aguarda até que o `receiveStopped` <xref:System.Threading.ManualResetEvent>, que é definido quando `ReceiveChunkLoop` para.</span><span class="sxs-lookup"><span data-stu-id="4250c-198">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="4250c-199">Supondo que o `ReceiveChunkLoop` para de dentro do tempo limite especificado, `OnClose` chamadas `innerChannel.Close` com o tempo limite restante.</span><span class="sxs-lookup"><span data-stu-id="4250c-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>  
  
### <a name="onabort"></a><span data-ttu-id="4250c-200">OnAbort</span><span class="sxs-lookup"><span data-stu-id="4250c-200">OnAbort</span></span>  
 <span data-ttu-id="4250c-201">`OnAbort` chamadas `innerChannel.Abort` para anular o canal interno.</span><span class="sxs-lookup"><span data-stu-id="4250c-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="4250c-202">Se não houver um pendente `ReceiveChunkLoop` ele obtém uma exceção a partir de pendente `innerChannel.Receive` chamar.</span><span class="sxs-lookup"><span data-stu-id="4250c-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>  
  
### <a name="onfaulted"></a><span data-ttu-id="4250c-203">OnFaulted</span><span class="sxs-lookup"><span data-stu-id="4250c-203">OnFaulted</span></span>  
 <span data-ttu-id="4250c-204">O `ChunkingChannel` não exige um comportamento especial quando o canal está com defeito isso `OnFaulted` não for substituído.</span><span class="sxs-lookup"><span data-stu-id="4250c-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>  
  
## <a name="implementing-channel-factory"></a><span data-ttu-id="4250c-205">Implementação de fábrica de canais</span><span class="sxs-lookup"><span data-stu-id="4250c-205">Implementing Channel Factory</span></span>  
 <span data-ttu-id="4250c-206">O `ChunkingChannelFactory` é responsável pela criação de instâncias de `ChunkingDuplexSessionChannel` e para as transições de estado em cascata para a fábrica de canais interna.</span><span class="sxs-lookup"><span data-stu-id="4250c-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>  
  
 <span data-ttu-id="4250c-207">`OnCreateChannel` usa a fábrica de canais interna para criar um `IDuplexSessionChannel` canal interno.</span><span class="sxs-lookup"><span data-stu-id="4250c-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="4250c-208">Em seguida, cria um novo `ChunkingDuplexSessionChannel` passá-lo neste canal interno juntamente com a lista de ações de mensagem a ser em bloco e o número máximo de blocos para armazenar em buffer após o recebimento.</span><span class="sxs-lookup"><span data-stu-id="4250c-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="4250c-209">A lista de ações de mensagem a ser em bloco e o número máximo de blocos para armazenar em buffer são dois parâmetros passados para `ChunkingChannelFactory` em seu construtor.</span><span class="sxs-lookup"><span data-stu-id="4250c-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="4250c-210">A seção sobre `ChunkingBindingElement` descreve de onde vêm esses valores.</span><span class="sxs-lookup"><span data-stu-id="4250c-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>  
  
 <span data-ttu-id="4250c-211">O `OnOpen`, `OnClose`, `OnAbort` e seus equivalentes assíncronos chame o método de transição de estado correspondente na fábrica de canais interna.</span><span class="sxs-lookup"><span data-stu-id="4250c-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>  
  
## <a name="implementing-channel-listener"></a><span data-ttu-id="4250c-212">Implementando o ouvinte de canais</span><span class="sxs-lookup"><span data-stu-id="4250c-212">Implementing Channel Listener</span></span>  
 <span data-ttu-id="4250c-213">O `ChunkingChannelListener` é um wrapper em torno de um ouvinte de canais interna.</span><span class="sxs-lookup"><span data-stu-id="4250c-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="4250c-214">Sua função principal, além de chamadas de delegados para esse ouvinte de canais interna, é encapsular novo `ChunkingDuplexSessionChannels` em torno de canais aceitos de ouvinte de canais interno.</span><span class="sxs-lookup"><span data-stu-id="4250c-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="4250c-215">Isso é feito no `OnAcceptChannel` e `OnEndAcceptChannel`.</span><span class="sxs-lookup"><span data-stu-id="4250c-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="4250c-216">Recém-criado `ChunkingDuplexSessionChannel` é passado o canal interno juntamente com os outros parâmetros descritos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4250c-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>  
  
## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="4250c-217">Implementando o elemento de associação e associação</span><span class="sxs-lookup"><span data-stu-id="4250c-217">Implementing Binding Element and Binding</span></span>  
 <span data-ttu-id="4250c-218">`ChunkingBindingElement` é responsável por criar a `ChunkingChannelFactory` e `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="4250c-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="4250c-219">O `ChunkingBindingElement` verifica se T no `CanBuildChannelFactory` \<T > e `CanBuildChannelListener` \<T > é do tipo `IDuplexSessionChannel` (o único canal com suporte pelo canal de agrupamento) e que os outros elementos de associação na associação de dar suporte a isso tipo de canal.</span><span class="sxs-lookup"><span data-stu-id="4250c-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>  
  
 <span data-ttu-id="4250c-220">`BuildChannelFactory`\<T > primeiro verifica se o tipo de canal solicitada pode ser compilado e, em seguida, obtém uma lista de ações de mensagem a ser em bloco.</span><span class="sxs-lookup"><span data-stu-id="4250c-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="4250c-221">Para obter mais informações, consulte a seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="4250c-221">For more information, see the following section.</span></span> <span data-ttu-id="4250c-222">Em seguida, cria uma nova `ChunkingChannelFactory` passá-lo a fábrica de canais interna (como retornado pelo `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), a lista de ações de mensagem e o número máximo de blocos para armazenar em buffer.</span><span class="sxs-lookup"><span data-stu-id="4250c-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="4250c-223">O número máximo de partes vem de uma propriedade chamada `MaxBufferedChunks` expostos pelo `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="4250c-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>  
  
 <span data-ttu-id="4250c-224">`BuildChannelListener<T>` tem uma implementação semelhante para a criação de `ChunkingChannelListener` e passando-o ouvinte de canais interna.</span><span class="sxs-lookup"><span data-stu-id="4250c-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>  
  
 <span data-ttu-id="4250c-225">Há uma associação de exemplo incluída neste exemplo denominado `TcpChunkingBinding`.</span><span class="sxs-lookup"><span data-stu-id="4250c-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="4250c-226">Essa ligação consiste em dois elementos de associação: `TcpTransportBindingElement` e `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="4250c-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="4250c-227">Além de expor a `MaxBufferedChunks` propriedade, a associação também define algumas da `TcpTransportBindingElement` propriedades, como `MaxReceivedMessageSize` (define como `ChunkingUtils.ChunkSize` + 100 KB bytes para os cabeçalhos).</span><span class="sxs-lookup"><span data-stu-id="4250c-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>  
  
 <span data-ttu-id="4250c-228">`TcpChunkingBinding` também implementa `IBindingRuntimePreferences` e retorna true do `ReceiveSynchronously` método que indica que apenas as receber chamadas síncronas são implementadas.</span><span class="sxs-lookup"><span data-stu-id="4250c-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>  
  
### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="4250c-229">Determinando quais mensagens para o fragmento</span><span class="sxs-lookup"><span data-stu-id="4250c-229">Determining Which Messages To Chunk</span></span>  
 <span data-ttu-id="4250c-230">O canal de agrupamento reparte apenas as mensagens identificadas por meio de `ChunkingBehavior` atributo.</span><span class="sxs-lookup"><span data-stu-id="4250c-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="4250c-231">O `ChunkingBehavior` classe implementa `IOperationBehavior` e é implementado por meio da chamada a `AddBindingParameter` método.</span><span class="sxs-lookup"><span data-stu-id="4250c-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="4250c-232">Nesse método, o `ChunkingBehavior` examina o valor do seu `AppliesTo` propriedade (`InMessage`, `OutMessage` ou ambos) para determinar quais mensagens devem ser em bloco.</span><span class="sxs-lookup"><span data-stu-id="4250c-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="4250c-233">Então obtém a ação de cada uma dessas mensagens (da coleção de mensagens no `OperationDescription`) e o adiciona a uma coleção de cadeia de caracteres contida em uma instância do `ChunkingBindingParameter`.</span><span class="sxs-lookup"><span data-stu-id="4250c-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="4250c-234">Em seguida, adiciona esses `ChunkingBindingParameter` nas `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="4250c-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>  
  
 <span data-ttu-id="4250c-235">Isso `BindingParameterCollection` é passado dentro do `BindingContext` a cada elemento de associação na associação quando esse elemento de associação cria a fábrica de canais ou o ouvinte de canais.</span><span class="sxs-lookup"><span data-stu-id="4250c-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="4250c-236">O `ChunkingBindingElement`da implementação de `BuildChannelFactory<T>` e `BuildChannelListener<T>` puxar isto `ChunkingBindingParameter` fora dos `BindingContext’`s `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="4250c-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="4250c-237">A coleção de ações contidas dentro de `ChunkingBindingParameter` é então passado para o `ChunkingChannelFactory` ou `ChunkingChannelListener`, que por sua vez o passa para o `ChunkingDuplexSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="4250c-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="4250c-238">A execução do exemplo</span><span class="sxs-lookup"><span data-stu-id="4250c-238">Running the Sample</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4250c-239">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4250c-239">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4250c-240">Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="4250c-240">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="4250c-241">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4250c-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="4250c-242">Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4250c-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="4250c-243">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4250c-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="4250c-244">Executar Service.exe primeiro, execute Client.exe e assista a ambas as janelas do console de saída.</span><span class="sxs-lookup"><span data-stu-id="4250c-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>  
  
 <span data-ttu-id="4250c-245">Ao executar o exemplo, a seguinte saída é esperada.</span><span class="sxs-lookup"><span data-stu-id="4250c-245">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="4250c-246">Cliente:</span><span class="sxs-lookup"><span data-stu-id="4250c-246">Client:</span></span>  
  
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
  
 <span data-ttu-id="4250c-247">Servidor:</span><span class="sxs-lookup"><span data-stu-id="4250c-247">Server:</span></span>  
  
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
