---
title: "Objetos binários de codificação com codificador ByteStream"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cf68356ffa5fe20de7bd417c77388cd214ca718
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a><span data-ttu-id="404c7-102">Objetos binários de codificação com codificador ByteStream</span><span class="sxs-lookup"><span data-stu-id="404c7-102">Encoding Binary Objects with ByteStream Encoder</span></span>
<span data-ttu-id="404c7-103">Enviar e receber dados binários brutos com [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é configurado usando <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="404c7-103">Sending and receiving raw binary data with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is configured using <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span></span>  
  
## <a name="byte-stream-message-encoder-architecture"></a><span data-ttu-id="404c7-104">Arquitetura de codificador de mensagem de fluxo de bytes</span><span class="sxs-lookup"><span data-stu-id="404c7-104">Byte Stream Message Encoder Architecture</span></span>  
 <span data-ttu-id="404c7-105">O codificador de mensagem binária usado pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não têm recursos para processamento, validar ou identificar os dados binários subjacentes na mensagem.</span><span class="sxs-lookup"><span data-stu-id="404c7-105">The binary message encoder used by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] has no facility for processing, validating, or identifying the underlying binary data in the message.</span></span> <span data-ttu-id="404c7-106">O pacote de dados é codificado em XML, enviado, recebido e decodificar.</span><span class="sxs-lookup"><span data-stu-id="404c7-106">The data package is encoded into XML, sent, received, and decoded.</span></span> <span data-ttu-id="404c7-107">O codificador processa os dados após ser transmitido para o transporte e antes que a mensagem é enviada para a fila de mensagens.</span><span class="sxs-lookup"><span data-stu-id="404c7-107">The encoder processes the data after being passed to the transport and before the message is sent to the message queue.</span></span> <span data-ttu-id="404c7-108">Funcionalmente, o codificador binário encapsula os dados da mensagem em `<binary>` elementos para enviar e remove os elementos após receber a mensagem.</span><span class="sxs-lookup"><span data-stu-id="404c7-108">Functionally, the binary encoder wraps the message data in `<binary>` elements for sending and removes the elements after the message is received.</span></span>  
  
## <a name="using-the-byte-stream-message-encoder"></a><span data-ttu-id="404c7-109">Usando o codificador de mensagens do fluxo de bytes</span><span class="sxs-lookup"><span data-stu-id="404c7-109">Using the Byte Stream Message Encoder</span></span>  
 <span data-ttu-id="404c7-110">O exemplo a seguir mostra um contrato de serviço que implementa o codificador de mensagens do fluxo de bytes.</span><span class="sxs-lookup"><span data-stu-id="404c7-110">The following example shows a service contract that implements the byte stream message encoder.</span></span>  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 <span data-ttu-id="404c7-111">O exemplo a seguir mostra o serviço que está sendo invocado.</span><span class="sxs-lookup"><span data-stu-id="404c7-111">The following example shows the service being invoked.</span></span>  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 <span data-ttu-id="404c7-112">No caso de uso de um serviço que implementa uma infraestrutura de mensagem (como um roteador), a mensagem é processada sem inspecionando, validar ou caso contrário, interagir com a mensagem, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="404c7-112">In the case of using a service that implements a message infrastructure (such as a router), the message is processed without inspecting, validating, or otherwise interacting with the message, as shown in the following example.</span></span>  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a><span data-ttu-id="404c7-113">Cenários</span><span class="sxs-lookup"><span data-stu-id="404c7-113">Scenarios</span></span>  
 <span data-ttu-id="404c7-114">O codificador de fluxo de bytes é útil nas seguintes situações.</span><span class="sxs-lookup"><span data-stu-id="404c7-114">The Byte Stream Encoder is useful in the following scenarios.</span></span>  
  
-   <span data-ttu-id="404c7-115">Transferência de uma imagem JPEG entre computadores usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="404c7-115">Transferring a JPEG image between computers using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="404c7-116">Nesse cenário, a imagem será enviado por meio do transporte de uma fonte externa, e os dados enviados serão os bytes brutos que compõem a imagem.</span><span class="sxs-lookup"><span data-stu-id="404c7-116">In this scenario, the image will arrive through the transport from an outside source, and the data sent will be the raw bytes that make up the image.</span></span> <span data-ttu-id="404c7-117">Um serviço receberá os dados binários e exibir a imagem.</span><span class="sxs-lookup"><span data-stu-id="404c7-117">A service will receive the binary data and display the image.</span></span>  
  
-   <span data-ttu-id="404c7-118">Ler informações de fora de uma fila de mensagens e processá-la.</span><span class="sxs-lookup"><span data-stu-id="404c7-118">Reading information out of a message queue and processing it.</span></span> <span data-ttu-id="404c7-119">A mensagem será lido de um Gerenciador de fila de mensagens e passada o canal de mensagens da fila devem ser tratados.</span><span class="sxs-lookup"><span data-stu-id="404c7-119">The message will be read from a message queue manager, and passed up the message queue channel to be handled.</span></span> <span data-ttu-id="404c7-120">O canal de mensagens da fila atuará como um Gerenciador de filas na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="404c7-120">The message queue channel will act as a queue manager in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel stack.</span></span>  
  
 <span data-ttu-id="404c7-121">No caso de enviar uma mensagem por um canal de mensagens da fila, o remetente não tem controle sobre os bytes recebidos do Gerenciador de fila.</span><span class="sxs-lookup"><span data-stu-id="404c7-121">In the case of sending a message over a message queue channel, the sender has no control over the bytes received from the queue manager.</span></span> <span data-ttu-id="404c7-122">Se o processo de recebimento não tem nenhum recurso para ler os bytes brutos, a mensagem será recebida como mal formatado e não será processada; presume-se que o processo de recebimento terá a capacidade de converter os bytes recebidos para um formato utilizável.</span><span class="sxs-lookup"><span data-stu-id="404c7-122">If the receiving process has no capability to read raw bytes, the message will be received as badly formatted and will not be processed; it is assumed that the receiving process will have the capability of translating the received bytes back into a usable format.</span></span>
