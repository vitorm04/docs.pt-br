---
title: Mensagens da fila ignoradas por segundo
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: 47835086a4ee920e814d9dd6c1e41b9cdc33efec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="145ad-102">Mensagens da fila ignoradas por segundo</span><span class="sxs-lookup"><span data-stu-id="145ad-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="145ad-103">Nome do contador: Na fila de mensagens descartadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="145ad-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="145ad-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="145ad-104">Description</span></span>  
 <span data-ttu-id="145ad-105">Número de mensagens que são ignoradas pelo transporte em fila neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="145ad-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="145ad-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="145ad-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="145ad-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="145ad-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
