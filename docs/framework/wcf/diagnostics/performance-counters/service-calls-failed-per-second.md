---
title: "Serviços: chamadas com falha por segundo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 632c81b6ffd84202b7609dccb89887af01ae706e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="51ad2-102">Serviços: chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="51ad2-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="51ad2-103">Nome do contador: Chamadas com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="51ad2-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="51ad2-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="51ad2-104">Description</span></span>  
 <span data-ttu-id="51ad2-105">Número de chamadas que têm exceções sem tratamento e são recebidas por este serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="51ad2-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="51ad2-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="51ad2-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="51ad2-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="51ad2-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="51ad2-108">No código gerenciado, as exceções são geradas quando ocorrem condições de erro.</span><span class="sxs-lookup"><span data-stu-id="51ad2-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="51ad2-109">No código gerenciado, as exceções são geradas quando ocorrem condições de erro.</span><span class="sxs-lookup"><span data-stu-id="51ad2-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="51ad2-110">Esse contador é incrementado toda vez que há uma exceção sem tratamento neste serviço.</span><span class="sxs-lookup"><span data-stu-id="51ad2-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ad2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51ad2-111">See Also</span></span>  
 [<span data-ttu-id="51ad2-112">Especificando e lidando com falhas em contratos e serviços</span><span class="sxs-lookup"><span data-stu-id="51ad2-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
