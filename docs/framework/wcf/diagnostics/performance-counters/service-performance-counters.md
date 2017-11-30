---
title: "Contadores de desempenho de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: de51c6d0a3070f8bba8a2c77f9c028e7cfbc944d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="service-performance-counters"></a><span data-ttu-id="6969d-102">Contadores de desempenho de serviço</span><span class="sxs-lookup"><span data-stu-id="6969d-102">Service Performance Counters</span></span>
<span data-ttu-id="6969d-103">Contadores de desempenho serviço medem o comportamento de serviço como um todo e podem ser usados para diagnosticar o desempenho do serviço inteiro.</span><span class="sxs-lookup"><span data-stu-id="6969d-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="6969d-104">Eles podem ser encontrados no `ServiceModelService 4.0.0.0` objeto de desempenho durante a exibição de Monitor de desempenho (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="6969d-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="6969d-105">As instâncias são nomeadas usando o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="6969d-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="6969d-106">Há um limite de comprimento do nome de uma instância contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="6969d-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="6969d-107">Quando um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] nome de instância do contador excede o comprimento máximo, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] substitui uma parte do nome da instância com um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="6969d-107">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6969d-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6969d-108">See Also</span></span>  
 [<span data-ttu-id="6969d-109">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="6969d-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
