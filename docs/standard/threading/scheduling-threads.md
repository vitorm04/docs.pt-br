---
title: Programando threads
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6bb715c11cc0d9b07e4ea8805ace7680ca92097c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="scheduling-threads"></a><span data-ttu-id="191a6-102">Programando threads</span><span class="sxs-lookup"><span data-stu-id="191a6-102">Scheduling Threads</span></span>
<span data-ttu-id="191a6-103">Cada thread tem uma prioridade atribuída.</span><span class="sxs-lookup"><span data-stu-id="191a6-103">Every thread has a thread priority assigned to it.</span></span> <span data-ttu-id="191a6-104">Threads criados dentro do Common Language Runtime inicialmente recebem a prioridade **ThreadPriority.Normal**.</span><span class="sxs-lookup"><span data-stu-id="191a6-104">Threads created within the common language runtime are initially assigned the priority of **ThreadPriority.Normal**.</span></span> <span data-ttu-id="191a6-105">Threads criados fora do Runtime retêm a prioridade que tinham antes de entrarem no ambiente gerenciado.</span><span class="sxs-lookup"><span data-stu-id="191a6-105">Threads created outside the runtime retain the priority they had before they entered the managed environment.</span></span> <span data-ttu-id="191a6-106">Você pode obter ou definir a prioridade de qualquer thread com a propriedade **Thread.Priority**.</span><span class="sxs-lookup"><span data-stu-id="191a6-106">You can get or set the priority of any thread with the **Thread.Priority** property.</span></span>  
  
 <span data-ttu-id="191a6-107">Threads são agendados para execução com base em sua prioridade.</span><span class="sxs-lookup"><span data-stu-id="191a6-107">Threads are scheduled for execution based on their priority.</span></span> <span data-ttu-id="191a6-108">Mesmo que os threads sejam executados no Runtime, todos são atribuídos frações de tempo do processador pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="191a6-108">Even though threads are executing within the runtime, all threads are assigned processor time slices by the operating system.</span></span> <span data-ttu-id="191a6-109">Os detalhes do algoritmo de agendamento usado para determinar a ordem na qual os threads são executados variam de acordo com cada sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="191a6-109">The details of the scheduling algorithm used to determine the order in which threads are executed varies with each operating system.</span></span> <span data-ttu-id="191a6-110">Em alguns sistemas operacionais, o thread com a prioridade mais alta (dos threads que podem ser executados) sempre é programada para ser executado primeiro.</span><span class="sxs-lookup"><span data-stu-id="191a6-110">Under some operating systems, the thread with the highest priority (of those threads that can be executed) is always scheduled to run first.</span></span> <span data-ttu-id="191a6-111">Se vários threads com a mesma prioridade estiverem disponíveis, o agendador percorre os threads com essa prioridade, fornecendo uma fração de tempo fixa na qual executar cada thread.</span><span class="sxs-lookup"><span data-stu-id="191a6-111">If multiple threads with the same priority are all available, the scheduler cycles through the threads at that priority, giving each thread a fixed time slice in which to execute.</span></span> <span data-ttu-id="191a6-112">Enquanto houver um thread com uma prioridade mais alta estiver disponível para execução, threads com prioridades inferiores não serão executados.</span><span class="sxs-lookup"><span data-stu-id="191a6-112">As long as a thread with a higher priority is available to run, lower priority threads do not get to execute.</span></span> <span data-ttu-id="191a6-113">Quando não houver mais nenhum threads executável com determinada prioridade, o agendador passará para a próxima prioridade mais alta e agendará a execução dos threads com essa prioridade.</span><span class="sxs-lookup"><span data-stu-id="191a6-113">When there are no more runnable threads at a given priority, the scheduler moves to the next lower priority and schedules the threads at that priority for execution.</span></span> <span data-ttu-id="191a6-114">Se um thread de prioridade mais alta se tornar executável, o thread de prioridade mais baixo será ignorado e o thread de prioridade mais alta poderá ser executado novamente.</span><span class="sxs-lookup"><span data-stu-id="191a6-114">If a higher priority thread becomes runnable, the lower priority thread is preempted and the higher priority thread is allowed to execute once again.</span></span> <span data-ttu-id="191a6-115">Além disso, o sistema operacional também poderá ajustar as prioridades de threads dinamicamente conforme a interface de usuário do aplicativo é movida entre o primeiro e segundo plano.</span><span class="sxs-lookup"><span data-stu-id="191a6-115">On top of all that, the operating system can also adjust thread priorities dynamically as an application's user interface is moved between foreground and background.</span></span> <span data-ttu-id="191a6-116">Outros sistemas operacionais podem optar por usar um algoritmo de programação diferente.</span><span class="sxs-lookup"><span data-stu-id="191a6-116">Other operating systems might choose to use a different scheduling algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="191a6-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="191a6-117">See Also</span></span>  
 [<span data-ttu-id="191a6-118">Usando threads e threading</span><span class="sxs-lookup"><span data-stu-id="191a6-118">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 [<span data-ttu-id="191a6-119">Threading gerenciado e não gerenciado no Windows</span><span class="sxs-lookup"><span data-stu-id="191a6-119">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
