---
title: 'Como: criar um contrato de resposta/solicitação'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 9954be556df13193c290a55616ad83ef07e0af7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141070"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="b9292-102">Como: criar um contrato de resposta/solicitação</span><span class="sxs-lookup"><span data-stu-id="b9292-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="b9292-103">Um contrato de solicitação-resposta especifica um método que retorna uma resposta.</span><span class="sxs-lookup"><span data-stu-id="b9292-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="b9292-104">A resposta deve ser enviada e correlacionada à solicitação de acordo com os termos deste contrato.</span><span class="sxs-lookup"><span data-stu-id="b9292-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="b9292-105">Mesmo que o método retorna sem resposta (`void` em c#, ou um `Sub` no Visual Basic), a infraestrutura cria e envia uma mensagem vazia ao chamador.</span><span class="sxs-lookup"><span data-stu-id="b9292-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="b9292-106">Para evitar o envio de uma mensagem de resposta vazia, use um contrato unidirecional para a operação.</span><span class="sxs-lookup"><span data-stu-id="b9292-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="b9292-107">Para criar um contrato de solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="b9292-107">To create a request-reply contract</span></span>  
  
1.  <span data-ttu-id="b9292-108">Crie uma interface na linguagem de programação de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="b9292-108">Create an interface in the programming language of your choice.</span></span>  
  
2.  <span data-ttu-id="b9292-109">Aplicar o <xref:System.ServiceModel.ServiceContractAttribute> à interface de atributo.</span><span class="sxs-lookup"><span data-stu-id="b9292-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3.  <span data-ttu-id="b9292-110">Aplicar o <xref:System.ServiceModel.OperationContractAttribute> de atributo para cada método que os clientes podem invocar.</span><span class="sxs-lookup"><span data-stu-id="b9292-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4.  <span data-ttu-id="b9292-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b9292-111">Optional.</span></span> <span data-ttu-id="b9292-112">Defina o valor da <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade para `true` para impedir o envio de uma mensagem de resposta vazia.</span><span class="sxs-lookup"><span data-stu-id="b9292-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="b9292-113">Por padrão, todas as operações são contratos de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="b9292-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9292-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b9292-114">Example</span></span>  
 <span data-ttu-id="b9292-115">O exemplo a seguir define um contrato para um serviço de calculadora fornece `Add` e `Subtract` métodos.</span><span class="sxs-lookup"><span data-stu-id="b9292-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="b9292-116">O `Multiply` método não é parte do contrato, porque ele não está marcado pelo <xref:System.ServiceModel.OperationContractAttribute> de classe e não está acessível aos clientes.</span><span class="sxs-lookup"><span data-stu-id="b9292-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
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
  
-   <span data-ttu-id="b9292-117">Para obter mais informações sobre como especificar contratos de operação, consulte o <xref:System.ServiceModel.OperationContractAttribute> classe e o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b9292-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
-   <span data-ttu-id="b9292-118">Aplicando o <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> atributos faz com que a geração automática de definições de contrato de serviço em um documento de descrição linguagem WSDL (Web Services) quando o serviço é implantado.</span><span class="sxs-lookup"><span data-stu-id="b9292-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="b9292-119">O documento é baixado por meio do acréscimo `?wsdl` endereço para o serviço de base para o HTTP.</span><span class="sxs-lookup"><span data-stu-id="b9292-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="b9292-120">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="b9292-120">For example,</span></span> `http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a><span data-ttu-id="b9292-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9292-121">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="b9292-122">Criando contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="b9292-122">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
- [<span data-ttu-id="b9292-123">Como: criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="b9292-123">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
