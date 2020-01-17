---
title: Operações Transacionadas em Dúvida por Segundo
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: bc978f5b45352fa9fcce5aee5a616c9f86f56aeb
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163833"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="4f1cd-102">Operações Transacionadas em Dúvida por Segundo</span><span class="sxs-lookup"><span data-stu-id="4f1cd-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="4f1cd-103">Nome do contador: operações transacionadas em dúvida por segundo.</span><span class="sxs-lookup"><span data-stu-id="4f1cd-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4f1cd-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f1cd-104">Description</span></span>  
 <span data-ttu-id="4f1cd-105">Número de operações transacionais com um resultado incerto nesse serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="4f1cd-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="4f1cd-106">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="4f1cd-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="4f1cd-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="4f1cd-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
