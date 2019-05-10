---
title: Instâncias
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: e0be9c93b5efe17235dbccd426cdd73fbb739361
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651843"
---
# <a name="instances"></a><span data-ttu-id="a807a-102">Instâncias</span><span class="sxs-lookup"><span data-stu-id="a807a-102">Instances</span></span>
<span data-ttu-id="a807a-103">Nome do contador: instâncias.</span><span class="sxs-lookup"><span data-stu-id="a807a-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a807a-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="a807a-104">Description</span></span>  
 <span data-ttu-id="a807a-105">Número de contextos de instância que o serviço contém no momento.</span><span class="sxs-lookup"><span data-stu-id="a807a-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="a807a-106">Na maioria das vezes, o número de contextos de instância é idêntico ao número de instâncias.</span><span class="sxs-lookup"><span data-stu-id="a807a-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="a807a-107">No entanto, os seguintes cenários são a exceção a essa regra.</span><span class="sxs-lookup"><span data-stu-id="a807a-107">However, the following scenarios are exception to this rule.</span></span>  
  
- <span data-ttu-id="a807a-108">Chama um método de serviço a <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> método explicitamente.</span><span class="sxs-lookup"><span data-stu-id="a807a-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
- <span data-ttu-id="a807a-109">Um <xref:System.ServiceModel.ReleaseInstanceMode> é aplicado a um <xref:System.ServiceModel.OperationBehaviorAttribute> instância.</span><span class="sxs-lookup"><span data-stu-id="a807a-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a807a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a807a-110">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
