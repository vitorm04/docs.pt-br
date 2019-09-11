---
title: Contadores de desempenho de serviço
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 4ce0efbeb0a1d6f2409bb976102b8ec8821d5cdc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848989"
---
# <a name="service-performance-counters"></a><span data-ttu-id="7220a-102">Contadores de desempenho de serviço</span><span class="sxs-lookup"><span data-stu-id="7220a-102">Service Performance Counters</span></span>
<span data-ttu-id="7220a-103">Os contadores de desempenho de serviço medem o comportamento do serviço como um todo e podem ser usados para diagnosticar o desempenho do serviço inteiro.</span><span class="sxs-lookup"><span data-stu-id="7220a-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="7220a-104">Eles podem ser encontrados no objeto `ServiceModelService 4.0.0.0` de desempenho ao exibir com o monitor de desempenho (Perfmon. exe).</span><span class="sxs-lookup"><span data-stu-id="7220a-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="7220a-105">As instâncias são nomeadas usando o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="7220a-105">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> <span data-ttu-id="7220a-106">Há um limite no comprimento do nome de uma instância do contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="7220a-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="7220a-107">Quando um nome de instância de contador de Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância por um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="7220a-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7220a-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7220a-108">See also</span></span>

- [<span data-ttu-id="7220a-109">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="7220a-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
