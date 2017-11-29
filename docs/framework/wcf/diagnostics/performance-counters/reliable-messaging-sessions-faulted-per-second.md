---
title: "Sessões de Mensagens Confiáveis com Falha por Segundo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23aa57da18072b9c3055079c9d069b282f50c99a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="87fb0-102">Sessões de Mensagens Confiáveis com Falha por Segundo</span><span class="sxs-lookup"><span data-stu-id="87fb0-102">Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="87fb0-103">Nome do contador: Sessões de mensagens confiáveis com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="87fb0-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="87fb0-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="87fb0-104">Description</span></span>  
 <span data-ttu-id="87fb0-105">Número de sessões de mensagens confiáveis com falha neste serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="87fb0-105">Number of reliable messaging sessions that are faulted in this service in a second.</span></span>  
  
 <span data-ttu-id="87fb0-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="87fb0-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="87fb0-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="87fb0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
