---
title: Instâncias
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 1b2801b5df3a5d2ca6d7fd03299ecdf4b7df426a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520250"
---
# <a name="instances"></a><span data-ttu-id="fa5b7-102">Instâncias</span><span class="sxs-lookup"><span data-stu-id="fa5b7-102">Instances</span></span>
<span data-ttu-id="fa5b7-103">Nome do contador: instâncias.</span><span class="sxs-lookup"><span data-stu-id="fa5b7-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fa5b7-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa5b7-104">Description</span></span>  
 <span data-ttu-id="fa5b7-105">Número de contextos de instância que o serviço contém no momento.</span><span class="sxs-lookup"><span data-stu-id="fa5b7-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="fa5b7-106">Na maioria das vezes, o número de contextos de instância é idêntico ao número de instâncias.</span><span class="sxs-lookup"><span data-stu-id="fa5b7-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="fa5b7-107">No entanto, os seguintes cenários são a exceção a essa regra.</span><span class="sxs-lookup"><span data-stu-id="fa5b7-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="fa5b7-108">Chama um método de serviço a <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> método explicitamente.</span><span class="sxs-lookup"><span data-stu-id="fa5b7-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="fa5b7-109">Um <xref:System.ServiceModel.ReleaseInstanceMode> é aplicado a um <xref:System.ServiceModel.OperationBehaviorAttribute> instância.</span><span class="sxs-lookup"><span data-stu-id="fa5b7-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa5b7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa5b7-110">See also</span></span>
- <xref:System.ServiceModel.OperationBehaviorAttribute>
