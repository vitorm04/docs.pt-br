---
title: 'Ponto de extremidade: mensagens confiáveis do sistema de mensagens descartadas por segundo'
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: 06259ba0d60d9f1cec7717364f2e014bb123ee40
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550261"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="e9c55-102">Ponto de extremidade: mensagens confiáveis do sistema de mensagens descartadas por segundo</span><span class="sxs-lookup"><span data-stu-id="e9c55-102">Endpoint: Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="e9c55-103">Nome do contador: sessões de mensagens confiáveis eliminadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="e9c55-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e9c55-104">Description</span><span class="sxs-lookup"><span data-stu-id="e9c55-104">Description</span></span>  
 <span data-ttu-id="e9c55-105">Número total de mensagens de mensagens confiáveis que foram descartadas neste ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="e9c55-105">Total number of reliable messaging messages that have been dropped at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="e9c55-106">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="e9c55-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e9c55-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="e9c55-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
