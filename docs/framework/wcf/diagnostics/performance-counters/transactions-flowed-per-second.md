---
title: Fluxo de transações por segundo
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: a71095b9fdd16d7e220be8a0aeb0a746bb50527e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472912"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="b542a-102">Fluxo de transações por segundo</span><span class="sxs-lookup"><span data-stu-id="b542a-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="b542a-103">Nome do contador: Fluxo de transações por segundo</span><span class="sxs-lookup"><span data-stu-id="b542a-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="b542a-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="b542a-104">Description</span></span>  
 <span data-ttu-id="b542a-105">Número de transações fluíram para essa operação em um segundo.</span><span class="sxs-lookup"><span data-stu-id="b542a-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="b542a-106">Esse contador é incrementado sempre que uma ID de transação está presente em uma mensagem que é enviada para a operação.</span><span class="sxs-lookup"><span data-stu-id="b542a-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="b542a-107">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="b542a-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b542a-108">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="b542a-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
