---
title: Thread.Suspend, coleta de lixo e pontos seguros
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e47674ef8d1b1a7487e42765bcbce4b33cf98769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="11862-102">Thread.Suspend, coleta de lixo e pontos seguros</span><span class="sxs-lookup"><span data-stu-id="11862-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="11862-103">Quando você chama <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> em um thread, o sistema observa que a suspensão de um thread foi solicitada e permite a execução até que ele atingiu um ponto de segurança antes de realmente suspender o thread do thread.</span><span class="sxs-lookup"><span data-stu-id="11862-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="11862-104">Um ponto de segurança para um thread é um ponto em sua execução de coleta de lixo pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="11862-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="11862-105">Quando um ponto de segurança é atingido, o tempo de execução garante que o thread suspenso não fará qualquer progresso adicional em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="11862-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="11862-106">Um thread de execução fora do código gerenciado é sempre seguro para coleta de lixo e a execução continua até que ele tentará retomar a execução de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="11862-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11862-107">Para executar uma coleta de lixo, tempo de execução deve suspender todos os threads exceto o thread de execução de coleta.</span><span class="sxs-lookup"><span data-stu-id="11862-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="11862-108">Cada segmento deve ser colocado em um ponto de segurança antes de poder ser suspenso.</span><span class="sxs-lookup"><span data-stu-id="11862-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11862-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11862-109">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [<span data-ttu-id="11862-110">Threading</span><span class="sxs-lookup"><span data-stu-id="11862-110">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="11862-111">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="11862-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)
