---
title: Como criar um contrato do Windows Communication Foundation com uma classe
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 0be2400ef3da5f0bbc218032ecd69af23f82cabd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597131"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="f342c-102">Como criar um contrato do Windows Communication Foundation com uma classe</span><span class="sxs-lookup"><span data-stu-id="f342c-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="f342c-103">A maneira preferida de criar um contrato de Windows Communication Foundation (WCF) é usando uma interface.</span><span class="sxs-lookup"><span data-stu-id="f342c-103">The preferred way of creating a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="f342c-104">Para obter mais informações, consulte [como: definir um contrato de serviço](../how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="f342c-104">For more information, see [How to: Define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="f342c-105">Uma alternativa, descrita aqui, é criar uma classe e, em seguida, aplicar o <xref:System.ServiceModel.ServiceContractAttribute> atributo à classe diretamente e o <xref:System.ServiceModel.OperationContractAttribute> atributo a cada um dos métodos na classe que fazem parte do contrato.</span><span class="sxs-lookup"><span data-stu-id="f342c-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="f342c-106">`[ServiceContract]`e `[ServiceContractAttribute]` fazer a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="f342c-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="f342c-107">A mesma coisa é verdadeira para `[OperationContract]` e `[OperationContractAttribute]` .</span><span class="sxs-lookup"><span data-stu-id="f342c-107">The same thing is true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="f342c-108">Em cada caso, a primeira é a abreviação do último.</span><span class="sxs-lookup"><span data-stu-id="f342c-108">In each case, the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="f342c-109">Para obter mais informações sobre contratos de serviço, consulte [Designing Service Contracts](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="f342c-109">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="f342c-110">Criando um contrato de Windows Communication Foundation com uma classe</span><span class="sxs-lookup"><span data-stu-id="f342c-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1. <span data-ttu-id="f342c-111">Crie uma nova classe usando Visual Basic, C# ou qualquer outra linguagem de Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="f342c-111">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="f342c-112">Aplique a <xref:System.ServiceModel.ServiceContractAttribute> classe à classe.</span><span class="sxs-lookup"><span data-stu-id="f342c-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3. <span data-ttu-id="f342c-113">Crie métodos na classe.</span><span class="sxs-lookup"><span data-stu-id="f342c-113">Create methods in the class.</span></span>  
  
4. <span data-ttu-id="f342c-114">Aplique a <xref:System.ServiceModel.OperationContractAttribute> classe a cada método que deve ser exposto como parte do contrato do WCF público.</span><span class="sxs-lookup"><span data-stu-id="f342c-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f342c-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f342c-115">Example</span></span>  
 <span data-ttu-id="f342c-116">O exemplo de código a seguir mostra uma classe que define um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="f342c-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="f342c-117">Por padrão, os métodos que têm a <xref:System.ServiceModel.OperationContractAttribute> classe aplicada usam um padrão de mensagem de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="f342c-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="f342c-118">Para obter mais informações sobre esse padrão de mensagem, consulte [como: criar um contrato de solicitação-resposta](how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="f342c-118">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="f342c-119">Você também pode criar e usar outros padrões de mensagem definindo as propriedades do atributo.</span><span class="sxs-lookup"><span data-stu-id="f342c-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="f342c-120">Para obter mais exemplos, consulte [como: criar um contrato unidirecional](how-to-create-a-one-way-contract.md) e [como criar um contrato duplex](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="f342c-120">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f342c-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="f342c-121">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
