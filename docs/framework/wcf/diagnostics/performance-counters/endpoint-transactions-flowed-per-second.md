---
title: 'Ponto de extremidade: fluxo de transações por segundo'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 9391651eaaca130ef47ddee9daa95b1f8c116892
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553786"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="11262-102">Ponto de extremidade: fluxo de transações por segundo</span><span class="sxs-lookup"><span data-stu-id="11262-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="11262-103">Nome do contador: transações fluidas por segundo.</span><span class="sxs-lookup"><span data-stu-id="11262-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="11262-104">Description</span><span class="sxs-lookup"><span data-stu-id="11262-104">Description</span></span>  
 <span data-ttu-id="11262-105">Número de transações fluidas para operações neste ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="11262-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="11262-106">Esse contador é incrementado sempre que uma ID de transação está presente em uma mensagem enviada ao ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="11262-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="11262-107">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="11262-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="11262-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="11262-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
