---
title: Eventos ETW no .NET Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework ETW events
- ETW events in the .NET Framework
ms.assetid: d186276f-6afb-4dfd-bf3c-4251edc2c299
caps.latest.revision: 9
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 53bd8bce147e8939a975f483223db08296707e3d
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="etw-events-in-the-net-framework"></a><span data-ttu-id="264c3-102">Eventos ETW no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="264c3-102">ETW Events in the .NET Framework</span></span>
<span data-ttu-id="264c3-103">O rastreamento de eventos para Windows (ETW) é um sistema de rastreamento de alto desempenho, baixa sobrecarga e escalonável fornecido pelos sistemas operacionais Windows.</span><span class="sxs-lookup"><span data-stu-id="264c3-103">Event tracing for Windows (ETW) is a high-performance, low-overhead, scalable tracing system provided by Windows operating systems.</span></span> <span data-ttu-id="264c3-104">Ele complementa o suporte de depuração e criação de perfil fornecido pelo .NET Framework e pode ser usado para solucionar problemas de uma variedade de cenários.</span><span class="sxs-lookup"><span data-stu-id="264c3-104">It supplements the profiling and debugging support provided by the .NET Framework and can be used to troubleshoot a variety of scenarios.</span></span> <span data-ttu-id="264c3-105">Para obter informações gerais sobre o ETW, consulte [Melhorar o ajuste de depuração e desempenho com o ETW](http://go.microsoft.com/fwlink/?LinkID=161142) na Biblioteca MSDN.</span><span class="sxs-lookup"><span data-stu-id="264c3-105">For general information about ETW, see [Improve Debugging and Performance Tuning with ETW](http://go.microsoft.com/fwlink/?LinkID=161142) in the MSDN Library.</span></span>  
  
 <span data-ttu-id="264c3-106">No .NET Framework, o rastreamento de eventos ETW está disponível para o CLR (Common Language Runtime), a [Biblioteca de Paralelismo de Tarefas](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) e o [PLINQ (LINQ Paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="264c3-106">In the .NET Framework, ETW event tracing is available for the common language runtime (CLR), the [Task Parallel Library](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md), and [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="264c3-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="264c3-107">In This Section</span></span>  
 [<span data-ttu-id="264c3-108">Eventos ETW na biblioteca de paralelismo de tarefas e no PLINQ</span><span class="sxs-lookup"><span data-stu-id="264c3-108">ETW Events in Task Parallel Library and PLINQ</span></span>](../../../docs/framework/performance/etw-events-in-task-parallel-library-and-plinq.md)  
 <span data-ttu-id="264c3-109">Descreve como criar o perfil de um código do aplicativo paralelo.</span><span class="sxs-lookup"><span data-stu-id="264c3-109">Describes how to profile parallel application code.</span></span>  
  
 [<span data-ttu-id="264c3-110">Eventos ETW no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="264c3-110">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)  
 <span data-ttu-id="264c3-111">Descreve como os eventos CLR ETW complementam o suporte de depuração e criação de perfil fornecido pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="264c3-111">Describes how CLR ETW events supplement the profiling and debugging support provided by the common language runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="264c3-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="264c3-112">See Also</span></span>  
 <span data-ttu-id="264c3-113">[Eventos de CLR ETW](../../../docs/framework/performance/clr-etw-events.md) </span><span class="sxs-lookup"><span data-stu-id="264c3-113">[CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) </span></span>  
 <span data-ttu-id="264c3-114">[TPL (Biblioteca de Paralelismo de Tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) </span><span class="sxs-lookup"><span data-stu-id="264c3-114">[Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) </span></span>  
 [<span data-ttu-id="264c3-115">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="264c3-115">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)

