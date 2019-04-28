---
title: 'Ponto de extremidade: Fluxo de transações por segundo'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 79f50b6706facd040ec2d325c676f210d5327bf8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916247"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="04d4f-102">Ponto de extremidade: Fluxo de transações por segundo</span><span class="sxs-lookup"><span data-stu-id="04d4f-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="04d4f-103">Nome do contador: Fluxo de transações por segundo.</span><span class="sxs-lookup"><span data-stu-id="04d4f-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="04d4f-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="04d4f-104">Description</span></span>  
 <span data-ttu-id="04d4f-105">Número de transações de fluir para operações nesse ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="04d4f-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="04d4f-106">Esse contador é incrementado sempre que uma ID de transação está presente em uma mensagem enviada para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="04d4f-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="04d4f-107">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="04d4f-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="04d4f-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="04d4f-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
