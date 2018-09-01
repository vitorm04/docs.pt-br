---
title: Fluxo de transações por segundo
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: e77aef4cfff1e64f112e720183675dfb7aa25d27
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392930"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="22dee-102">Fluxo de transações por segundo</span><span class="sxs-lookup"><span data-stu-id="22dee-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="22dee-103">Nome do contador: Fluxo de transações por segundo</span><span class="sxs-lookup"><span data-stu-id="22dee-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="22dee-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="22dee-104">Description</span></span>  
 <span data-ttu-id="22dee-105">Número de transações flui para essa operação em um segundo.</span><span class="sxs-lookup"><span data-stu-id="22dee-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="22dee-106">Esse contador é incrementado sempre que uma ID de transação está presente em uma mensagem que é enviada para a operação.</span><span class="sxs-lookup"><span data-stu-id="22dee-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="22dee-107">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="22dee-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="22dee-108">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="22dee-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
