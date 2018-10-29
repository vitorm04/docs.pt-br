---
title: EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
ms.date: 09/14/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be9c858d7c76fdcc1b3e02485eb0b459f4e7555c
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583146"
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a><span data-ttu-id="c2941-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="c2941-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>

<span data-ttu-id="c2941-103">Os identificadores de espera de evento permitem que os threads sincronizem atividades sinalizando uns aos outros e aguardando sinais uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="c2941-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="c2941-104">Esses eventos de sincronização baseiam-se em identificadores de espera do sistema operacional e podem ser divididos em dois tipos: aqueles que são redefinidos automaticamente quando sinalizados e aqueles que são redefinidos manualmente.</span><span class="sxs-lookup"><span data-stu-id="c2941-104">These synchronization events are based on operating system wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
<span data-ttu-id="c2941-105">Os identificadores de espera de evento são úteis em muitos dos mesmos cenários de sincronização que a classe <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="c2941-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="c2941-106">Os identificadores de espera de evento geralmente são mais fáceis de usar do que os métodos <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> e <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>, e oferecem mais controle sobre a sinalização.</span><span class="sxs-lookup"><span data-stu-id="c2941-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="c2941-107">Os identificadores de espera de evento nomeado também podem ser usados para sincronizar as atividades em domínios de aplicativos e processos, enquanto que os monitores são locais a um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c2941-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2941-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c2941-108">In this section</span></span>

 [<span data-ttu-id="c2941-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="c2941-109">EventWaitHandle</span></span>](eventwaithandle.md)  
 <span data-ttu-id="c2941-110">A classe <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> pode representar eventos de redefinição automáticos ou manuais, bem como eventos locais ou eventos de sistema nomeado.</span><span class="sxs-lookup"><span data-stu-id="c2941-110">The <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="c2941-111">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="c2941-111">AutoResetEvent</span></span>](autoresetevent.md)  
 <span data-ttu-id="c2941-112">A classe <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> deriva de <xref:System.Threading.EventWaitHandle> e representa um evento local que é redefinido automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c2941-112">The <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that resets automatically.</span></span>  
  
 [<span data-ttu-id="c2941-113">ManualResetEvent e ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="c2941-113">ManualResetEvent and ManualResetEventSlim</span></span>](manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="c2941-114">A classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> deriva de <xref:System.Threading.EventWaitHandle> e representa um evento local que deve ser redefinido manualmente.</span><span class="sxs-lookup"><span data-stu-id="c2941-114">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="c2941-115">A classe <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> é uma versão leve e mais rápida, que pode ser usada para eventos dentro do mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="c2941-115">The <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="c2941-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="c2941-116">CountdownEvent</span></span>](countdownevent.md)  
 <span data-ttu-id="c2941-117">A classe <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> fornece uma maneira simplificada de implementar os padrões de paralelismo de bifurcação/junção no código que usa identificadores de espera.</span><span class="sxs-lookup"><span data-stu-id="c2941-117">The <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  

## <a name="see-also"></a><span data-ttu-id="c2941-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2941-118">See also</span></span>

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.Threading.Barrier?displayProperty=nameWithType>
- [<span data-ttu-id="c2941-119">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="c2941-119">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="c2941-120">Noções básicas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="c2941-120">Managed threading basics</span></span>](managed-threading-basics.md)
