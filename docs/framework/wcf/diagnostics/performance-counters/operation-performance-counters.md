---
title: Contadores de desempenho de operação
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 46b7d5ff071ebf1e3f790a9b56906d9908028ae9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804411"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="84ed8-102">Contadores de desempenho de operação</span><span class="sxs-lookup"><span data-stu-id="84ed8-102">Operation Performance Counters</span></span>
<span data-ttu-id="84ed8-103">Contadores de desempenho da operação estão localizados sob o `ServiceModelOperation 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="84ed8-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="84ed8-104">Cada operação tem uma instância individual.</span><span class="sxs-lookup"><span data-stu-id="84ed8-104">Each operation has an individual instance.</span></span> <span data-ttu-id="84ed8-105">Ou seja, se um dado contrato tem operações de 10, 10 instâncias de contador de operação são associadas com esse contrato.</span><span class="sxs-lookup"><span data-stu-id="84ed8-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="84ed8-106">As instâncias de objeto são nomeadas usando o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="84ed8-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="84ed8-107">Esse contador permite avaliar como a chamada está sendo usada e como a operação está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="84ed8-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="84ed8-108">Há um limite de comprimento do nome de uma instância contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="84ed8-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="84ed8-109">Quando um nome de instância de contador do Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância com um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="84ed8-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ed8-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84ed8-110">See Also</span></span>  
 [<span data-ttu-id="84ed8-111">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="84ed8-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
