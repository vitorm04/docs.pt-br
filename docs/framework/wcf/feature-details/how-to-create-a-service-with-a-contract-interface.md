---
title: 'Como: criar um serviço com interface de contrato'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 0aa5429d771aeda0b392b89ec4cc1a07de30973f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298529"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="16c28-102">Como: criar um serviço com interface de contrato</span><span class="sxs-lookup"><span data-stu-id="16c28-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="16c28-103">É a maneira preferencial para criar um contrato do Windows Communication Foundation (WCF) usando uma interface.</span><span class="sxs-lookup"><span data-stu-id="16c28-103">The preferred way to create a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="16c28-104">Esse contrato especifica a coleção e a estrutura de mensagens necessária para acessar as operações de ofertas de serviço.</span><span class="sxs-lookup"><span data-stu-id="16c28-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="16c28-105">Essa interface define os tipos de entrada e saídos, aplicando o <xref:System.ServiceModel.ServiceContractAttribute> classe para a interface e o <xref:System.ServiceModel.OperationContractAttribute> classe para os métodos que você deseja expor.</span><span class="sxs-lookup"><span data-stu-id="16c28-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 <span data-ttu-id="16c28-106">Para obter mais informações sobre contratos de serviço, consulte [Criando contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="16c28-106">For more information about service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="16c28-107">Criando um contrato WCF com uma interface</span><span class="sxs-lookup"><span data-stu-id="16c28-107">Creating a WCF contract with an interface</span></span>  
  
1. <span data-ttu-id="16c28-108">Criar uma nova interface usando o Visual Basic, C#, ou qualquer outra linguagem do tempo de execução de linguagem comum.</span><span class="sxs-lookup"><span data-stu-id="16c28-108">Create a new interface using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="16c28-109">Aplique a classe <xref:System.ServiceModel.ServiceContractAttribute> à interface.</span><span class="sxs-lookup"><span data-stu-id="16c28-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3. <span data-ttu-id="16c28-110">Defina os métodos na interface.</span><span class="sxs-lookup"><span data-stu-id="16c28-110">Define the methods in the interface.</span></span>  
  
4. <span data-ttu-id="16c28-111">Aplicar o <xref:System.ServiceModel.OperationContractAttribute> classe para cada método que deve ser exposto como parte do contrato de WCF público.</span><span class="sxs-lookup"><span data-stu-id="16c28-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16c28-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16c28-112">Example</span></span>  
 <span data-ttu-id="16c28-113">O exemplo de código a seguir mostra uma interface que define um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="16c28-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="16c28-114">Os métodos que têm o <xref:System.ServiceModel.OperationContractAttribute> classe aplicada usam um padrão de mensagem de solicitação-resposta por padrão.</span><span class="sxs-lookup"><span data-stu-id="16c28-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="16c28-115">Para obter mais informações sobre esse padrão de mensagem, consulte [como: Criar um contrato de solicitação-resposta](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="16c28-115">For more information about this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="16c28-116">Você também pode criar e usar outros padrões de mensagens, definindo propriedades do atributo.</span><span class="sxs-lookup"><span data-stu-id="16c28-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="16c28-117">Para ver mais exemplos, confira [Como: Criar um contrato unidirecional](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) e [como: Criar um contrato Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="16c28-117">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c28-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16c28-118">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
