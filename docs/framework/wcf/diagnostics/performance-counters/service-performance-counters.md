---
title: Contadores de desempenho de serviço
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: dc31e05f82f232095f6560c8fdd9bf75c040e2ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210406"
---
# <a name="service-performance-counters"></a><span data-ttu-id="5e588-102">Contadores de desempenho de serviço</span><span class="sxs-lookup"><span data-stu-id="5e588-102">Service Performance Counters</span></span>
<span data-ttu-id="5e588-103">Contadores de desempenho serviço medem o comportamento de serviço como um todo e podem ser usados para diagnosticar o desempenho do serviço inteiro.</span><span class="sxs-lookup"><span data-stu-id="5e588-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="5e588-104">Eles podem ser encontrados no `ServiceModelService 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="5e588-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="5e588-105">As instâncias são nomeadas usando o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="5e588-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="5e588-106">Há um limite no comprimento do nome de uma instância contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="5e588-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="5e588-107">Quando um nome de instância de contador do Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância com um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="5e588-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e588-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e588-108">See also</span></span>

- [<span data-ttu-id="5e588-109">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="5e588-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
