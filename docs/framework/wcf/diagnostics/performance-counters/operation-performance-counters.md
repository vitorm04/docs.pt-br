---
title: "Contadores de desempenho de operação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 83460e1c4db17938466051269dbeba3f19e0b40a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="operation-performance-counters"></a><span data-ttu-id="af2ef-102">Contadores de desempenho de operação</span><span class="sxs-lookup"><span data-stu-id="af2ef-102">Operation Performance Counters</span></span>
<span data-ttu-id="af2ef-103">Contadores de desempenho da operação estão localizados sob o `ServiceModelOperation 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="af2ef-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="af2ef-104">Cada operação tem uma instância individual.</span><span class="sxs-lookup"><span data-stu-id="af2ef-104">Each operation has an individual instance.</span></span> <span data-ttu-id="af2ef-105">Ou seja, se um dado contrato tem operações de 10, 10 instâncias de contador de operação são associadas com esse contrato.</span><span class="sxs-lookup"><span data-stu-id="af2ef-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="af2ef-106">As instâncias de objeto são nomeadas usando o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="af2ef-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="af2ef-107">Esse contador permite avaliar como a chamada está sendo usada e como a operação está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="af2ef-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="af2ef-108">Há um limite de comprimento do nome de uma instância contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="af2ef-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="af2ef-109">Quando um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] nome de instância do contador excede o comprimento máximo, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] substitui uma parte do nome da instância com um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="af2ef-109">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af2ef-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af2ef-110">See Also</span></span>  
 [<span data-ttu-id="af2ef-111">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="af2ef-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
