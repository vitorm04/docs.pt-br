---
title: 'Serviço: chamadas por segundo'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 5189a78e2655707d165f187e06ac9a60d055eac0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499881"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="fb0b5-102">Serviço: chamadas por segundo</span><span class="sxs-lookup"><span data-stu-id="fb0b5-102">Service: Calls Per Second</span></span>
<span data-ttu-id="fb0b5-103">Nome do contador: Chamadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="fb0b5-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fb0b5-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb0b5-104">Description</span></span>  
 <span data-ttu-id="fb0b5-105">Número de chamadas para esse serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="fb0b5-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="fb0b5-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="fb0b5-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fb0b5-107">(N 1 - N 0) / ((1 de D -D 0) / F) em que o numerador (N) representa o número de operações executadas durante o último intervalo de amostragem, representa o denominador (D) o número de tiques decorrido desde o último intervalo de amostragem, e F é a frequência de tiques.</span><span class="sxs-lookup"><span data-stu-id="fb0b5-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
