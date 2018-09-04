---
title: Operações Transacionadas Confirmadas por Segundo
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 124eae3b36a731ac50a147782b19c87e3adfa7be
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564005"
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="f389f-102">Operações Transacionadas Confirmadas por Segundo</span><span class="sxs-lookup"><span data-stu-id="f389f-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="f389f-103">Nome do contador: Operações transacionadas confirmadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="f389f-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f389f-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="f389f-104">Description</span></span>  
 <span data-ttu-id="f389f-105">Número de operações transacionais que foram confirmadas neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="f389f-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="f389f-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="f389f-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f389f-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="f389f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
