---
title: "Fluxo de transações por segundo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 432ed6adbaa1f121f11680e0f9574a642565a6f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="4d721-102">Fluxo de transações por segundo</span><span class="sxs-lookup"><span data-stu-id="4d721-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="4d721-103">Nome do contador: Fluxo de transações por segundo</span><span class="sxs-lookup"><span data-stu-id="4d721-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="4d721-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d721-104">Description</span></span>  
 <span data-ttu-id="4d721-105">Número de transações fluíram para essa operação em um segundo.</span><span class="sxs-lookup"><span data-stu-id="4d721-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="4d721-106">Esse contador é incrementado sempre que uma ID de transação está presente em uma mensagem que é enviada para a operação.</span><span class="sxs-lookup"><span data-stu-id="4d721-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="4d721-107">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="4d721-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="4d721-108">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="4d721-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
