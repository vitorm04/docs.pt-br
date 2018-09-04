---
title: Mensagens em fila rejeitadas por segundo
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: 096e2188b13d0fd5a9be35e5e6473107a58c5566
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507274"
---
# <a name="queued-rejected-messages-per-second"></a><span data-ttu-id="3fab0-102">Mensagens em fila rejeitadas por segundo</span><span class="sxs-lookup"><span data-stu-id="3fab0-102">Queued Rejected Messages Per Second</span></span>
<span data-ttu-id="3fab0-103">Nome do contador: Na fila de mensagens rejeitadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="3fab0-103">Counter Name: Queued Messages Rejected Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3fab0-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="3fab0-104">Description</span></span>  
 <span data-ttu-id="3fab0-105">Número de mensagens que foram rejeitadas pelo transporte enfileirado neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="3fab0-105">Number of messages that are rejected by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="3fab0-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="3fab0-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="3fab0-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="3fab0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
