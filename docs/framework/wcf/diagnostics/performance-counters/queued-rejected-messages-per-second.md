---
title: Mensagens em fila rejeitadas por segundo
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: 31091c6c9dd04ecd7294f69f9611f25e401df724
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473439"
---
# <a name="queued-rejected-messages-per-second"></a><span data-ttu-id="f65a5-102">Mensagens em fila rejeitadas por segundo</span><span class="sxs-lookup"><span data-stu-id="f65a5-102">Queued Rejected Messages Per Second</span></span>
<span data-ttu-id="f65a5-103">Nome do contador: Na fila de mensagens rejeitadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="f65a5-103">Counter Name: Queued Messages Rejected Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f65a5-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="f65a5-104">Description</span></span>  
 <span data-ttu-id="f65a5-105">Número de mensagens que foram rejeitadas pelo transporte em fila neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="f65a5-105">Number of messages that are rejected by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="f65a5-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="f65a5-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f65a5-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="f65a5-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
