---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: 86d47ab0a83ff3e4a68bfa8ccf1349cf2b345b23
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597730"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="96fec-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="96fec-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="96fec-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="96fec-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="96fec-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="96fec-104">Description</span></span>  
 <span data-ttu-id="96fec-105">O sistema atingiu o limite definido para o Acelerador de ManualFlowControlLimit.</span><span class="sxs-lookup"><span data-stu-id="96fec-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="96fec-106">O valor de restrição pode ser alterado modificando a propriedade ManualFlowControlLimit no ServiceHost ou InstanceContext, conforme aplicável.</span><span class="sxs-lookup"><span data-stu-id="96fec-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="96fec-107">Esse rastreamento é emitido quando o limite de controle de fluxo manual inicialmente é reduzido a 0.</span><span class="sxs-lookup"><span data-stu-id="96fec-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="96fec-108">As alterações subsequentes 0 não são rastreadas.</span><span class="sxs-lookup"><span data-stu-id="96fec-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="96fec-109">Limite de controle de fluxo no contexto de instância é rastreada de uma vez para cada contexto.</span><span class="sxs-lookup"><span data-stu-id="96fec-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96fec-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96fec-110">See also</span></span>
- [<span data-ttu-id="96fec-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="96fec-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="96fec-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="96fec-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="96fec-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="96fec-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
