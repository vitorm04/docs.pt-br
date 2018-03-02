---
title: EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6c545f9ebc924c0a12ee2e76fdb6c725c25e2353
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a><span data-ttu-id="d9ed7-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="d9ed7-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>
<span data-ttu-id="d9ed7-103">Os identificadores de espera de evento permitem que os threads sincronizem atividades sinalizando uns aos outros e aguardando sinais uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="d9ed7-104">Esses eventos de sincronização baseiam-se em identificadores de espera do Win32 e podem ser divididos em dois tipos: aqueles que são redefinidos automaticamente quando sinalizados e aqueles que são redefinidos manualmente.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-104">These synchronization events are based on Win32 wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
 <span data-ttu-id="d9ed7-105">Os identificadores de espera de evento são úteis em muitos dos mesmos cenários de sincronização que a classe <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="d9ed7-106">Os identificadores de espera de evento geralmente são mais fáceis de usar do que os métodos <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> e <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>, e oferecem mais controle sobre a sinalização.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="d9ed7-107">Os identificadores de espera de evento nomeado também podem ser usados para sincronizar as atividades em domínios de aplicativos e processos, enquanto que os monitores são locais a um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d9ed7-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d9ed7-108">In This Section</span></span>  
 [<span data-ttu-id="d9ed7-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="d9ed7-109">EventWaitHandle</span></span>](../../../docs/standard/threading/eventwaithandle.md)  
 <span data-ttu-id="d9ed7-110">A classe <xref:System.Threading.EventWaitHandle> pode representar eventos de redefinição automáticos ou manuais, bem como eventos locais ou eventos de sistema nomeado.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-110">The <xref:System.Threading.EventWaitHandle> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="d9ed7-111">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="d9ed7-111">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 <span data-ttu-id="d9ed7-112">A classe <xref:System.Threading.AutoResetEvent> deriva de <xref:System.Threading.EventWaitHandle> e representa um evento local que é redefinido automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-112">The <xref:System.Threading.AutoResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that resets automatically.</span></span>  
  
 [<span data-ttu-id="d9ed7-113">ManualResetEvent e ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="d9ed7-113">ManualResetEvent and ManualResetEventSlim</span></span>](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="d9ed7-114">A classe <xref:System.Threading.ManualResetEvent> deriva de <xref:System.Threading.EventWaitHandle> e representa um evento local que deve ser redefinido manualmente.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-114">The <xref:System.Threading.ManualResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="d9ed7-115">A classe <xref:System.Threading.ManualResetEventSlim> é uma versão leve e mais rápida, que pode ser usada para eventos dentro do mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-115">The <xref:System.Threading.ManualResetEventSlim> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="d9ed7-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="d9ed7-116">CountdownEvent</span></span>](../../../docs/standard/threading/countdownevent.md)  
 <span data-ttu-id="d9ed7-117">A classe <xref:System.Threading.CountdownEvent> fornece uma maneira simplificada de implementar os padrões de paralelismo de bifurcação/junção no código que usa identificadores de espera.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-117">The <xref:System.Threading.CountdownEvent> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d9ed7-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="d9ed7-118">Related Sections</span></span>  
 [<span data-ttu-id="d9ed7-119">Identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="d9ed7-119">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="d9ed7-120">A classe <xref:System.Threading.WaitHandle> é a classe base para as classes <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore> e <xref:System.Threading.Mutex>.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-120">The <xref:System.Threading.WaitHandle> class is the base class for the <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, and <xref:System.Threading.Mutex> classes.</span></span> <span data-ttu-id="d9ed7-121">Contém métodos estáticos como <xref:System.Threading.WaitHandle.SignalAndWait%2A> e <xref:System.Threading.WaitHandle.WaitAll%2A> que são úteis quando se trabalha com todos os tipos de identificadores de espera.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-121">It contains static methods such as <xref:System.Threading.WaitHandle.SignalAndWait%2A> and <xref:System.Threading.WaitHandle.WaitAll%2A> that are useful when working with all types of wait handles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9ed7-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9ed7-122">See Also</span></span>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [<span data-ttu-id="d9ed7-123">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="d9ed7-123">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="d9ed7-124">Noções básicas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="d9ed7-124">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)
