---
title: Contadores de desempenho de operação
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 59c75dacb2a01f1b85d67d5cc1651dbc55b6aa8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320173"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="6fdd8-102">Contadores de desempenho de operação</span><span class="sxs-lookup"><span data-stu-id="6fdd8-102">Operation Performance Counters</span></span>
<span data-ttu-id="6fdd8-103">Os contadores de desempenho de operação são encontrados no objeto de desempenho `ServiceModelOperation 4.0.0.0` ao exibir com o monitor de desempenho (Perfmon. exe).</span><span class="sxs-lookup"><span data-stu-id="6fdd8-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="6fdd8-104">Cada operação tem uma instância individual.</span><span class="sxs-lookup"><span data-stu-id="6fdd8-104">Each operation has an individual instance.</span></span> <span data-ttu-id="6fdd8-105">Ou seja, se um determinado contrato tiver 10 operações, 10 instâncias do contador de operações serão associadas a esse contrato.</span><span class="sxs-lookup"><span data-stu-id="6fdd8-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="6fdd8-106">As instâncias de objeto são nomeadas usando o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="6fdd8-106">The object instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 <span data-ttu-id="6fdd8-107">Esse contador permite que você meça como a chamada está sendo usada e o quão bem a operação está sendo executada.</span><span class="sxs-lookup"><span data-stu-id="6fdd8-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="6fdd8-108">Há um limite no comprimento do nome de uma instância do contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="6fdd8-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="6fdd8-109">Quando um nome de instância de contador de Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância por um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="6fdd8-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fdd8-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fdd8-110">See also</span></span>

- [<span data-ttu-id="6fdd8-111">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="6fdd8-111">Performance Counters</span></span>](index.md)
