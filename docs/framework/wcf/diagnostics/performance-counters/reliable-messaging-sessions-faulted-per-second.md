---
title: Sessões de Mensagens Confiáveis com Falha por Segundo
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: fafc63d692d2a6892330b0be5fe534ace5d7f0ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="861d4-102">Sessões de Mensagens Confiáveis com Falha por Segundo</span><span class="sxs-lookup"><span data-stu-id="861d4-102">Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="861d4-103">Nome do contador: Sessões de mensagens confiáveis com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="861d4-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="861d4-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="861d4-104">Description</span></span>  
 <span data-ttu-id="861d4-105">Número de sessões de mensagens confiáveis com falha neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="861d4-105">Number of reliable messaging sessions that are faulted in this service in a second.</span></span>  
  
 <span data-ttu-id="861d4-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="861d4-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="861d4-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="861d4-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
