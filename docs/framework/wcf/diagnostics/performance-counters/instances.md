---
title: "Instâncias"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23182f18f28cfb843c1c3a70996590a92d9cdea8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="instances"></a><span data-ttu-id="94473-102">Instâncias</span><span class="sxs-lookup"><span data-stu-id="94473-102">Instances</span></span>
<span data-ttu-id="94473-103">Nome do contador: instâncias.</span><span class="sxs-lookup"><span data-stu-id="94473-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="94473-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="94473-104">Description</span></span>  
 <span data-ttu-id="94473-105">Número de contextos de instância que contém o serviço.</span><span class="sxs-lookup"><span data-stu-id="94473-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="94473-106">Na maioria das vezes, o número de contextos de instância é idêntico ao número de instâncias.</span><span class="sxs-lookup"><span data-stu-id="94473-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="94473-107">No entanto, os cenários a seguir são a exceção a essa regra.</span><span class="sxs-lookup"><span data-stu-id="94473-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="94473-108">Chama um método de serviço a <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> método explicitamente.</span><span class="sxs-lookup"><span data-stu-id="94473-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="94473-109">Um <xref:System.ServiceModel.ReleaseInstanceMode> é aplicado a um <xref:System.ServiceModel.OperationBehaviorAttribute> instância.</span><span class="sxs-lookup"><span data-stu-id="94473-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94473-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94473-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
