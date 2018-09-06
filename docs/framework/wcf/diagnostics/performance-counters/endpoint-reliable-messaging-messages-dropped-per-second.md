---
title: 'Ponto de extremidade: mensagens confiáveis do sistema de mensagens descartadas por segundo'
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: 8f935bee06d175ce454bd7f58a1afbbe9ab505ad
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863498"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="27626-102">Ponto de extremidade: mensagens confiáveis do sistema de mensagens descartadas por segundo</span><span class="sxs-lookup"><span data-stu-id="27626-102">Endpoint: Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="27626-103">Nome do contador: Sessões de Reliable Messaging eliminados por segundo.</span><span class="sxs-lookup"><span data-stu-id="27626-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="27626-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="27626-104">Description</span></span>  
 <span data-ttu-id="27626-105">Número total de mensagens confiáveis que foram descartados nesse ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="27626-105">Total number of reliable messaging messages that have been dropped at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="27626-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="27626-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="27626-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="27626-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
