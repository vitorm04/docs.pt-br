---
title: Implementando contratos de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 766e0c4d30a4fa0eed9ce154ca932f5371a43211
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196314"
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="46157-102">Implementando contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="46157-102">Implementing Service Contracts</span></span>
<span data-ttu-id="46157-103">Um serviço é uma classe que expõe a funcionalidade disponível para clientes em um ou mais pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="46157-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="46157-104">Para criar um serviço, escreva uma classe que implementa um contrato do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="46157-104">To create a service, write a class that implements a Windows Communication Foundation (WCF) contract.</span></span> <span data-ttu-id="46157-105">Você pode fazer isso de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="46157-105">You can do this in one of two ways.</span></span> <span data-ttu-id="46157-106">Você pode definir o contrato separadamente como uma interface e, em seguida, crie uma classe que implementa essa interface.</span><span class="sxs-lookup"><span data-stu-id="46157-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="46157-107">Como alternativa, você pode criar o contrato e a classe diretamente, colocando o <xref:System.ServiceModel.ServiceContractAttribute> atributo na classe em si e o <xref:System.ServiceModel.OperationContractAttribute> atributo sobre os métodos disponíveis para os clientes do serviço.</span><span class="sxs-lookup"><span data-stu-id="46157-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="46157-108">Criando uma classe de serviço</span><span class="sxs-lookup"><span data-stu-id="46157-108">Creating a service class</span></span>  
 <span data-ttu-id="46157-109">A seguir está um exemplo de um serviço que implementa um `IMath` contrato que tenha sido definido separadamente.</span><span class="sxs-lookup"><span data-stu-id="46157-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="46157-110">Como alternativa, um serviço pode expor um contrato diretamente.</span><span class="sxs-lookup"><span data-stu-id="46157-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="46157-111">A seguir está um exemplo de uma classe de serviço que define e implementa um `MathService` contrato.</span><span class="sxs-lookup"><span data-stu-id="46157-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="46157-112">Observe que os serviços acima expõem contratos diferentes porque os nomes de contrato são diferentes.</span><span class="sxs-lookup"><span data-stu-id="46157-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="46157-113">No primeiro caso, o contrato exposto é denominado "`IMath`while" no segundo caso, o contrato é denominado"`MathService`".</span><span class="sxs-lookup"><span data-stu-id="46157-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="46157-114">Você pode definir algumas coisas no serviço e operação de níveis de implementação, bem como de instanciação e simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="46157-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> <span data-ttu-id="46157-115">Para obter mais informações, consulte [projetar e implementar serviços](../../../docs/framework/wcf/designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="46157-115">For more information, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="46157-116">Depois de implementar um contrato de serviço, você deve criar um ou mais pontos de extremidade para o serviço.</span><span class="sxs-lookup"><span data-stu-id="46157-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> <span data-ttu-id="46157-117">Para obter mais informações, consulte [visão geral de criação de ponto de extremidade](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="46157-117">For more information, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="46157-118">Para obter mais informações sobre como executar um serviço, consulte [serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="46157-118">For more information about how to run a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46157-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46157-119">See also</span></span>

- [<span data-ttu-id="46157-120">Serviços de design e implantação</span><span class="sxs-lookup"><span data-stu-id="46157-120">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="46157-121">Como: Criar um serviço com uma classe de contrato</span><span class="sxs-lookup"><span data-stu-id="46157-121">How to: Create a Service with a Contract Class</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [<span data-ttu-id="46157-122">Como: Criar um serviço com uma Interface de contrato</span><span class="sxs-lookup"><span data-stu-id="46157-122">How to: Create a Service with a Contract Interface</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [<span data-ttu-id="46157-123">Especificando o comportamento em tempo de execução do serviço</span><span class="sxs-lookup"><span data-stu-id="46157-123">Specifying Service Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
