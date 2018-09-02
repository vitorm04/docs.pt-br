---
title: Operações Transacionadas Anuladas por Segundo
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: 6369fea6def5ebb6b62274caed31d5fb63b3b0e1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417476"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="8272d-102">Operações Transacionadas Anuladas por Segundo</span><span class="sxs-lookup"><span data-stu-id="8272d-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="8272d-103">Nome do contador: Transacionado operações anuladas por segundo.</span><span class="sxs-lookup"><span data-stu-id="8272d-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8272d-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="8272d-104">Description</span></span>  
 <span data-ttu-id="8272d-105">Número de operações transacionais ter sido anulada neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="8272d-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="8272d-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="8272d-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="8272d-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="8272d-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
