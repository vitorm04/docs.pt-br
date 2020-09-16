---
title: 'Serviços: chamadas com falha por segundo'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 5629c55cba6f21de24a1de7e8d38a9c08fcf4fb1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559103"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="8de6b-102">Serviços: chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="8de6b-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="8de6b-103">Nome do contador: chamadas com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="8de6b-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8de6b-104">Description</span><span class="sxs-lookup"><span data-stu-id="8de6b-104">Description</span></span>  
 <span data-ttu-id="8de6b-105">Número de chamadas que têm exceções sem tratamento e são recebidas por esse serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="8de6b-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="8de6b-106">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="8de6b-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="8de6b-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="8de6b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="8de6b-108">No código gerenciado, as exceções são geradas quando ocorrem condições de erro.</span><span class="sxs-lookup"><span data-stu-id="8de6b-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="8de6b-109">No código gerenciado, as exceções são geradas quando ocorrem condições de erro.</span><span class="sxs-lookup"><span data-stu-id="8de6b-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="8de6b-110">Esse contador é incrementado toda vez que há uma exceção sem tratamento nesse serviço.</span><span class="sxs-lookup"><span data-stu-id="8de6b-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de6b-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="8de6b-111">See also</span></span>

- [<span data-ttu-id="8de6b-112">Especificando e lidando com falhas em contratos e serviços</span><span class="sxs-lookup"><span data-stu-id="8de6b-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
