---
title: "Como criar um serviço com interface de contrato"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 750c3d3371970d93872fd4e4e0814913a408187a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="a9984-102">Como criar um serviço com interface de contrato</span><span class="sxs-lookup"><span data-stu-id="a9984-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="a9984-103">A melhor maneira de criar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contrato é usando uma interface.</span><span class="sxs-lookup"><span data-stu-id="a9984-103">The preferred way to create a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contract is by using an interface.</span></span> <span data-ttu-id="a9984-104">Esse contrato especifica a coleta e a estrutura de mensagens necessária para acessar as operações de ofertas de serviço.</span><span class="sxs-lookup"><span data-stu-id="a9984-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="a9984-105">Essa interface define os tipos de entrada e saídos aplicando o <xref:System.ServiceModel.ServiceContractAttribute> classe para a interface e o <xref:System.ServiceModel.OperationContractAttribute> classe para os métodos que você deseja expor.</span><span class="sxs-lookup"><span data-stu-id="a9984-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a9984-106">contratos de serviço, consulte [criar contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a9984-106"> service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="a9984-107">Criando um contrato WCF com uma interface</span><span class="sxs-lookup"><span data-stu-id="a9984-107">Creating a WCF contract with an interface</span></span>  
  
1.  <span data-ttu-id="a9984-108">Criar uma nova interface usando [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], c# ou qualquer outra linguagem common language runtime.</span><span class="sxs-lookup"><span data-stu-id="a9984-108">Create a new interface using [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="a9984-109">Aplique a classe <xref:System.ServiceModel.ServiceContractAttribute> à interface.</span><span class="sxs-lookup"><span data-stu-id="a9984-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3.  <span data-ttu-id="a9984-110">Defina os métodos na interface.</span><span class="sxs-lookup"><span data-stu-id="a9984-110">Define the methods in the interface.</span></span>  
  
4.  <span data-ttu-id="a9984-111">Aplicar o <xref:System.ServiceModel.OperationContractAttribute> classe para cada método que deve ser exposto como parte do público [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contrato.</span><span class="sxs-lookup"><span data-stu-id="a9984-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9984-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a9984-112">Example</span></span>  
 <span data-ttu-id="a9984-113">O exemplo de código a seguir mostra uma interface que define um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="a9984-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="a9984-114">Os métodos que têm o <xref:System.ServiceModel.OperationContractAttribute> classe aplicada usam um padrão de mensagem de solicitação-resposta por padrão.</span><span class="sxs-lookup"><span data-stu-id="a9984-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a9984-115">Esse padrão de mensagem, consulte [como: criar um contrato de solicitação-resposta](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a9984-115"> this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="a9984-116">Você também pode criar e usar outros padrões de mensagem definindo propriedades do atributo.</span><span class="sxs-lookup"><span data-stu-id="a9984-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="a9984-117">Para obter mais exemplos, consulte [como: criar um contrato unidirecional](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) e [como: criar um contrato Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a9984-117">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9984-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9984-118">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
