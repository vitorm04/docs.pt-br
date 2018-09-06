---
title: 'Serviços: chamadas com falha por segundo'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 9cd649788e1304c68caa1bbf4b5fd27e6fc9d508
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861810"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="d2699-102">Serviços: chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="d2699-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="d2699-103">Nome do contador: Chamadas com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="d2699-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d2699-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2699-104">Description</span></span>  
 <span data-ttu-id="d2699-105">Número de chamadas que têm exceções sem tratamento e recebidos por esse serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="d2699-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="d2699-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="d2699-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d2699-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="d2699-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="d2699-108">No código gerenciado, as exceções são geradas quando ocorrem condições de erro.</span><span class="sxs-lookup"><span data-stu-id="d2699-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="d2699-109">No código gerenciado, as exceções são geradas quando ocorrem condições de erro.</span><span class="sxs-lookup"><span data-stu-id="d2699-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="d2699-110">Esse contador é incrementado sempre que houver uma exceção não tratada neste serviço.</span><span class="sxs-lookup"><span data-stu-id="d2699-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2699-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2699-111">See Also</span></span>  
 [<span data-ttu-id="d2699-112">Especificando e lidando com falhas em contratos e serviços</span><span class="sxs-lookup"><span data-stu-id="d2699-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
