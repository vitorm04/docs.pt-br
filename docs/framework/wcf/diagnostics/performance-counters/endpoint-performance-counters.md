---
title: Contadores de desempenho de ponto de extremidade
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 1b0f7462fea8843bcb0a0938a8034f405f30a6fb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320508"
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="a4eea-102">Contadores de desempenho de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="a4eea-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="a4eea-103">Os contadores de desempenho de ponto de extremidade capturam dados que revela como um ponto de extremidade está aceitando mensagens.</span><span class="sxs-lookup"><span data-stu-id="a4eea-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="a4eea-104">Eles podem ser encontrados no objeto de desempenho `ServiceModelEndpoint 4.0.0.0` ao exibir com o monitor de desempenho.</span><span class="sxs-lookup"><span data-stu-id="a4eea-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="a4eea-105">As instâncias são nomeadas usando esse padrão:</span><span class="sxs-lookup"><span data-stu-id="a4eea-105">The instances are named using this pattern:</span></span>  
  
`(ServiceName).(ContractName)@(endpoint listener address)`  
  
 <span data-ttu-id="a4eea-106">Os dados são semelhantes aos coletados para operações individuais, mas são agregados somente no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a4eea-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="a4eea-107">Há um limite no comprimento do nome de uma instância do contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="a4eea-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="a4eea-108">Quando um nome de instância de contador de Windows Communication Foundation (WCF) excede o comprimento máximo, o WCF substitui uma parte do nome da instância por um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="a4eea-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4eea-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4eea-109">See also</span></span>

- [<span data-ttu-id="a4eea-110">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="a4eea-110">Performance Counters</span></span>](index.md)
