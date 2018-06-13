---
title: 'Serviço: fluxo de transações por segundo'
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: 1151117c8537d4a8eaa4de60d14e314b55ce82d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474838"
---
# <a name="service-transactions-flowed-per-second"></a><span data-ttu-id="15db4-102">Serviço: fluxo de transações por segundo</span><span class="sxs-lookup"><span data-stu-id="15db4-102">Service: Transactions Flowed Per Second</span></span>
<span data-ttu-id="15db4-103">Nome do contador: Fluxo de transações por segundo.</span><span class="sxs-lookup"><span data-stu-id="15db4-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="15db4-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="15db4-104">Description</span></span>  
 <span data-ttu-id="15db4-105">Número de transações fluíram para operações neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="15db4-105">Number of transactions flowed to operations in this service in a second.</span></span>  
  
 <span data-ttu-id="15db4-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="15db4-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="15db4-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="15db4-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
