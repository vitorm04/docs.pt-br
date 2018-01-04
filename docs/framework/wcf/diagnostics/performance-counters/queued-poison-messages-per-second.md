---
title: Mensagens suspeitas na fila por segundo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8f22d200834927204918324ced70ac02c3c669f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="5be4b-102">Mensagens suspeitas na fila por segundo</span><span class="sxs-lookup"><span data-stu-id="5be4b-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="5be4b-103">Nome do contador: Na fila de mensagens suspeitas por segundo.</span><span class="sxs-lookup"><span data-stu-id="5be4b-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5be4b-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="5be4b-104">Description</span></span>  
 <span data-ttu-id="5be4b-105">Número de mensagens que são marcadas como suspeitas pelo transporte em fila neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="5be4b-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="5be4b-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="5be4b-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5be4b-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="5be4b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
