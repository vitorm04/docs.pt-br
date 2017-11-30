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
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0bcb27ed9c8981665a50c129dfbd824c9612f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a><span data-ttu-id="c531c-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="c531c-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>
<span data-ttu-id="c531c-103">Identificadores de espera de eventos permitem que os threads para sincronizar as atividades de sinalização entre si e aguardando sinais uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="c531c-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="c531c-104">Esses eventos de sincronização são baseados em identificadores de espera do Win32 e podem ser divididos em dois tipos: aqueles que redefinir automaticamente quando sinalizado e aqueles que são redefinidos manualmente.</span><span class="sxs-lookup"><span data-stu-id="c531c-104">These synchronization events are based on Win32 wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
 <span data-ttu-id="c531c-105">Identificadores de espera de eventos são úteis para muitos dos cenários de sincronização mesmo como o <xref:System.Threading.Monitor> classe.</span><span class="sxs-lookup"><span data-stu-id="c531c-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="c531c-106">Identificadores de espera de eventos geralmente são mais fáceis de usar do que o <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> e <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> métodos e oferecem mais controle sobre a sinalização.</span><span class="sxs-lookup"><span data-stu-id="c531c-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="c531c-107">Identificadores de espera de evento nomeado também podem ser usados para sincronizar as atividades em domínios de aplicativos e processos, enquanto que os monitores são locais para um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c531c-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c531c-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c531c-108">In This Section</span></span>  
 [<span data-ttu-id="c531c-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="c531c-109">EventWaitHandle</span></span>](../../../docs/standard/threading/eventwaithandle.md)  
 <span data-ttu-id="c531c-110">O <xref:System.Threading.EventWaitHandle> classe pode representar qualquer automático ou manual redefinir os eventos e o local ou chamada de eventos do sistema.</span><span class="sxs-lookup"><span data-stu-id="c531c-110">The <xref:System.Threading.EventWaitHandle> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="c531c-111">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="c531c-111">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 <span data-ttu-id="c531c-112">O <xref:System.Threading.AutoResetEvent> classe derivada de <xref:System.Threading.EventWaitHandle> e representa um evento local redefine automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c531c-112">The <xref:System.Threading.AutoResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that resets automatically.</span></span>  
  
 [<span data-ttu-id="c531c-113">ManualResetEvent e ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="c531c-113">ManualResetEvent and ManualResetEventSlim</span></span>](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="c531c-114">O <xref:System.Threading.ManualResetEvent> classe derivada de <xref:System.Threading.EventWaitHandle> e representa um evento local deverá ser redefinido manualmente.</span><span class="sxs-lookup"><span data-stu-id="c531c-114">The <xref:System.Threading.ManualResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="c531c-115">O <xref:System.Threading.ManualResetEventSlim> classe é uma versão leve e mais rápida, que pode ser usada para eventos dentro do mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="c531c-115">The <xref:System.Threading.ManualResetEventSlim> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="c531c-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="c531c-116">CountdownEvent</span></span>](../../../docs/standard/threading/countdownevent.md)  
 <span data-ttu-id="c531c-117">O <xref:System.Threading.CountdownEvent> classe fornece uma maneira simplificada para implementar os padrões de paralelismo de bifurcação/junção no código que usa identificadores de espera.</span><span class="sxs-lookup"><span data-stu-id="c531c-117">The <xref:System.Threading.CountdownEvent> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c531c-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c531c-118">Related Sections</span></span>  
 [<span data-ttu-id="c531c-119">Identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="c531c-119">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="c531c-120">O <xref:System.Threading.WaitHandle> classe é a classe base para o <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, e <xref:System.Threading.Mutex> classes.</span><span class="sxs-lookup"><span data-stu-id="c531c-120">The <xref:System.Threading.WaitHandle> class is the base class for the <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, and <xref:System.Threading.Mutex> classes.</span></span> <span data-ttu-id="c531c-121">Contém métodos estáticos como <xref:System.Threading.WaitHandle.SignalAndWait%2A> e <xref:System.Threading.WaitHandle.WaitAll%2A> que são úteis ao trabalhar com todos os tipos de identificadores de espera.</span><span class="sxs-lookup"><span data-stu-id="c531c-121">It contains static methods such as <xref:System.Threading.WaitHandle.SignalAndWait%2A> and <xref:System.Threading.WaitHandle.WaitAll%2A> that are useful when working with all types of wait handles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c531c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c531c-122">See Also</span></span>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [<span data-ttu-id="c531c-123">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="c531c-123">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="c531c-124">Noções básicas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="c531c-124">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)
