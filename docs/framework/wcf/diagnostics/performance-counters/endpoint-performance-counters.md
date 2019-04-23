---
title: Contadores de desempenho de ponto de extremidade
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: f07e318e39a68e689ec484b09fa743623cfb51d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158374"
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="ec4fd-102">Contadores de desempenho de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="ec4fd-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="ec4fd-103">Contadores de desempenho do ponto de extremidade capturam dados que revela como um ponto de extremidade é aceitar mensagens.</span><span class="sxs-lookup"><span data-stu-id="ec4fd-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="ec4fd-104">Eles podem ser encontrados no `ServiceModelEndpoint 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ec4fd-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="ec4fd-105">As instâncias são nomeadas usando esse padrão:</span><span class="sxs-lookup"><span data-stu-id="ec4fd-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="ec4fd-106">Os dados é semelhantes ao que coletados para operações individuais, mas só são agregados entre o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ec4fd-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ec4fd-107">Há um limite no comprimento do nome de uma instância contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ec4fd-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="ec4fd-108">Quando um nome de instância de contador do Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância com um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="ec4fd-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec4fd-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec4fd-109">See also</span></span>

- [<span data-ttu-id="ec4fd-110">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="ec4fd-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
