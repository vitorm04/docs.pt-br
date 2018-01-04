---
title: "Serviços de resposta por solicitação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9e8c01fa3451cbeb335c4771e287566af1c104b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="request-reply-services"></a><span data-ttu-id="d7c90-102">Serviços de resposta por solicitação</span><span class="sxs-lookup"><span data-stu-id="d7c90-102">Request-Reply Services</span></span>
<span data-ttu-id="d7c90-103">Serviços de solicitação-resposta são o tipo de padrão de contrato de operação em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7c90-103">Request-reply services are the default type of operation contract in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="d7c90-104">Os clientes fazer chamadas para operações de serviço e aguardar uma resposta do serviço.</span><span class="sxs-lookup"><span data-stu-id="d7c90-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="d7c90-105">Você pode realizar chamadas para uma operação de serviço ou sincronicamente, onde o cliente bloqueia até ele recebe uma resposta do serviço ou os tempos de chamada ou de forma assíncrona, em que o cliente faz uma chamada para a operação de serviço, continua a trabalhar e recebe o resposta do serviço em outro thread.</span><span class="sxs-lookup"><span data-stu-id="d7c90-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="d7c90-106">Para criar um contrato de serviço de solicitação-resposta, definir o contrato de serviço e aplicar o <xref:System.ServiceModel.OperationContractAttribute> de classe para cada operação, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d7c90-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="d7c90-107">Você não precisa definir o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade `false` porque esse é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="d7c90-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c90-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7c90-108">See Also</span></span>  
 [<span data-ttu-id="d7c90-109">Serviços unidirecionais</span><span class="sxs-lookup"><span data-stu-id="d7c90-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)  
 [<span data-ttu-id="d7c90-110">Serviços duplex</span><span class="sxs-lookup"><span data-stu-id="d7c90-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
