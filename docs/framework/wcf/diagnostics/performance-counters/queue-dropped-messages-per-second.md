---
title: Mensagens da fila ignoradas por segundo
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: f15b2db08ac4486377189a1533b653260d79024a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418242"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="fb982-102">Mensagens da fila ignoradas por segundo</span><span class="sxs-lookup"><span data-stu-id="fb982-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="fb982-103">Nome do contador: Na fila de mensagens descartadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="fb982-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fb982-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb982-104">Description</span></span>  
 <span data-ttu-id="fb982-105">Número de mensagens que serão descartadas pelo transporte enfileirado neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="fb982-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="fb982-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="fb982-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fb982-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="fb982-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
