---
title: 'Ponto de extremidade: chamadas por segundo'
ms.date: 03/30/2017
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
ms.openlocfilehash: a70df63f6fd268abdd2e1799d1aa38afb41e2811
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43804611"
---
# <a name="endpoint-calls-per-second"></a><span data-ttu-id="4dd29-102">Ponto de extremidade: chamadas por segundo</span><span class="sxs-lookup"><span data-stu-id="4dd29-102">Endpoint: Calls Per Second</span></span>
<span data-ttu-id="4dd29-103">Nome do contador: Chamadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="4dd29-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4dd29-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="4dd29-104">Description</span></span>  
 <span data-ttu-id="4dd29-105">Número de chamadas para esse ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="4dd29-105">Number of calls to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="4dd29-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="4dd29-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="4dd29-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="4dd29-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
