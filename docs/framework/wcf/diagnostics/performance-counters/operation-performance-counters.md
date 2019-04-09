---
title: Contadores de desempenho de operação
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: d4f5755129fecb62e6a4da98a2bf642c5e20f9c1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077102"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="953b4-102">Contadores de desempenho de operação</span><span class="sxs-lookup"><span data-stu-id="953b4-102">Operation Performance Counters</span></span>
<span data-ttu-id="953b4-103">Contadores de desempenho da operação estiverem localizados no `ServiceModelOperation 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="953b4-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="953b4-104">Cada operação tem uma instância individual.</span><span class="sxs-lookup"><span data-stu-id="953b4-104">Each operation has an individual instance.</span></span> <span data-ttu-id="953b4-105">Ou seja, se um determinado contrato tem 10 operações, 10 instâncias de contador de operação são associadas esse contrato.</span><span class="sxs-lookup"><span data-stu-id="953b4-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="953b4-106">As instâncias de objeto são nomeadas usando o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="953b4-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="953b4-107">Esse contador permite medir como a chamada está sendo usada e como a operação está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="953b4-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="953b4-108">Há um limite no comprimento do nome de uma instância contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="953b4-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="953b4-109">Quando um nome de instância de contador do Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância com um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="953b4-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="953b4-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="953b4-110">See also</span></span>

- [<span data-ttu-id="953b4-111">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="953b4-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
