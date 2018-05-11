---
title: Mensagens suspeitas na fila por segundo
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: 6407cce120f5d534f88a12591ea2ad09bb5130d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="2f1da-102">Mensagens suspeitas na fila por segundo</span><span class="sxs-lookup"><span data-stu-id="2f1da-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="2f1da-103">Nome do contador: Na fila de mensagens suspeitas por segundo.</span><span class="sxs-lookup"><span data-stu-id="2f1da-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2f1da-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f1da-104">Description</span></span>  
 <span data-ttu-id="2f1da-105">Número de mensagens que são marcadas como suspeitas pelo transporte em fila neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="2f1da-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="2f1da-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="2f1da-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2f1da-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="2f1da-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
