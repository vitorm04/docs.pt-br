---
title: Chamadas com falha por segundo
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: ccb5908e9036650e3f21a9496649c8090c2e47b2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736316"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="51db9-102">Chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="51db9-102">Calls Failed Per Second</span></span>
<span data-ttu-id="51db9-103">Nome do contador: Chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="51db9-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="51db9-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="51db9-104">Description</span></span>  
 <span data-ttu-id="51db9-105">Número de chamadas com exceções não tratadas nesta operação em um segundo.</span><span class="sxs-lookup"><span data-stu-id="51db9-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="51db9-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="51db9-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="51db9-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="51db9-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="51db9-108">Esse contador é incrementado toda vez que há uma exceção sem tratamento nesta operação.</span><span class="sxs-lookup"><span data-stu-id="51db9-108">This counter is incremented everytime there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51db9-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51db9-109">See Also</span></span>  
 [<span data-ttu-id="51db9-110">Especificando e lidando com falhas em contratos e serviços</span><span class="sxs-lookup"><span data-stu-id="51db9-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
