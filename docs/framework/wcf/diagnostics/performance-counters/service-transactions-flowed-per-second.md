---
title: 'Serviço: fluxo de transações por segundo'
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: e8fbc314321a46fd3539998bd3dd22770086ca37
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164002"
---
# <a name="service-transactions-flowed-per-second"></a><span data-ttu-id="8ed52-102">Serviço: fluxo de transações por segundo</span><span class="sxs-lookup"><span data-stu-id="8ed52-102">Service: Transactions Flowed Per Second</span></span>
<span data-ttu-id="8ed52-103">Nome do contador: transações fluidas por segundo.</span><span class="sxs-lookup"><span data-stu-id="8ed52-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8ed52-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ed52-104">Description</span></span>  
 <span data-ttu-id="8ed52-105">Número de transações fluidas para operações neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="8ed52-105">Number of transactions flowed to operations in this service in a second.</span></span>  
  
 <span data-ttu-id="8ed52-106">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="8ed52-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="8ed52-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="8ed52-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
