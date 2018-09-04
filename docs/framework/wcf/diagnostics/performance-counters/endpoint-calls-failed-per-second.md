---
title: 'Ponto de extremidade: chamadas com falha por segundo'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: fa4fc1d8a875557f1da9e54e7a05eb012e7c221c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43531791"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="62ea4-102">Ponto de extremidade: chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="62ea4-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="62ea4-103">Nome do contador: Chamadas com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="62ea4-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="62ea4-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="62ea4-104">Description</span></span>  
 <span data-ttu-id="62ea4-105">Número de chamadas que têm exceções sem tratamento e são recebidas por este ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="62ea4-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="62ea4-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="62ea4-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="62ea4-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="62ea4-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="62ea4-108">Esse contador é incrementado sempre que houver uma exceção sem tratamento nesse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="62ea4-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ea4-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62ea4-109">See Also</span></span>  
 [<span data-ttu-id="62ea4-110">Especificando e lidando com falhas em contratos e serviços</span><span class="sxs-lookup"><span data-stu-id="62ea4-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
