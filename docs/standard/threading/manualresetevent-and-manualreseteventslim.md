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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b90a84cf87c6c64d48d89840e2213d83b2e39d44
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="manualresetevent-and-manualreseteventslim"></a><span data-ttu-id="a6e46-102">ManualResetEvent e ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="a6e46-102">ManualResetEvent and ManualResetEventSlim</span></span>
<span data-ttu-id="a6e46-103">A classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> representa um evento de identificador de espera local que deve ser redefinido manualmente após ser sinalizado.</span><span class="sxs-lookup"><span data-stu-id="a6e46-103">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class represents a local wait handle event that must be reset manually after it is signaled.</span></span> <span data-ttu-id="a6e46-104">Essa classe representa um caso especial de sua classe base, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6e46-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a6e46-105">Veja a documentação conceitual de [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) para conhecer o uso e os recursos de eventos de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="a6e46-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of manual reset events.</span></span>  
  
 <span data-ttu-id="a6e46-106">Um objeto <xref:System.Threading.ManualResetEvent> permanece sinalizado até que seu método <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> seja chamado.</span><span class="sxs-lookup"><span data-stu-id="a6e46-106">A <xref:System.Threading.ManualResetEvent> object remains signaled until its <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="a6e46-107">Qualquer número de threads em espera ou threads que esperam no evento depois de sinalizado, podem ser liberados enquanto o estado do objeto é sinalizado.</span><span class="sxs-lookup"><span data-stu-id="a6e46-107">Any number of waiting threads, or threads that wait on the event after it has been signaled, can be released while the object's state is signaled.</span></span> <span data-ttu-id="a6e46-108"><xref:System.Threading.ManualResetEvent> corresponde a uma chamada Win32 `CreateEvent`, especificando `true` para o argumento `bManualReset`.</span><span class="sxs-lookup"><span data-stu-id="a6e46-108"><xref:System.Threading.ManualResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `true` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="a6e46-109">No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar a classe <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> para melhorar o desempenho quando se espera que os tempos de espera sejam muito curtos, e quando o evento não cruza um limite de processo.</span><span class="sxs-lookup"><span data-stu-id="a6e46-109">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class for better performance when wait times are expected to be very short, and when the event does not cross a process boundary.</span></span> <span data-ttu-id="a6e46-110">O <xref:System.Threading.ManualResetEventSlim> usa a rotação ocupada por um curto período enquanto aguarda a sinalização do evento.</span><span class="sxs-lookup"><span data-stu-id="a6e46-110"><xref:System.Threading.ManualResetEventSlim> uses busy spinning for a short time while it waits for the event to become signaled.</span></span> <span data-ttu-id="a6e46-111">Quando os tempos de espera são curtos, a rotação pode ser muito menos dispendiosa do que a espera usando os identificadores de espera.</span><span class="sxs-lookup"><span data-stu-id="a6e46-111">When wait times are short, spinning can be much less expensive than waiting by using wait handles.</span></span> <span data-ttu-id="a6e46-112">No entanto, se o evento não for sinalizado dentro de um determinado período de tempo, <xref:System.Threading.ManualResetEventSlim> recorre a uma espera de identificador de evento regular.</span><span class="sxs-lookup"><span data-stu-id="a6e46-112">However, if the event does not become signaled within a certain period of time, <xref:System.Threading.ManualResetEventSlim> resorts to a regular event handle wait.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e46-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6e46-113">See Also</span></span>  
 [<span data-ttu-id="a6e46-114">Threading</span><span class="sxs-lookup"><span data-stu-id="a6e46-114">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="a6e46-115">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="a6e46-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="a6e46-116">Identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="a6e46-116">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [<span data-ttu-id="a6e46-117">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="a6e46-117">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 [<span data-ttu-id="a6e46-118">SpinWait</span><span class="sxs-lookup"><span data-stu-id="a6e46-118">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="a6e46-119">Semaphore e SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="a6e46-119">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
