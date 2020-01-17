---
title: 'Serviço: chamadas por segundo'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: be5d77169a71d6f44205a1150da5239eceff7d9c
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163887"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="4be7b-102">Serviço: chamadas por segundo</span><span class="sxs-lookup"><span data-stu-id="4be7b-102">Service: Calls Per Second</span></span>
<span data-ttu-id="4be7b-103">Nome do contador: chamadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="4be7b-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4be7b-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="4be7b-104">Description</span></span>  
 <span data-ttu-id="4be7b-105">Número de chamadas para esse serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="4be7b-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="4be7b-106">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="4be7b-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="4be7b-107">(N 1-N 0)/((D 1-D 0)/F) em que o numerador (N) representa o número de operações executadas durante o último intervalo de amostragem, o denominador (D) representa o número de tiques decorridos durante o último intervalo de amostragem e F é a frequência das tiques.</span><span class="sxs-lookup"><span data-stu-id="4be7b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
