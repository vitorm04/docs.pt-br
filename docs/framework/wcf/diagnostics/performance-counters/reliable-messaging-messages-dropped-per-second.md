---
title: Mensagens confiáveis do sistema de mensagens descartadas por segundo
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 9a87ec509b19f0c566b50ae3672a6c3d2940ee12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474188"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="9ef3a-102">Mensagens confiáveis do sistema de mensagens descartadas por segundo</span><span class="sxs-lookup"><span data-stu-id="9ef3a-102">Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="9ef3a-103">Nome do contador: Sessões de mensagens confiáveis descartadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="9ef3a-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9ef3a-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ef3a-104">Description</span></span>  
 <span data-ttu-id="9ef3a-105">Número total de mensagens confiáveis foram descartadas neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="9ef3a-105">Total number of reliable messaging messages that have been dropped in this service in a second.</span></span>  
  
 <span data-ttu-id="9ef3a-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="9ef3a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9ef3a-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="9ef3a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
