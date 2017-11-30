---
title: AutoResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 69d16e8c6491b4c66ab5a5452762e73172ebbb77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="autoresetevent"></a><span data-ttu-id="4da0a-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="4da0a-102">AutoResetEvent</span></span>
<span data-ttu-id="4da0a-103">O <xref:System.Threading.AutoResetEvent> classe representa um evento de identificador de espera local redefine automaticamente quando sinalizado, após o lançamento de um único thread de espera.</span><span class="sxs-lookup"><span data-stu-id="4da0a-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="4da0a-104">Essa classe representa um caso especial de sua classe base, <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="4da0a-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="4da0a-105">Consulte o [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) documentação conceitual para o uso e recursos de eventos de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="4da0a-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="4da0a-106">Um <xref:System.Threading.AutoResetEvent> objeto é redefinido automaticamente para não sinalizado pelo sistema depois que um único thread de espera foi liberado.</span><span class="sxs-lookup"><span data-stu-id="4da0a-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="4da0a-107">Se nenhum segmento estiver aguardando, o estado do objeto de evento permanece sinalizado.</span><span class="sxs-lookup"><span data-stu-id="4da0a-107">If no threads are waiting, the event object's state remains signaled.</span></span> <span data-ttu-id="4da0a-108"><xref:System.Threading.AutoResetEvent>corresponde a um Win32 `CreateEvent` chamar, especificando `false` para o `bManualReset` argumento.</span><span class="sxs-lookup"><span data-stu-id="4da0a-108"><xref:System.Threading.AutoResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `false` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="4da0a-109">Para obter um exemplo que usa <xref:System.Threading.AutoResetEvent>, consulte [Monitor](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span><span class="sxs-lookup"><span data-stu-id="4da0a-109">For an example that uses <xref:System.Threading.AutoResetEvent>, see [Monitor](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da0a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4da0a-110">See Also</span></span>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="4da0a-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="4da0a-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [<span data-ttu-id="4da0a-112">Threading</span><span class="sxs-lookup"><span data-stu-id="4da0a-112">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="4da0a-113">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="4da0a-113">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="4da0a-114">Identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="4da0a-114">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
