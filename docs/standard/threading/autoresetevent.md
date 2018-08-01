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
ms.openlocfilehash: c1785ce223f0dcd4da7ea6ef9fa3a3e897a39dca
ms.sourcegitcommit: dc02d7d95f1e3efcc7166eaf431b0ec0dc9d8dca
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37143505"
---
# <a name="autoresetevent"></a><span data-ttu-id="87c71-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="87c71-102">AutoResetEvent</span></span>
<span data-ttu-id="87c71-103">A classe <xref:System.Threading.AutoResetEvent> representa um evento de identificador de espera local que redefine automaticamente quando sinalizado, após o lançamento de um único thread de espera.</span><span class="sxs-lookup"><span data-stu-id="87c71-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="87c71-104">Essa classe representa um caso especial de sua classe base, <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="87c71-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="87c71-105">Consulte a documentação conceitual de [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) para conhecer o uso e os recursos de eventos de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="87c71-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="87c71-106">Um objeto <xref:System.Threading.AutoResetEvent> é redefinido automaticamente para ser não sinalizado pelo sistema depois que um único thread de espera for liberado.</span><span class="sxs-lookup"><span data-stu-id="87c71-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="87c71-107">Se nenhum thread estiver aguardando, o estado do objeto de evento permanecerá sinalizado.</span><span class="sxs-lookup"><span data-stu-id="87c71-107">If no threads are waiting, the event object's state remains signaled.</span></span> <span data-ttu-id="87c71-108"><xref:System.Threading.AutoResetEvent> corresponde a uma chamada Win32 `CreateEvent`, especificando `false` para o argumento `bManualReset`.</span><span class="sxs-lookup"><span data-stu-id="87c71-108"><xref:System.Threading.AutoResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `false` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="87c71-109">Para obter um exemplo que usa <xref:System.Threading.AutoResetEvent>, confira <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="87c71-109">For an example that uses <xref:System.Threading.AutoResetEvent>, see <xref:System.Threading.Monitor>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c71-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87c71-110">See Also</span></span>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="87c71-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="87c71-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [<span data-ttu-id="87c71-112">Threading</span><span class="sxs-lookup"><span data-stu-id="87c71-112">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="87c71-113">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="87c71-113">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="87c71-114">Identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="87c71-114">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
