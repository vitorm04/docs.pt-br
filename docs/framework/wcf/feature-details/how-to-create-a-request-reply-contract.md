---
title: Como criar um contrato de resposta/solicitação
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 793f7214f8319e87c3e344990577841fc029bc55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185023"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="63d89-102">Como criar um contrato de resposta/solicitação</span><span class="sxs-lookup"><span data-stu-id="63d89-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="63d89-103">Um contrato de solicitação e resposta especifica um método que retorna uma resposta.</span><span class="sxs-lookup"><span data-stu-id="63d89-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="63d89-104">A resposta deve ser enviada e correlacionada à solicitação nos termos deste contrato.</span><span class="sxs-lookup"><span data-stu-id="63d89-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="63d89-105">Mesmo que o método`void` não retorne nenhuma `Sub` resposta (em C#, ou a in Visual Basic), a infra-estrutura cria e envia uma mensagem vazia para o chamador.</span><span class="sxs-lookup"><span data-stu-id="63d89-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="63d89-106">Para evitar o envio de uma mensagem de resposta vazia, use um contrato de mão única para a operação.</span><span class="sxs-lookup"><span data-stu-id="63d89-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="63d89-107">Para criar um contrato de solicitação e resposta</span><span class="sxs-lookup"><span data-stu-id="63d89-107">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="63d89-108">Crie uma interface na linguagem de programação de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="63d89-108">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="63d89-109">Aplique <xref:System.ServiceModel.ServiceContractAttribute> o atributo na interface.</span><span class="sxs-lookup"><span data-stu-id="63d89-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="63d89-110">Aplique <xref:System.ServiceModel.OperationContractAttribute> o atributo a cada método que os clientes podem invocar.</span><span class="sxs-lookup"><span data-stu-id="63d89-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="63d89-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="63d89-111">Optional.</span></span> <span data-ttu-id="63d89-112">Defina o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> valor `true` da propriedade para evitar o envio de uma mensagem de resposta vazia.</span><span class="sxs-lookup"><span data-stu-id="63d89-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="63d89-113">Por padrão, todas as operações são contratos de solicitação e resposta.</span><span class="sxs-lookup"><span data-stu-id="63d89-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63d89-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="63d89-114">Example</span></span>  
 <span data-ttu-id="63d89-115">A amostra a seguir define um contrato `Add` para `Subtract` um serviço de calculadora que fornece e métodos.</span><span class="sxs-lookup"><span data-stu-id="63d89-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="63d89-116">O `Multiply` método não faz parte do contrato porque <xref:System.ServiceModel.OperationContractAttribute> não é marcado pela classe e por isso não é acessível aos clientes.</span><span class="sxs-lookup"><span data-stu-id="63d89-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
```csharp
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);

    [OperationContract]
    int Subtract(int a, int b);

    int Multiply(int a, int b)
}
```
  
- <span data-ttu-id="63d89-117">Para obter mais informações sobre como <xref:System.ServiceModel.OperationContractAttribute> especificar <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> contratos de operação, consulte a classe e o imóvel.</span><span class="sxs-lookup"><span data-stu-id="63d89-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
- <span data-ttu-id="63d89-118">A aplicação <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> e atributos faz com que a geração automática de definições de contrato de serviço em um documento WSDL (Web Services Description Language, linguagem de descrição de serviços da Web) uma vez que o serviço seja implantado.</span><span class="sxs-lookup"><span data-stu-id="63d89-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="63d89-119">O documento é baixado `?wsdl` anexando-se ao endereço base HTTP para o serviço.</span><span class="sxs-lookup"><span data-stu-id="63d89-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="63d89-120">Por exemplo, `http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="63d89-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d89-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="63d89-121">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="63d89-122">Criando contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="63d89-122">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
- [<span data-ttu-id="63d89-123">Como criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="63d89-123">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
