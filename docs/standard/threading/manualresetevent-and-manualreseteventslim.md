---
title: ManualResetEvent e ManualResetEventSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 864c39aa6673537d66d8402896bce5b4fa92e5ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602437"
---
# <a name="manualresetevent-and-manualreseteventslim"></a><span data-ttu-id="61323-102">ManualResetEvent e ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="61323-102">ManualResetEvent and ManualResetEventSlim</span></span>
<span data-ttu-id="61323-103">A classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> representa um evento de identificador de espera local que deve ser redefinido manualmente após ser sinalizado.</span><span class="sxs-lookup"><span data-stu-id="61323-103">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class represents a local wait handle event that must be reset manually after it is signaled.</span></span> <span data-ttu-id="61323-104">Essa classe representa um caso especial de sua classe base, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="61323-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span></span> <span data-ttu-id="61323-105">Veja a documentação conceitual de [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) para conhecer o uso e os recursos de eventos de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="61323-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of manual reset events.</span></span>  
  
 <span data-ttu-id="61323-106">Um objeto <xref:System.Threading.ManualResetEvent> permanece sinalizado até que seu método <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> seja chamado.</span><span class="sxs-lookup"><span data-stu-id="61323-106">A <xref:System.Threading.ManualResetEvent> object remains signaled until its <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="61323-107">Qualquer número de threads em espera ou threads que esperam no evento depois de sinalizado, podem ser liberados enquanto o estado do objeto é sinalizado.</span><span class="sxs-lookup"><span data-stu-id="61323-107">Any number of waiting threads, or threads that wait on the event after it has been signaled, can be released while the object's state is signaled.</span></span>
  
 <span data-ttu-id="61323-108">No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar a classe <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> para melhorar o desempenho quando se espera que os tempos de espera sejam muito curtos, e quando o evento não cruza um limite de processo.</span><span class="sxs-lookup"><span data-stu-id="61323-108">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class for better performance when wait times are expected to be very short, and when the event does not cross a process boundary.</span></span> <span data-ttu-id="61323-109">O <xref:System.Threading.ManualResetEventSlim> usa a rotação ocupada por um curto período enquanto aguarda a sinalização do evento.</span><span class="sxs-lookup"><span data-stu-id="61323-109"><xref:System.Threading.ManualResetEventSlim> uses busy spinning for a short time while it waits for the event to become signaled.</span></span> <span data-ttu-id="61323-110">Quando os tempos de espera são curtos, a rotação pode ser muito menos dispendiosa do que a espera usando os identificadores de espera.</span><span class="sxs-lookup"><span data-stu-id="61323-110">When wait times are short, spinning can be much less expensive than waiting by using wait handles.</span></span> <span data-ttu-id="61323-111">No entanto, se o evento não for sinalizado dentro de um determinado período de tempo, <xref:System.Threading.ManualResetEventSlim> recorre a uma espera de identificador de evento regular.</span><span class="sxs-lookup"><span data-stu-id="61323-111">However, if the event does not become signaled within a certain period of time, <xref:System.Threading.ManualResetEventSlim> resorts to a regular event handle wait.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61323-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61323-112">See also</span></span>

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [<span data-ttu-id="61323-113">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="61323-113">AutoResetEvent</span></span>](autoresetevent.md)
- [<span data-ttu-id="61323-114">SpinWait</span><span class="sxs-lookup"><span data-stu-id="61323-114">SpinWait</span></span>](spinwait.md)
- [<span data-ttu-id="61323-115">Semaphore e SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="61323-115">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)
- [<span data-ttu-id="61323-116">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="61323-116">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
- [<span data-ttu-id="61323-117">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="61323-117">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="61323-118">Threading</span><span class="sxs-lookup"><span data-stu-id="61323-118">Threading</span></span>](index.md)
