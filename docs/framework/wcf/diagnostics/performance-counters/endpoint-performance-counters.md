---
title: Contadores de desempenho de ponto de extremidade
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d34df7c70e0edeef831843d9afcb2db32422ebe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="89dc3-102">Contadores de desempenho de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="89dc3-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="89dc3-103">Contadores de desempenho do ponto de extremidade capturar dados revela como um ponto de extremidade é aceitar mensagens.</span><span class="sxs-lookup"><span data-stu-id="89dc3-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="89dc3-104">Eles podem ser encontrados no `ServiceModelEndpoint 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho.</span><span class="sxs-lookup"><span data-stu-id="89dc3-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="89dc3-105">As instâncias são nomeadas usando esse padrão:</span><span class="sxs-lookup"><span data-stu-id="89dc3-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="89dc3-106">Os dados é semelhantes ao que coletados para as operações individuais, mas só são agregados entre o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="89dc3-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="89dc3-107">Há um limite de comprimento do nome de uma instância contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="89dc3-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="89dc3-108">Quando um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] nome de instância do contador excede o comprimento máximo, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] substitui uma parte do nome da instância com um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="89dc3-108">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89dc3-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89dc3-109">See Also</span></span>  
 [<span data-ttu-id="89dc3-110">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="89dc3-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
