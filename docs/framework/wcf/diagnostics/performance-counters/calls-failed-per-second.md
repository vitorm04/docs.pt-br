---
title: Chamadas com falha por segundo
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: ff9320b0990a0543bbb1da553d040ff5a4b4fed9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178614"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="d861e-102">Chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="d861e-102">Calls Failed Per Second</span></span>
<span data-ttu-id="d861e-103">Nome do contador: Chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="d861e-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="d861e-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="d861e-104">Description</span></span>  
 <span data-ttu-id="d861e-105">Número de chamadas com exceções não tratadas nesta operação em um segundo.</span><span class="sxs-lookup"><span data-stu-id="d861e-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="d861e-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="d861e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d861e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="d861e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="d861e-108">Esse contador é incrementado toda vez que há uma exceção sem tratamento nesta operação.</span><span class="sxs-lookup"><span data-stu-id="d861e-108">This counter is incremented everytime there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d861e-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d861e-109">See also</span></span>

- [<span data-ttu-id="d861e-110">Especificando e lidando com falhas em contratos e serviços</span><span class="sxs-lookup"><span data-stu-id="d861e-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
