---
title: Fluxo de transações por segundo
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: 8b6077af3f98f7a205772b4883dc122374083e00
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163820"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="019bb-102">Fluxo de transações por segundo</span><span class="sxs-lookup"><span data-stu-id="019bb-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="019bb-103">Nome do contador: transações fluidas por segundo</span><span class="sxs-lookup"><span data-stu-id="019bb-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="019bb-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="019bb-104">Description</span></span>  
 <span data-ttu-id="019bb-105">Número de transações fluidas para esta operação em um segundo.</span><span class="sxs-lookup"><span data-stu-id="019bb-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="019bb-106">Esse contador é incrementado sempre que uma ID de transação está presente em uma mensagem que é enviada para a operação.</span><span class="sxs-lookup"><span data-stu-id="019bb-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="019bb-107">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="019bb-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="019bb-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="019bb-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
