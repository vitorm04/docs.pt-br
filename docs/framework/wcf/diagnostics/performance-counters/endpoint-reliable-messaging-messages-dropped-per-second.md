---
title: 'Ponto de extremidade: mensagens confiáveis do sistema de mensagens descartadas por segundo'
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: a87e5fef0c13e239959a386f108af3c4cebae7f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472278"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="e13d7-102">Ponto de extremidade: mensagens confiáveis do sistema de mensagens descartadas por segundo</span><span class="sxs-lookup"><span data-stu-id="e13d7-102">Endpoint: Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="e13d7-103">Nome do contador: Sessões de mensagens confiáveis descartadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="e13d7-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e13d7-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="e13d7-104">Description</span></span>  
 <span data-ttu-id="e13d7-105">Número total de mensagens confiáveis que foram ignoradas neste ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="e13d7-105">Total number of reliable messaging messages that have been dropped at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="e13d7-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="e13d7-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e13d7-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="e13d7-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
