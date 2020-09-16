---
title: 'Ponto de extremidade: chamadas com falha por segundo'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 97e887bd04cd7a755ce38914ace6de39ac871687
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545710"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="ef526-102">Ponto de extremidade: chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="ef526-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="ef526-103">Nome do contador: chamadas com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="ef526-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ef526-104">Description</span><span class="sxs-lookup"><span data-stu-id="ef526-104">Description</span></span>  
 <span data-ttu-id="ef526-105">Número de chamadas que têm exceções sem tratamento e são recebidas por esse ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="ef526-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="ef526-106">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="ef526-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ef526-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="ef526-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="ef526-108">Esse contador é incrementado toda vez que há uma exceção sem tratamento neste ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ef526-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef526-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="ef526-109">See also</span></span>

- [<span data-ttu-id="ef526-110">Especificando e lidando com falhas em contratos e serviços</span><span class="sxs-lookup"><span data-stu-id="ef526-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
