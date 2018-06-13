---
title: Operações Transacionadas Anuladas por Segundo
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: dacdf93f4610df9161134a41ece19fd2a18637c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474526"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="a0cfc-102">Operações Transacionadas Anuladas por Segundo</span><span class="sxs-lookup"><span data-stu-id="a0cfc-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="a0cfc-103">Nome do contador: Transacionado operações anuladas por segundo.</span><span class="sxs-lookup"><span data-stu-id="a0cfc-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a0cfc-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0cfc-104">Description</span></span>  
 <span data-ttu-id="a0cfc-105">Número de operações transacionais anulados neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="a0cfc-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="a0cfc-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="a0cfc-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="a0cfc-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="a0cfc-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
