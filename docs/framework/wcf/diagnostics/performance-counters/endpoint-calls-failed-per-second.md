---
title: 'Ponto de extremidade: Chamadas com falha por segundo'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 03fbdd83246fa811424f445823f705a3bef5697a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608031"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="cd956-102">Ponto de extremidade: Chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="cd956-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="cd956-103">Nome do contador: Chamadas com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="cd956-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cd956-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd956-104">Description</span></span>  
 <span data-ttu-id="cd956-105">Número de chamadas que têm exceções sem tratamento e são recebidas por este ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="cd956-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="cd956-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="cd956-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="cd956-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="cd956-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="cd956-108">Esse contador é incrementado sempre que houver uma exceção sem tratamento nesse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="cd956-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd956-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd956-109">See also</span></span>
- [<span data-ttu-id="cd956-110">Especificando e lidando com falhas em contratos e serviços</span><span class="sxs-lookup"><span data-stu-id="cd956-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
