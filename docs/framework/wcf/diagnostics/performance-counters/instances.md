---
title: Instâncias
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: a95acf8e775e0802dc0ed781c562fa6373995a70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473036"
---
# <a name="instances"></a><span data-ttu-id="7c814-102">Instâncias</span><span class="sxs-lookup"><span data-stu-id="7c814-102">Instances</span></span>
<span data-ttu-id="7c814-103">Nome do contador: instâncias.</span><span class="sxs-lookup"><span data-stu-id="7c814-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7c814-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c814-104">Description</span></span>  
 <span data-ttu-id="7c814-105">Número de contextos de instância que contém o serviço.</span><span class="sxs-lookup"><span data-stu-id="7c814-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="7c814-106">Na maioria das vezes, o número de contextos de instância é idêntico ao número de instâncias.</span><span class="sxs-lookup"><span data-stu-id="7c814-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="7c814-107">No entanto, os cenários a seguir são a exceção a essa regra.</span><span class="sxs-lookup"><span data-stu-id="7c814-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="7c814-108">Chama um método de serviço a <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> método explicitamente.</span><span class="sxs-lookup"><span data-stu-id="7c814-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="7c814-109">Um <xref:System.ServiceModel.ReleaseInstanceMode> é aplicado a um <xref:System.ServiceModel.OperationBehaviorAttribute> instância.</span><span class="sxs-lookup"><span data-stu-id="7c814-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c814-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c814-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
