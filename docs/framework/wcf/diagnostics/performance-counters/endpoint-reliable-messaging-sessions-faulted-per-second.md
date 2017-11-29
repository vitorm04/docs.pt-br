---
title: "Ponto de extremidade: sessões de transmissão de mensagens confiáveis com falha por segundo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0f4a8614420a11b31bf3b19fb03e13210f4590a8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="54541-102">Ponto de extremidade: sessões de transmissão de mensagens confiáveis com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="54541-102">Endpoint: Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="54541-103">Nome do contador: Sessões de mensagens confiáveis com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="54541-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="54541-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="54541-104">Description</span></span>  
 <span data-ttu-id="54541-105">Número de sessões de mensagens confiáveis com falha neste ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="54541-105">Number of reliable messaging sessions that are faulted at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="54541-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="54541-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="54541-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="54541-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
