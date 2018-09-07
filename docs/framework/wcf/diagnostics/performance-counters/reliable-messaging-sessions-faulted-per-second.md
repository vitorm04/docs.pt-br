---
title: Sessões de Mensagens Confiáveis com Falha por Segundo
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: c77d6a5f12dcce15dba94e2f63025a219ebcc6fd
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44077152"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="065af-102">Sessões de Mensagens Confiáveis com Falha por Segundo</span><span class="sxs-lookup"><span data-stu-id="065af-102">Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="065af-103">Nome do contador: Sessões de Reliable Messaging com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="065af-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="065af-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="065af-104">Description</span></span>  
 <span data-ttu-id="065af-105">Número de sessões de reliable messaging com falha neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="065af-105">Number of reliable messaging sessions that are faulted in this service in a second.</span></span>  
  
 <span data-ttu-id="065af-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="065af-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="065af-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="065af-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
