---
title: Sessões de transmissão de mensagens confiáveis com falha por segundo
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: 4dd247131182aca65a837095144673690cb134c8
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163937"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="fb267-102">Sessões de transmissão de mensagens confiáveis com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="fb267-102">Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="fb267-103">Nome do contador: sessões de mensagens confiáveis com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="fb267-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fb267-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb267-104">Description</span></span>  
 <span data-ttu-id="fb267-105">Número de sessões de mensagens confiáveis com falha neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="fb267-105">Number of reliable messaging sessions that are faulted in this service in a second.</span></span>  
  
 <span data-ttu-id="fb267-106">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="fb267-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fb267-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="fb267-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
