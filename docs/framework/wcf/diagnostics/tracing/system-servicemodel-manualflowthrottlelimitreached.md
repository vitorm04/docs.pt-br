---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35f149423fc8c0cd2a25834742d7c8b79ad8d8c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="e2388-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="e2388-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="e2388-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="e2388-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="e2388-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2388-104">Description</span></span>  
 <span data-ttu-id="e2388-105">O sistema atingiu o limite definido para o Acelerador de ManualFlowControlLimit.</span><span class="sxs-lookup"><span data-stu-id="e2388-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="e2388-106">O valor do acelerador pode ser alterado modificando a propriedade ManualFlowControlLimit no ServiceHost ou InstanceContext, conforme aplicável.</span><span class="sxs-lookup"><span data-stu-id="e2388-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="e2388-107">Este rastreamento é emitido quando o limite de controle de fluxo manual inicialmente é reduzido a 0.</span><span class="sxs-lookup"><span data-stu-id="e2388-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="e2388-108">As alterações subsequentes a 0 não são rastreadas.</span><span class="sxs-lookup"><span data-stu-id="e2388-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="e2388-109">Limite de controle de fluxo no contexto de instância é rastreada uma vez para cada contexto.</span><span class="sxs-lookup"><span data-stu-id="e2388-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2388-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2388-110">See Also</span></span>  
 [<span data-ttu-id="e2388-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="e2388-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e2388-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="e2388-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e2388-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="e2388-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
