---
title: Operações Transacionadas Confirmadas por Segundo
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 047640e9b5cc22f2d443832fb7bd5afd47aef5be
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550632"
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="6cf3c-102">Operações Transacionadas Confirmadas por Segundo</span><span class="sxs-lookup"><span data-stu-id="6cf3c-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="6cf3c-103">Nome do contador: operações transacionadas confirmadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="6cf3c-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6cf3c-104">Description</span><span class="sxs-lookup"><span data-stu-id="6cf3c-104">Description</span></span>  
 <span data-ttu-id="6cf3c-105">Número de operações transacionais que foram confirmadas neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="6cf3c-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="6cf3c-106">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="6cf3c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="6cf3c-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="6cf3c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
