---
title: "Operações Transacionadas Anuladas por Segundo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d80d18ed1e3911b0603f930e45bda3dffaff1f75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="ba9fb-102">Operações Transacionadas Anuladas por Segundo</span><span class="sxs-lookup"><span data-stu-id="ba9fb-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="ba9fb-103">Nome do contador: Transacionado operações anuladas por segundo.</span><span class="sxs-lookup"><span data-stu-id="ba9fb-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ba9fb-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba9fb-104">Description</span></span>  
 <span data-ttu-id="ba9fb-105">Número de operações transacionais anulados neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="ba9fb-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="ba9fb-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="ba9fb-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ba9fb-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="ba9fb-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
