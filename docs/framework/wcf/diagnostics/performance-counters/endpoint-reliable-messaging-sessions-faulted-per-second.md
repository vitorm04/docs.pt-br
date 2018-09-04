---
title: 'Ponto de extremidade: sessões de transmissão de mensagens confiáveis com falha por segundo'
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: f6b48ec4c37c28588dd874a5bfa94a01a2f43b0c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564181"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="969e3-102">Ponto de extremidade: sessões de transmissão de mensagens confiáveis com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="969e3-102">Endpoint: Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="969e3-103">Nome do contador: Sessões de Reliable Messaging com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="969e3-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="969e3-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="969e3-104">Description</span></span>  
 <span data-ttu-id="969e3-105">Número de sessões de reliable messaging com falha neste ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="969e3-105">Number of reliable messaging sessions that are faulted at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="969e3-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="969e3-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="969e3-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="969e3-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
