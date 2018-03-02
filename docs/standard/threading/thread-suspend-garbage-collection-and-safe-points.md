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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fdd56763712dee9c6fa1f292eb3bbb2f0ccbf505
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="f8d44-102">Thread.Suspend, coleta de lixo e pontos seguros</span><span class="sxs-lookup"><span data-stu-id="f8d44-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="f8d44-103">Quando você chama <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> em um thread, o sistema observa que uma suspensão de thread foi solicitada e permite que o thread seja executado até atingir um ponto seguro antes de realmente suspendê-lo.</span><span class="sxs-lookup"><span data-stu-id="f8d44-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="f8d44-104">Um ponto seguro de um thread é um ponto da execução em que a coleta de lixo pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="f8d44-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="f8d44-105">Quando um ponto seguro é alcançado, o tempo de execução garante que o thread suspenso não fará mais progresso no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f8d44-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="f8d44-106">Um thread que é executado fora do código gerenciado está sempre seguro para a coleta de lixo e sua execução continua até que ele tente retomar a execução do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f8d44-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8d44-107">Para executar uma coleta de lixo, o tempo de execução deve suspender todos os threads exceto o thread que executa a coleta.</span><span class="sxs-lookup"><span data-stu-id="f8d44-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="f8d44-108">Cada thread deve ser colocado em um ponto seguro antes de poder ser suspenso.</span><span class="sxs-lookup"><span data-stu-id="f8d44-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d44-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8d44-109">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [<span data-ttu-id="f8d44-110">Threading</span><span class="sxs-lookup"><span data-stu-id="f8d44-110">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="f8d44-111">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="f8d44-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)
