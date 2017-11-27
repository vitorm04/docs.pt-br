---
title: "Ponto de extremidade: fluxo de transações por segundo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dc0764c689db15a256ad8384c10010c33b6a99f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="f7b18-102">Ponto de extremidade: fluxo de transações por segundo</span><span class="sxs-lookup"><span data-stu-id="f7b18-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="f7b18-103">Nome do contador: Fluxo de transações por segundo.</span><span class="sxs-lookup"><span data-stu-id="f7b18-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f7b18-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7b18-104">Description</span></span>  
 <span data-ttu-id="f7b18-105">Número de transações fluíram para operações neste ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="f7b18-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="f7b18-106">Esse contador é incrementado sempre que uma ID de transação está presente em uma mensagem enviada ao ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f7b18-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="f7b18-107">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="f7b18-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f7b18-108">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="f7b18-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
