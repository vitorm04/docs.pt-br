---
title: Instâncias
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 668cfb3026b9ab7259665f5e53873a512b1e2238
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975579"
---
# <a name="instances"></a><span data-ttu-id="c6279-102">Instâncias</span><span class="sxs-lookup"><span data-stu-id="c6279-102">Instances</span></span>
<span data-ttu-id="c6279-103">Nome do contador: instâncias.</span><span class="sxs-lookup"><span data-stu-id="c6279-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c6279-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6279-104">Description</span></span>  
 <span data-ttu-id="c6279-105">Número de contextos de instância que o serviço contém no momento.</span><span class="sxs-lookup"><span data-stu-id="c6279-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="c6279-106">Na maioria das vezes, o número de contextos de instância é idêntico ao número de instâncias.</span><span class="sxs-lookup"><span data-stu-id="c6279-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="c6279-107">No entanto, os seguintes cenários são a exceção a essa regra.</span><span class="sxs-lookup"><span data-stu-id="c6279-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="c6279-108">Chama um método de serviço a <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> método explicitamente.</span><span class="sxs-lookup"><span data-stu-id="c6279-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="c6279-109">Um <xref:System.ServiceModel.ReleaseInstanceMode> é aplicado a um <xref:System.ServiceModel.OperationBehaviorAttribute> instância.</span><span class="sxs-lookup"><span data-stu-id="c6279-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6279-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6279-110">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
