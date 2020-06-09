---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: bffa6361df5a50748f45aa3004f7a307ad516d7b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84580483"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="dbae8-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="dbae8-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="dbae8-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="dbae8-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="dbae8-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbae8-104">Description</span></span>  
 <span data-ttu-id="dbae8-105">O sistema atingiu o limite definido para a limitação de ManualFlowControlLimit.</span><span class="sxs-lookup"><span data-stu-id="dbae8-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="dbae8-106">O valor de restrição pode ser alterado modificando a propriedade ManualFlowControlLimit no ServiceHost ou InstanceContext, conforme aplicável.</span><span class="sxs-lookup"><span data-stu-id="dbae8-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="dbae8-107">Esse rastreamento é emitido quando o limite de controle de fluxo manual é reduzido inicialmente para 0.</span><span class="sxs-lookup"><span data-stu-id="dbae8-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="dbae8-108">Alterações subsequentes em 0 não são rastreadas.</span><span class="sxs-lookup"><span data-stu-id="dbae8-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="dbae8-109">O limite de controle de fluxo no contexto de instância é rastreado uma vez para cada contexto.</span><span class="sxs-lookup"><span data-stu-id="dbae8-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbae8-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbae8-110">See also</span></span>

- [<span data-ttu-id="dbae8-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="dbae8-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="dbae8-112">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="dbae8-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="dbae8-113">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="dbae8-113">Administration and Diagnostics</span></span>](../index.md)
