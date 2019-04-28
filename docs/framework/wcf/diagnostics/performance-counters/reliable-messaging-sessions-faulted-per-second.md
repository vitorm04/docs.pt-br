---
title: Sessões de transmissão de mensagens confiáveis com falha por segundo
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: c77d6a5f12dcce15dba94e2f63025a219ebcc6fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916117"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="75daa-102">Sessões de transmissão de mensagens confiáveis com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="75daa-102">Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="75daa-103">Nome do contador: Sessões de Reliable Messaging com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="75daa-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="75daa-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="75daa-104">Description</span></span>  
 <span data-ttu-id="75daa-105">Número de sessões de reliable messaging com falha neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="75daa-105">Number of reliable messaging sessions that are faulted in this service in a second.</span></span>  
  
 <span data-ttu-id="75daa-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="75daa-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="75daa-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="75daa-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
