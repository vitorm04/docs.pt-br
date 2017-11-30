---
title: ManualResetEvent e ManualResetEventSlim
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f663dd17b063f77e2f9ce6bd4bbd0f8859ba4116
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="manualresetevent-and-manualreseteventslim"></a><span data-ttu-id="71d50-102">ManualResetEvent e ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="71d50-102">ManualResetEvent and ManualResetEventSlim</span></span>
<span data-ttu-id="71d50-103">O <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> classe representa um evento de identificador de espera local deve ser redefinido manualmente depois que ela for sinalizada.</span><span class="sxs-lookup"><span data-stu-id="71d50-103">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class represents a local wait handle event that must be reset manually after it is signaled.</span></span> <span data-ttu-id="71d50-104">Essa classe representa um caso especial de sua classe base, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="71d50-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span></span> <span data-ttu-id="71d50-105">Consulte o [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) eventos de redefinição de documentação conceitual para o uso e recursos de manual.</span><span class="sxs-lookup"><span data-stu-id="71d50-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of manual reset events.</span></span>  
  
 <span data-ttu-id="71d50-106">Um <xref:System.Threading.ManualResetEvent> objeto permanece sinalizado até que seu <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> método é chamado.</span><span class="sxs-lookup"><span data-stu-id="71d50-106">A <xref:System.Threading.ManualResetEvent> object remains signaled until its <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="71d50-107">Qualquer número de threads ou threads que esperar o evento depois que ela foi sinalizada, de espera pode ser liberado enquanto o estado do objeto é sinalizado.</span><span class="sxs-lookup"><span data-stu-id="71d50-107">Any number of waiting threads, or threads that wait on the event after it has been signaled, can be released while the object's state is signaled.</span></span> <span data-ttu-id="71d50-108"><xref:System.Threading.ManualResetEvent>corresponde a um Win32 `CreateEvent` chamar, especificando `true` para o `bManualReset` argumento.</span><span class="sxs-lookup"><span data-stu-id="71d50-108"><xref:System.Threading.ManualResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `true` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="71d50-109">No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar o <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> de classe para melhorar o desempenho quando os tempos de espera devem ser muito curto, e quando o evento não se cruza um limite de processo.</span><span class="sxs-lookup"><span data-stu-id="71d50-109">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class for better performance when wait times are expected to be very short, and when the event does not cross a process boundary.</span></span> <span data-ttu-id="71d50-110"><xref:System.Threading.ManualResetEventSlim>usa ocupado girando por um curto período enquanto aguarda o evento tornou-se sinalizado.</span><span class="sxs-lookup"><span data-stu-id="71d50-110"><xref:System.Threading.ManualResetEventSlim> uses busy spinning for a short time while it waits for the event to become signaled.</span></span> <span data-ttu-id="71d50-111">Quando os tempos de espera são curtos, girando pode ser muito menos dispendioso que espera usando identificadores de espera.</span><span class="sxs-lookup"><span data-stu-id="71d50-111">When wait times are short, spinning can be much less expensive than waiting by using wait handles.</span></span> <span data-ttu-id="71d50-112">No entanto, se o evento não ficar sinalizado dentro de um determinado período de tempo, <xref:System.Threading.ManualResetEventSlim> recorre uma espera de identificador de evento regular.</span><span class="sxs-lookup"><span data-stu-id="71d50-112">However, if the event does not become signaled within a certain period of time, <xref:System.Threading.ManualResetEventSlim> resorts to a regular event handle wait.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d50-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71d50-113">See Also</span></span>  
 [<span data-ttu-id="71d50-114">Threading</span><span class="sxs-lookup"><span data-stu-id="71d50-114">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="71d50-115">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="71d50-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="71d50-116">Identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="71d50-116">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [<span data-ttu-id="71d50-117">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="71d50-117">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 [<span data-ttu-id="71d50-118">SpinWait</span><span class="sxs-lookup"><span data-stu-id="71d50-118">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="71d50-119">Semaphore e SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="71d50-119">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
