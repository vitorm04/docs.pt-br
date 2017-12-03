---
title: Chamadas por segundo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0efb5a94-d83b-4793-b529-6fcbedb65c43
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: baef18df3e1dda8725859c9529ab61c0668c8ff3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="calls-per-second"></a><span data-ttu-id="cbe58-102">Chamadas por segundo</span><span class="sxs-lookup"><span data-stu-id="cbe58-102">Calls Per Second</span></span>
<span data-ttu-id="cbe58-103">Nome do contador: Chamadas por segundo</span><span class="sxs-lookup"><span data-stu-id="cbe58-103">Counter Name: Calls Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="cbe58-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="cbe58-104">Description</span></span>  
 <span data-ttu-id="cbe58-105">Número de chamadas para esta operação em um segundo.</span><span class="sxs-lookup"><span data-stu-id="cbe58-105">Number of calls to this operation in a second.</span></span>  
  
 <span data-ttu-id="cbe58-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="cbe58-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="cbe58-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="cbe58-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
