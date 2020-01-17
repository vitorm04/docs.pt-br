---
title: 'Ponto de extremidade: chamadas por segundo'
ms.date: 03/30/2017
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
ms.openlocfilehash: d639d881bcedd336c7bbabd28ec385f60ff54d43
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163781"
---
# <a name="endpoint-calls-per-second"></a><span data-ttu-id="62757-102">Ponto de extremidade: chamadas por segundo</span><span class="sxs-lookup"><span data-stu-id="62757-102">Endpoint: Calls Per Second</span></span>
<span data-ttu-id="62757-103">Nome do contador: chamadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="62757-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="62757-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="62757-104">Description</span></span>  
 <span data-ttu-id="62757-105">Número de chamadas para esse ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="62757-105">Number of calls to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="62757-106">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="62757-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="62757-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="62757-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
