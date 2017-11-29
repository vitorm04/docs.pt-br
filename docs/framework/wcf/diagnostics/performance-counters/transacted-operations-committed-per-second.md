---
title: "Operações Transacionadas Confirmadas por Segundo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0408bbc4bbe6e49bcd830a1de8563c02002f1b7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="1ba4f-102">Operações Transacionadas Confirmadas por Segundo</span><span class="sxs-lookup"><span data-stu-id="1ba4f-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="1ba4f-103">Nome do contador: Operações transacionadas confirmadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="1ba4f-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1ba4f-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ba4f-104">Description</span></span>  
 <span data-ttu-id="1ba4f-105">Número de operações transacionais que foram confirmadas neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="1ba4f-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="1ba4f-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="1ba4f-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="1ba4f-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="1ba4f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
