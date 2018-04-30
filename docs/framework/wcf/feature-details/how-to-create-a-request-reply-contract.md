---
title: Como criar um contrato de resposta/solicitação
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a272eaa88a53814daea9d515550a37f7991ecb8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="fe895-102">Como criar um contrato de resposta/solicitação</span><span class="sxs-lookup"><span data-stu-id="fe895-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="fe895-103">Um contrato de solicitação-resposta especifica um método que retorna uma resposta.</span><span class="sxs-lookup"><span data-stu-id="fe895-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="fe895-104">A resposta deve ser enviada e correlacionada a solicitação de acordo com os termos deste contrato.</span><span class="sxs-lookup"><span data-stu-id="fe895-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="fe895-105">Mesmo se o método não retornar nenhuma resposta (`void` em c#, ou um `Sub` no Visual Basic), a infraestrutura cria e envia uma mensagem vazia para o chamador.</span><span class="sxs-lookup"><span data-stu-id="fe895-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="fe895-106">Para evitar o envio de uma mensagem de resposta vazia, use um contrato unidirecional para a operação.</span><span class="sxs-lookup"><span data-stu-id="fe895-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="fe895-107">Para criar um contrato de solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="fe895-107">To create a request-reply contract</span></span>  
  
1.  <span data-ttu-id="fe895-108">Crie uma interface na linguagem de programação de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="fe895-108">Create an interface in the programming language of your choice.</span></span>  
  
2.  <span data-ttu-id="fe895-109">Aplicar o <xref:System.ServiceModel.ServiceContractAttribute> de atributo para a interface.</span><span class="sxs-lookup"><span data-stu-id="fe895-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3.  <span data-ttu-id="fe895-110">Aplicar o <xref:System.ServiceModel.OperationContractAttribute> de atributo para cada método que os clientes podem chamar.</span><span class="sxs-lookup"><span data-stu-id="fe895-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4.  <span data-ttu-id="fe895-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="fe895-111">Optional.</span></span> <span data-ttu-id="fe895-112">Defina o valor da <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade `true` para evitar o envio de uma mensagem de resposta vazia.</span><span class="sxs-lookup"><span data-stu-id="fe895-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="fe895-113">Por padrão, todas as operações são contratos de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="fe895-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe895-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fe895-114">Example</span></span>  
 <span data-ttu-id="fe895-115">O exemplo a seguir define um contrato para um serviço de cálculo que fornece `Add` e `Subtract` métodos.</span><span class="sxs-lookup"><span data-stu-id="fe895-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="fe895-116">O `Multiply` método não faz parte do contrato porque ele não está marcado pelo <xref:System.ServiceModel.OperationContractAttribute> de classe e não está acessível aos clientes.</span><span class="sxs-lookup"><span data-stu-id="fe895-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
```
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
  
-   <span data-ttu-id="fe895-117">Para obter mais informações sobre como especificar contratos de operação, consulte o <xref:System.ServiceModel.OperationContractAttribute> classe e o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="fe895-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
-   <span data-ttu-id="fe895-118">Aplicar o <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> atributos faz com que a geração automática de definições de contrato de serviço em um documento WSDL Web Services Description Language () quando o serviço é implantado.</span><span class="sxs-lookup"><span data-stu-id="fe895-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="fe895-119">O documento é baixado, acrescentando `?wsdl` para HTTP endereço para o serviço de base.</span><span class="sxs-lookup"><span data-stu-id="fe895-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="fe895-120">Por exemplo, `http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="fe895-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe895-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe895-121">See Also</span></span>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="fe895-122">Criando contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="fe895-122">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [<span data-ttu-id="fe895-123">Como criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="fe895-123">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
