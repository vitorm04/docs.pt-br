---
title: Mensagens confiáveis do sistema de mensagens descartadas por segundo
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 7722b32f99b302c5c272e095033879c9e04c7ee1
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664443"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="070f3-102">Mensagens confiáveis do sistema de mensagens descartadas por segundo</span><span class="sxs-lookup"><span data-stu-id="070f3-102">Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="070f3-103">Nome do contador: Sessões de Reliable Messaging eliminados por segundo.</span><span class="sxs-lookup"><span data-stu-id="070f3-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="070f3-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="070f3-104">Description</span></span>  
 <span data-ttu-id="070f3-105">Número total de mensagens confiáveis que foram ignoradas neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="070f3-105">Total number of reliable messaging messages that have been dropped in this service in a second.</span></span>  
  
 <span data-ttu-id="070f3-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="070f3-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="070f3-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="070f3-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
