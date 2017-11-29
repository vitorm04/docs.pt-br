---
title: 'Ponto de extremidade: chamadas com falha por segundo'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5da436c5e8159ff922c36172490a28e854bbee8b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="2dff1-102">Ponto de extremidade: chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="2dff1-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="2dff1-103">Nome do contador: Chamadas com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="2dff1-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2dff1-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="2dff1-104">Description</span></span>  
 <span data-ttu-id="2dff1-105">Número de chamadas que têm exceções sem tratamento e são recebidas por este ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="2dff1-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="2dff1-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="2dff1-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2dff1-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="2dff1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="2dff1-108">Esse contador é incrementado toda vez que há uma exceção sem tratamento neste ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2dff1-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dff1-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2dff1-109">See Also</span></span>  
 <span data-ttu-id="2dff1-110">[Specifying and Handling Faults in Contracts and Services](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) (Especificando e lidando com falhas em contratos e serviços)</span><span class="sxs-lookup"><span data-stu-id="2dff1-110">[Specifying and Handling Faults in Contracts and Services](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)</span></span>
