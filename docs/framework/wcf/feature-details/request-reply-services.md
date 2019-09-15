---
title: Serviços de resposta por solicitação
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: f58da6f1cdaad1b976659ee2e9febe12cc07726f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991135"
---
# <a name="request-reply-services"></a><span data-ttu-id="e9ca1-102">Serviços de resposta por solicitação</span><span class="sxs-lookup"><span data-stu-id="e9ca1-102">Request-Reply Services</span></span>
<span data-ttu-id="e9ca1-103">Os serviços de solicitação-resposta são o tipo padrão de contrato de operação no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e9ca1-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="e9ca1-104">Os clientes fazem chamadas para operações de serviço e aguardam uma resposta do serviço.</span><span class="sxs-lookup"><span data-stu-id="e9ca1-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="e9ca1-105">Você pode executar chamadas para uma operação de serviço de forma síncrona, em que o cliente é bloqueado até receber uma resposta do serviço ou dos tempos de chamada, ou de forma assíncrona, em que o cliente faz uma chamada para a operação de serviço, continua trabalhando e recebe o resposta do serviço em outro thread.</span><span class="sxs-lookup"><span data-stu-id="e9ca1-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="e9ca1-106">Para criar um contrato de serviço de solicitação-resposta, defina seu contrato de serviço e <xref:System.ServiceModel.OperationContractAttribute> aplique a classe a cada operação, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e9ca1-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="e9ca1-107">Você não precisa definir a <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> Propriedade como `false` , pois esse é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="e9ca1-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9ca1-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9ca1-108">See also</span></span>

- [<span data-ttu-id="e9ca1-109">Serviços unidirecionais</span><span class="sxs-lookup"><span data-stu-id="e9ca1-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [<span data-ttu-id="e9ca1-110">Serviços duplex</span><span class="sxs-lookup"><span data-stu-id="e9ca1-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
