---
title: AutoResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70af739bdb90a70a1319354b4964c261e432912b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729938"
---
# <a name="autoresetevent"></a><span data-ttu-id="73358-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="73358-102">AutoResetEvent</span></span>
<span data-ttu-id="73358-103">A classe <xref:System.Threading.AutoResetEvent> representa um evento de identificador de espera local que redefine automaticamente quando sinalizado, após o lançamento de um único thread de espera.</span><span class="sxs-lookup"><span data-stu-id="73358-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="73358-104">Essa classe representa um caso especial de sua classe base, <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="73358-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="73358-105">Consulte a documentação conceitual de [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) para conhecer o uso e os recursos de eventos de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="73358-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="73358-106">Um objeto <xref:System.Threading.AutoResetEvent> é redefinido automaticamente para ser não sinalizado pelo sistema depois que um único thread de espera for liberado.</span><span class="sxs-lookup"><span data-stu-id="73358-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="73358-107">Se nenhum thread estiver aguardando, o estado do objeto de evento permanecerá sinalizado.</span><span class="sxs-lookup"><span data-stu-id="73358-107">If no threads are waiting, the event object's state remains signaled.</span></span>
  
 <span data-ttu-id="73358-108">Para obter um exemplo que usa <xref:System.Threading.AutoResetEvent>, confira <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="73358-108">For an example that uses <xref:System.Threading.AutoResetEvent>, see <xref:System.Threading.Monitor>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73358-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73358-109">See also</span></span>

- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [<span data-ttu-id="73358-110">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="73358-110">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
- [<span data-ttu-id="73358-111">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="73358-111">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="73358-112">Threading</span><span class="sxs-lookup"><span data-stu-id="73358-112">Threading</span></span>](index.md)
