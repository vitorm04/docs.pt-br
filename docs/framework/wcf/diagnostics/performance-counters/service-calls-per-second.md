---
title: "Serviço: chamadas por segundo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 940249c4ec0317013efcb03aafc11d384ec0363f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="service-calls-per-second"></a><span data-ttu-id="f021d-102">Serviço: chamadas por segundo</span><span class="sxs-lookup"><span data-stu-id="f021d-102">Service: Calls Per Second</span></span>
<span data-ttu-id="f021d-103">Nome do contador: Chamadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="f021d-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f021d-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="f021d-104">Description</span></span>  
 <span data-ttu-id="f021d-105">Número de chamadas a este serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="f021d-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="f021d-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="f021d-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f021d-107">(1 - N 0 N) / ((1 D -D 0) / F) onde o numerador (N) representa o número de operações executadas durante o último intervalo de amostragem, representa o denominador (D) que o número de tiques decorrido desde o último intervalo de amostragem, e F é a frequência de tiques.</span><span class="sxs-lookup"><span data-stu-id="f021d-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
