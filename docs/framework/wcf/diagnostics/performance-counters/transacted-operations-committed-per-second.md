---
title: Operações Transacionadas Confirmadas por Segundo
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 124eae3b36a731ac50a147782b19c87e3adfa7be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766370"
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="78f53-102">Operações Transacionadas Confirmadas por Segundo</span><span class="sxs-lookup"><span data-stu-id="78f53-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="78f53-103">Nome do contador: Operações transacionadas confirmadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="78f53-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="78f53-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="78f53-104">Description</span></span>  
 <span data-ttu-id="78f53-105">Número de operações transacionais que foram confirmadas neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="78f53-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="78f53-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="78f53-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="78f53-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="78f53-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
