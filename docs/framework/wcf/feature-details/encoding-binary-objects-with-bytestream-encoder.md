---
title: Objetos binários de codificação com codificador ByteStream
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 09a919e11971f81bc76dca0e45a7eb0e70ef749e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626933"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a><span data-ttu-id="b6871-102">Objetos binários de codificação com codificador ByteStream</span><span class="sxs-lookup"><span data-stu-id="b6871-102">Encoding Binary Objects with ByteStream Encoder</span></span>
<span data-ttu-id="b6871-103">Enviar e receber dados binários brutos com o Windows Communication Foundation (WCF) é configurado usando <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="b6871-103">Sending and receiving raw binary data with Windows Communication Foundation (WCF) is configured using <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span></span>  
  
## <a name="byte-stream-message-encoder-architecture"></a><span data-ttu-id="b6871-104">Arquitetura de codificador de mensagem do byte Stream</span><span class="sxs-lookup"><span data-stu-id="b6871-104">Byte Stream Message Encoder Architecture</span></span>  
 <span data-ttu-id="b6871-105">O codificador de mensagem binária usado pelo WCF não têm recursos para processar, validar ou identificando os dados binários subjacentes na mensagem.</span><span class="sxs-lookup"><span data-stu-id="b6871-105">The binary message encoder used by WCF has no facility for processing, validating, or identifying the underlying binary data in the message.</span></span> <span data-ttu-id="b6871-106">O pacote de dados é codificado em XML, enviado, recebido e decodificado.</span><span class="sxs-lookup"><span data-stu-id="b6871-106">The data package is encoded into XML, sent, received, and decoded.</span></span> <span data-ttu-id="b6871-107">O codificador processa os dados após ser transmitido para o transporte e antes da mensagem é enviada para a fila de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b6871-107">The encoder processes the data after being passed to the transport and before the message is sent to the message queue.</span></span> <span data-ttu-id="b6871-108">Funcionalmente, o codificador binário encapsula os dados da mensagem em `<binary>` elementos para o envio e remove os elementos depois que a mensagem é recebida.</span><span class="sxs-lookup"><span data-stu-id="b6871-108">Functionally, the binary encoder wraps the message data in `<binary>` elements for sending and removes the elements after the message is received.</span></span>  
  
## <a name="using-the-byte-stream-message-encoder"></a><span data-ttu-id="b6871-109">Usando o codificador de mensagem do Byte Stream</span><span class="sxs-lookup"><span data-stu-id="b6871-109">Using the Byte Stream Message Encoder</span></span>  
 <span data-ttu-id="b6871-110">O exemplo a seguir mostra um contrato de serviço que implementa o codificador de mensagem de fluxo de bytes.</span><span class="sxs-lookup"><span data-stu-id="b6871-110">The following example shows a service contract that implements the byte stream message encoder.</span></span>  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 <span data-ttu-id="b6871-111">O exemplo a seguir mostra o serviço que está sendo invocado.</span><span class="sxs-lookup"><span data-stu-id="b6871-111">The following example shows the service being invoked.</span></span>  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 <span data-ttu-id="b6871-112">No caso de uso de um serviço que implementa uma infra-estrutura de mensagem (como um roteador), a mensagem é processada sem inspecionando, validar ou caso contrário, interagir com a mensagem, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6871-112">In the case of using a service that implements a message infrastructure (such as a router), the message is processed without inspecting, validating, or otherwise interacting with the message, as shown in the following example.</span></span>  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a><span data-ttu-id="b6871-113">Cenários</span><span class="sxs-lookup"><span data-stu-id="b6871-113">Scenarios</span></span>  
 <span data-ttu-id="b6871-114">O codificador do Byte Stream é útil nos cenários a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6871-114">The Byte Stream Encoder is useful in the following scenarios.</span></span>  
  
- <span data-ttu-id="b6871-115">Transferência de uma imagem JPEG entre computadores usando o WCF.</span><span class="sxs-lookup"><span data-stu-id="b6871-115">Transferring a JPEG image between computers using WCF.</span></span> <span data-ttu-id="b6871-116">Nesse cenário, a imagem será chegam por meio do transporte de uma fonte externa e os dados enviados serão os bytes brutos que compõem a imagem.</span><span class="sxs-lookup"><span data-stu-id="b6871-116">In this scenario, the image will arrive through the transport from an outside source, and the data sent will be the raw bytes that make up the image.</span></span> <span data-ttu-id="b6871-117">Um serviço receberá os dados binários e exibir a imagem.</span><span class="sxs-lookup"><span data-stu-id="b6871-117">A service will receive the binary data and display the image.</span></span>  
  
- <span data-ttu-id="b6871-118">Ler informações de fora de uma fila de mensagens e processá-la.</span><span class="sxs-lookup"><span data-stu-id="b6871-118">Reading information out of a message queue and processing it.</span></span> <span data-ttu-id="b6871-119">A mensagem será ler de um Gerenciador de fila de mensagens e passada para cima o canal de mensagens da fila a ser manipulado.</span><span class="sxs-lookup"><span data-stu-id="b6871-119">The message will be read from a message queue manager, and passed up the message queue channel to be handled.</span></span> <span data-ttu-id="b6871-120">O canal de mensagens da fila atuará como um Gerenciador de fila na pilha de canais do WCF.</span><span class="sxs-lookup"><span data-stu-id="b6871-120">The message queue channel will act as a queue manager in the WCF channel stack.</span></span>  
  
 <span data-ttu-id="b6871-121">No caso de enviar uma mensagem sobre um canal de mensagens da fila, o remetente não tem controle sobre os bytes recebidos do Gerenciador de fila.</span><span class="sxs-lookup"><span data-stu-id="b6871-121">In the case of sending a message over a message queue channel, the sender has no control over the bytes received from the queue manager.</span></span> <span data-ttu-id="b6871-122">Se o processo de recebimento não tem nenhum recurso para ler os bytes brutos, a mensagem será recebida medida formatada incorretamente e não serão processados; supõe-se que o processo de recebimento terão a capacidade de converter os bytes recebidos para um formato utilizável.</span><span class="sxs-lookup"><span data-stu-id="b6871-122">If the receiving process has no capability to read raw bytes, the message will be received as badly formatted and will not be processed; it is assumed that the receiving process will have the capability of translating the received bytes back into a usable format.</span></span>
