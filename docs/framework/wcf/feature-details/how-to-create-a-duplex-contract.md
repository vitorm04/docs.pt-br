---
title: Como criar um contrato duplex
description: Saiba como criar um contrato duplex, que permite que clientes e servidores WCF se comuniquem entre si de forma independente. O pode iniciar chamadas para o outro.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: 9320e5b36b8faba3602fbe1df1b95c05dcc7fa7e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247085"
---
# <a name="how-to-create-a-duplex-contract"></a><span data-ttu-id="dc518-104">Como criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="dc518-104">How to: Create a Duplex Contract</span></span>
<span data-ttu-id="dc518-105">Este tópico mostra as etapas básicas para criar métodos que usam um contrato duplex (bidirecional).</span><span class="sxs-lookup"><span data-stu-id="dc518-105">This topic shows the basic steps to create methods that use a duplex (two-way) contract.</span></span> <span data-ttu-id="dc518-106">Um contrato duplex permite que os clientes e os servidores se comuniquem entre si independentemente, de modo que qualquer um possa iniciar chamadas para o outro.</span><span class="sxs-lookup"><span data-stu-id="dc518-106">A duplex contract allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="dc518-107">O contrato duplex é um dos três padrões de mensagem disponíveis para os serviços Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="dc518-107">The duplex contract is one of three message patterns available to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="dc518-108">Os outros padrões de duas mensagens são unidirecionais e solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="dc518-108">The other two message patterns are one-way and request-reply.</span></span> <span data-ttu-id="dc518-109">Um contrato duplex consiste de dois contratos unidirecionais entre o cliente e o servidor e não exige que as chamadas de método sejam correlacionadas.</span><span class="sxs-lookup"><span data-stu-id="dc518-109">A duplex contract consists of two one-way contracts between the client and the server and does not require that the method calls be correlated.</span></span> <span data-ttu-id="dc518-110">Use esse tipo de contrato quando o serviço tiver que consultar o cliente para obter mais informações ou explicitamente gerar eventos no cliente.</span><span class="sxs-lookup"><span data-stu-id="dc518-110">Use this kind of contract when your service must query the client for more information or explicitly raise events on the client.</span></span> <span data-ttu-id="dc518-111">Para obter mais informações sobre como criar um aplicativo cliente para um contrato duplex, consulte [como acessar serviços com um contrato duplex](how-to-access-services-with-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="dc518-111">For more information about creating a client application for a duplex contract, see [How to: Access Services with a Duplex Contract](how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="dc518-112">Para obter um exemplo funcional, consulte o exemplo de [duplex](../samples/duplex.md) .</span><span class="sxs-lookup"><span data-stu-id="dc518-112">For a working sample, see the [Duplex](../samples/duplex.md) sample.</span></span>  
  
### <a name="to-create-a-duplex-contract"></a><span data-ttu-id="dc518-113">Para criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="dc518-113">To create a duplex contract</span></span>  
  
1. <span data-ttu-id="dc518-114">Crie a interface que compõem o lado do servidor do contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="dc518-114">Create the interface that makes up the server side of the duplex contract.</span></span>  
  
2. <span data-ttu-id="dc518-115">Aplique a classe <xref:System.ServiceModel.ServiceContractAttribute> à interface.</span><span class="sxs-lookup"><span data-stu-id="dc518-115">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. <span data-ttu-id="dc518-116">Declare as assinaturas de método na interface.</span><span class="sxs-lookup"><span data-stu-id="dc518-116">Declare the method signatures in the interface.</span></span>  
  
4. <span data-ttu-id="dc518-117">Aplique a classe <xref:System.ServiceModel.OperationContractAttribute> a cada assinatura de método que deve ser parte do contrato público.</span><span class="sxs-lookup"><span data-stu-id="dc518-117">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
5. <span data-ttu-id="dc518-118">Crie a interface de retorno de chamada que define o conjunto de operações que o serviço pode chamar no cliente.</span><span class="sxs-lookup"><span data-stu-id="dc518-118">Create the callback interface that defines the set of operations that the service can invoke on the client.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. <span data-ttu-id="dc518-119">Declare as assinaturas de método na interface de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="dc518-119">Declare the method signatures in the callback interface.</span></span>  
  
7. <span data-ttu-id="dc518-120">Aplique a classe <xref:System.ServiceModel.OperationContractAttribute> a cada assinatura de método que deve ser parte do contrato público.</span><span class="sxs-lookup"><span data-stu-id="dc518-120">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
8. <span data-ttu-id="dc518-121">Vincular as duas interfaces em um contrato duplex definindo a propriedade <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> na interface primária para o tipo da interface de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="dc518-121">Link the two interfaces into a duplex contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property in the primary interface to the type of the callback interface.</span></span>  
  
### <a name="to-call-methods-on-the-client"></a><span data-ttu-id="dc518-122">Para chamar métodos no cliente</span><span class="sxs-lookup"><span data-stu-id="dc518-122">To call methods on the client</span></span>  
  
1. <span data-ttu-id="dc518-123">Na implementação de serviço do contrato primário, declare uma variável para a interface de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="dc518-123">In the service's implementation of the primary contract, declare a variable for the callback interface.</span></span>  
  
2. <span data-ttu-id="dc518-124">Defina a variável para a referência de objeto retornada pelo método <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> da classe <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="dc518-124">Set the variable to the object reference returned by the <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> method of the <xref:System.ServiceModel.OperationContext> class.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. <span data-ttu-id="dc518-125">Chame os métodos definidos pela interface de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="dc518-125">Call the methods defined by the callback interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc518-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc518-126">Example</span></span>  
 <span data-ttu-id="dc518-127">O exemplo de código a seguir demonstra a comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="dc518-127">The following code example demonstrates duplex communication.</span></span> <span data-ttu-id="dc518-128">O contrato do serviço contém operações de serviço para avançar e voltar.</span><span class="sxs-lookup"><span data-stu-id="dc518-128">The service’s contract contains service operations for moving forward and backward.</span></span> <span data-ttu-id="dc518-129">O contrato do cliente contém uma operação de serviço para relatar sua posição.</span><span class="sxs-lookup"><span data-stu-id="dc518-129">The client’s contract contains a service operation for reporting its position.</span></span>  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- <span data-ttu-id="dc518-130">Aplicar os atributos <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> permite a geração automática de definições do contrato de serviço na linguagem WSDL.</span><span class="sxs-lookup"><span data-stu-id="dc518-130">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes allows the automatic generation of service contract definitions in the Web Services Description Language (WSDL).</span></span>  
  
- <span data-ttu-id="dc518-131">Use a [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) para recuperar o documento WSDL e o código (opcional) e a configuração de um cliente.</span><span class="sxs-lookup"><span data-stu-id="dc518-131">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to retrieve the WSDL document and (optional) code and configuration for a client.</span></span>  
  
- <span data-ttu-id="dc518-132">Os pontos de extremidade que expõem serviços duplex devem ser protegidos.</span><span class="sxs-lookup"><span data-stu-id="dc518-132">Endpoints exposing duplex services must be secured.</span></span> <span data-ttu-id="dc518-133">Quando um serviço recebe uma mensagem duplex, ele olha o ReplyTo na mensagem de entrada para determinar para onde enviar a resposta.</span><span class="sxs-lookup"><span data-stu-id="dc518-133">When a service receives a duplex message, it looks at the ReplyTo in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="dc518-134">Se o canal não estiver protegido, um cliente não confiável poderá enviar uma mensagem mal-intencionada com um ReplyTo do computador de destino, resultando em uma negação de serviço do computador de destino.</span><span class="sxs-lookup"><span data-stu-id="dc518-134">If the channel is not secured, then an untrusted client could send a malicious message with a target machine's ReplyTo, leading to a denial of service of the target machine.</span></span> <span data-ttu-id="dc518-135">Com mensagens normais de solicitação-resposta, isso não é um problema, pois o ReplyTo é ignorado e a resposta é enviada no canal no qual a mensagem original chegou.</span><span class="sxs-lookup"><span data-stu-id="dc518-135">With regular request-reply messages, this is not an issue, because the ReplyTo is ignored and the response is sent on the channel the original message came in on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc518-136">Veja também</span><span class="sxs-lookup"><span data-stu-id="dc518-136">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="dc518-137">Como acessar serviços com um contrato Duplex</span><span class="sxs-lookup"><span data-stu-id="dc518-137">How to: Access Services with a Duplex Contract</span></span>](how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="dc518-138">Duplex</span><span class="sxs-lookup"><span data-stu-id="dc518-138">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="dc518-139">Serviços de design e implantação</span><span class="sxs-lookup"><span data-stu-id="dc518-139">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
- [<span data-ttu-id="dc518-140">Como definir um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="dc518-140">How to: Define a Service Contract</span></span>](../how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="dc518-141">Sessão</span><span class="sxs-lookup"><span data-stu-id="dc518-141">Session</span></span>](../samples/session.md)
