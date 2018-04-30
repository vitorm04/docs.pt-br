---
title: Como criar um contrato do Windows Communication Foundation com uma classe
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 54d5e1328482fc7d0c1ee33918ffae6bf7195db9
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="cef7f-102">Como criar um contrato do Windows Communication Foundation com uma classe</span><span class="sxs-lookup"><span data-stu-id="cef7f-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="cef7f-103">A melhor maneira de criar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contrato é usando uma interface.</span><span class="sxs-lookup"><span data-stu-id="cef7f-103">The preferred way of creating a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contract is by using an interface.</span></span> <span data-ttu-id="cef7f-104">Para obter mais informações, consulte [como: definir um contrato de serviço](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="cef7f-104">For more information, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="cef7f-105">Uma alternativa, descrito aqui, é criar uma classe e, em seguida, aplicar o <xref:System.ServiceModel.ServiceContractAttribute> diretamente de atributo para a classe e o <xref:System.ServiceModel.OperationContractAttribute> de atributo para cada um dos métodos na classe que fazem parte do contrato.</span><span class="sxs-lookup"><span data-stu-id="cef7f-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="cef7f-106">`[ServiceContract]` e `[ServiceContractAttribute]` fazer a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="cef7f-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="cef7f-107">A mesma coisa que ele true para `[OperationContract]` e `[OperationContractAttribute]`.</span><span class="sxs-lookup"><span data-stu-id="cef7f-107">The same thing it true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="cef7f-108">Em cada caso o anterior é abreviado para o último.</span><span class="sxs-lookup"><span data-stu-id="cef7f-108">In each case the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="cef7f-109">Para obter mais informações sobre contratos de serviço, consulte [criar contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="cef7f-109">For more information about service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="cef7f-110">Criar um contrato do Windows Communication Foundation com uma classe</span><span class="sxs-lookup"><span data-stu-id="cef7f-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1.  <span data-ttu-id="cef7f-111">Crie uma nova classe usando o Visual Basic, c# ou qualquer outra linguagem common language runtime.</span><span class="sxs-lookup"><span data-stu-id="cef7f-111">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="cef7f-112">Aplicar o <xref:System.ServiceModel.ServiceContractAttribute> classe para a classe.</span><span class="sxs-lookup"><span data-stu-id="cef7f-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3.  <span data-ttu-id="cef7f-113">Crie métodos na classe.</span><span class="sxs-lookup"><span data-stu-id="cef7f-113">Create methods in the class.</span></span>  
  
4.  <span data-ttu-id="cef7f-114">Aplicar o <xref:System.ServiceModel.OperationContractAttribute> classe para cada método que deve ser exposto como parte do público [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contrato.</span><span class="sxs-lookup"><span data-stu-id="cef7f-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cef7f-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cef7f-115">Example</span></span>  
 <span data-ttu-id="cef7f-116">O exemplo de código a seguir mostra uma classe que define um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="cef7f-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="cef7f-117">Os métodos que têm o <xref:System.ServiceModel.OperationContractAttribute> classe aplicada usam um padrão de mensagem de solicitação-resposta por padrão.</span><span class="sxs-lookup"><span data-stu-id="cef7f-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="cef7f-118">Para obter mais informações sobre esse padrão de mensagem, consulte [como: criar um contrato de solicitação-resposta](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="cef7f-118">For more information about this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="cef7f-119">Você também pode criar e usar outros padrões de mensagem definindo propriedades do atributo.</span><span class="sxs-lookup"><span data-stu-id="cef7f-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="cef7f-120">Para obter mais exemplos, consulte [como: criar um contrato unidirecional](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) e [como: criar um contrato Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="cef7f-120">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cef7f-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cef7f-121">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
