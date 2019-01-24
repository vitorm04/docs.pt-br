---
title: Contadores de desempenho de serviço
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: bf0b12e6d4954c0a1392554d7269a7d539a77dc1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545584"
---
# <a name="service-performance-counters"></a><span data-ttu-id="45f8d-102">Contadores de desempenho de serviço</span><span class="sxs-lookup"><span data-stu-id="45f8d-102">Service Performance Counters</span></span>
<span data-ttu-id="45f8d-103">Contadores de desempenho serviço medem o comportamento de serviço como um todo e podem ser usados para diagnosticar o desempenho do serviço inteiro.</span><span class="sxs-lookup"><span data-stu-id="45f8d-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="45f8d-104">Eles podem ser encontrados no `ServiceModelService 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="45f8d-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="45f8d-105">As instâncias são nomeadas usando o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="45f8d-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="45f8d-106">Há um limite no comprimento do nome de uma instância contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="45f8d-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="45f8d-107">Quando um nome de instância de contador do Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância com um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="45f8d-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45f8d-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45f8d-108">See also</span></span>
- [<span data-ttu-id="45f8d-109">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="45f8d-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
