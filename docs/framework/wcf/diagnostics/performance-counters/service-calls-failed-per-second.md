---
title: 'Serviço: Chamadas com falha por segundo'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: d87d5f06d0c9a3849ec80a3d1c7badefde7cf372
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167486"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="c9e5c-102">Serviço: Chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="c9e5c-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="c9e5c-103">Nome do contador: Chamadas com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="c9e5c-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c9e5c-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9e5c-104">Description</span></span>  
 <span data-ttu-id="c9e5c-105">Número de chamadas que têm exceções sem tratamento e recebidos por esse serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="c9e5c-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="c9e5c-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="c9e5c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c9e5c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="c9e5c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="c9e5c-108">No código gerenciado, as exceções são geradas quando ocorrem condições de erro.</span><span class="sxs-lookup"><span data-stu-id="c9e5c-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="c9e5c-109">No código gerenciado, as exceções são geradas quando ocorrem condições de erro.</span><span class="sxs-lookup"><span data-stu-id="c9e5c-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="c9e5c-110">Esse contador é incrementado sempre que houver uma exceção não tratada neste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9e5c-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9e5c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9e5c-111">See also</span></span>

- [<span data-ttu-id="c9e5c-112">Especificando e lidando com falhas em contratos e serviços</span><span class="sxs-lookup"><span data-stu-id="c9e5c-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
