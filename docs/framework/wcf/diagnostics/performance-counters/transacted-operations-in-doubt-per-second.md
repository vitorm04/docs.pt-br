---
title: Operações Transacionadas em Dúvida por Segundo
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: f7365c4e5f03711129916c8c6964f7e25e9b553e
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44507952"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="4708a-102">Operações Transacionadas em Dúvida por Segundo</span><span class="sxs-lookup"><span data-stu-id="4708a-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="4708a-103">Nome do contador: Operações transacionadas em dúvida por segundo.</span><span class="sxs-lookup"><span data-stu-id="4708a-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4708a-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="4708a-104">Description</span></span>  
 <span data-ttu-id="4708a-105">Número de operações transacionais com resultados em dúvida neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="4708a-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="4708a-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="4708a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="4708a-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="4708a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
