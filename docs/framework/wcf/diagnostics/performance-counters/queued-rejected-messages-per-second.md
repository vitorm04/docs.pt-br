---
title: Mensagens em fila rejeitadas por segundo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a773d30cc9cb33a9bd3a1e1fb5562026bcfb7e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="queued-rejected-messages-per-second"></a><span data-ttu-id="bb6c9-102">Mensagens em fila rejeitadas por segundo</span><span class="sxs-lookup"><span data-stu-id="bb6c9-102">Queued Rejected Messages Per Second</span></span>
<span data-ttu-id="bb6c9-103">Nome do contador: Na fila de mensagens rejeitadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="bb6c9-103">Counter Name: Queued Messages Rejected Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bb6c9-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb6c9-104">Description</span></span>  
 <span data-ttu-id="bb6c9-105">Número de mensagens que foram rejeitadas pelo transporte em fila neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="bb6c9-105">Number of messages that are rejected by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="bb6c9-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="bb6c9-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="bb6c9-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="bb6c9-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
