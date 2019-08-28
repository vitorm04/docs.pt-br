---
title: Contadores de desempenho de operação
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 7a9b35346333f7b910802ff2a1b1769d177f3952
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040326"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="3cf1b-102">Contadores de desempenho de operação</span><span class="sxs-lookup"><span data-stu-id="3cf1b-102">Operation Performance Counters</span></span>
<span data-ttu-id="3cf1b-103">Os contadores de desempenho de operação são `ServiceModelOperation 4.0.0.0` encontrados no objeto de desempenho ao exibir com o monitor de desempenho (Perfmon. exe).</span><span class="sxs-lookup"><span data-stu-id="3cf1b-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="3cf1b-104">Cada operação tem uma instância individual.</span><span class="sxs-lookup"><span data-stu-id="3cf1b-104">Each operation has an individual instance.</span></span> <span data-ttu-id="3cf1b-105">Ou seja, se um determinado contrato tiver 10 operações, 10 instâncias do contador de operações serão associadas a esse contrato.</span><span class="sxs-lookup"><span data-stu-id="3cf1b-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="3cf1b-106">As instâncias de objeto são nomeadas usando o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="3cf1b-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="3cf1b-107">Esse contador permite que você meça como a chamada está sendo usada e o quão bem a operação está sendo executada.</span><span class="sxs-lookup"><span data-stu-id="3cf1b-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="3cf1b-108">Há um limite no comprimento do nome de uma instância do contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="3cf1b-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="3cf1b-109">Quando um nome de instância de contador de Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância por um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="3cf1b-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf1b-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cf1b-110">See also</span></span>

- [<span data-ttu-id="3cf1b-111">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="3cf1b-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
