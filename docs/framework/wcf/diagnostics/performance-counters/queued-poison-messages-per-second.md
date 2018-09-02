---
title: Mensagens suspeitas na fila por segundo
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: d4c921b105dfd1c1a364d2c86f54ab920078dd4a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420683"
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="6d9e5-102">Mensagens suspeitas na fila por segundo</span><span class="sxs-lookup"><span data-stu-id="6d9e5-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="6d9e5-103">Nome do contador: Na fila de mensagens suspeitas por segundo.</span><span class="sxs-lookup"><span data-stu-id="6d9e5-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6d9e5-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d9e5-104">Description</span></span>  
 <span data-ttu-id="6d9e5-105">Número de mensagens que são marcados como inviabilizado pelo transporte neste serviço em fila em um segundo.</span><span class="sxs-lookup"><span data-stu-id="6d9e5-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="6d9e5-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="6d9e5-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="6d9e5-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="6d9e5-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
