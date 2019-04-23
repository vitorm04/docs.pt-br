---
title: Serviços de resposta por solicitação
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 1ff11b1cae4ec8f6fe886a55cb0add27831048d0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177808"
---
# <a name="request-reply-services"></a><span data-ttu-id="c0fde-102">Serviços de resposta por solicitação</span><span class="sxs-lookup"><span data-stu-id="c0fde-102">Request-Reply Services</span></span>
<span data-ttu-id="c0fde-103">Serviços de solicitação-resposta são o tipo de padrão de contrato de operação no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c0fde-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="c0fde-104">Os clientes fazem chamadas para operações de serviço e aguardam uma resposta do serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fde-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="c0fde-105">Você pode realizar chamadas para uma operação de serviço ou forma síncrona, em que o cliente bloqueia até que ele recebe uma resposta do serviço ou os tempos de chamada ou de forma assíncrona, em que o cliente faz uma chamada para a operação de serviço, continua a trabalhar e recebe o resposta do serviço em outro thread.</span><span class="sxs-lookup"><span data-stu-id="c0fde-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="c0fde-106">Para criar um contrato de serviço de solicitação-resposta, defina seu contrato de serviço e aplique o <xref:System.ServiceModel.OperationContractAttribute> de classe para cada operação, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c0fde-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="c0fde-107">Você não precisa definir as <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade para `false` porque esse é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="c0fde-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0fde-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0fde-108">See also</span></span>

- [<span data-ttu-id="c0fde-109">Serviços unidirecionais</span><span class="sxs-lookup"><span data-stu-id="c0fde-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [<span data-ttu-id="c0fde-110">Serviços duplex</span><span class="sxs-lookup"><span data-stu-id="c0fde-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
