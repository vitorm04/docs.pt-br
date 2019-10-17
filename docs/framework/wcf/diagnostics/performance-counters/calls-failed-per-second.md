---
title: Chamadas com falha por segundo
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: e7c0b53f4c2b1a7e87a5791b44e452ec9146c459
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321117"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="50dce-102">Chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="50dce-102">Calls Failed Per Second</span></span>
<span data-ttu-id="50dce-103">Nome do contador: chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="50dce-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="50dce-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="50dce-104">Description</span></span>  
 <span data-ttu-id="50dce-105">Número de chamadas com exceções sem tratamento nesta operação em um segundo.</span><span class="sxs-lookup"><span data-stu-id="50dce-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="50dce-106">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="50dce-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="50dce-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="50dce-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="50dce-108">Esse contador é incrementado toda vez que há uma exceção sem tratamento nesta operação.</span><span class="sxs-lookup"><span data-stu-id="50dce-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50dce-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50dce-109">See also</span></span>

- [<span data-ttu-id="50dce-110">Especificando e lidando com falhas em contratos e serviços</span><span class="sxs-lookup"><span data-stu-id="50dce-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
