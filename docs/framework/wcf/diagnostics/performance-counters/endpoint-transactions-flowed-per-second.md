---
title: 'Ponto de extremidade: fluxo de transações por segundo'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 39458dcb6ac033fd5084b5f2e760e0e26c345da7
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163547"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="47275-102">Ponto de extremidade: fluxo de transações por segundo</span><span class="sxs-lookup"><span data-stu-id="47275-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="47275-103">Nome do contador: transações fluidas por segundo.</span><span class="sxs-lookup"><span data-stu-id="47275-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="47275-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="47275-104">Description</span></span>  
 <span data-ttu-id="47275-105">Número de transações fluidas para operações neste ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="47275-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="47275-106">Esse contador é incrementado sempre que uma ID de transação está presente em uma mensagem enviada ao ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="47275-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="47275-107">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="47275-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="47275-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="47275-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
