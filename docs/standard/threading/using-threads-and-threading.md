---
title: Usando threads e threading
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5bed13950a29cfa787ef8c9eb2608c6d74dfd49f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="using-threads-and-threading"></a><span data-ttu-id="c8d31-102">Usando threads e threading</span><span class="sxs-lookup"><span data-stu-id="c8d31-102">Using Threads and Threading</span></span>
<span data-ttu-id="c8d31-103">Os tópicos nesta seção abordam a criação e gerenciamento de threads gerenciados, como transmitir dados para threads gerenciados e obter resultados e como destruir threads e tratar um <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="c8d31-103">The topics in this section discuss the creation and management of managed threads, how to pass data to managed threads and get results back, and how to destroy threads and handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8d31-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c8d31-104">In This Section</span></span>  
 [<span data-ttu-id="c8d31-105">Criando threads e passando dados na hora de início</span><span class="sxs-lookup"><span data-stu-id="c8d31-105">Creating Threads and Passing Data at Start Time</span></span>](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 <span data-ttu-id="c8d31-106">Discute e demonstra a criação de threads gerenciados, incluindo como transmitir dados para novos threads e como obter dados de volta.</span><span class="sxs-lookup"><span data-stu-id="c8d31-106">Discusses and demonstrates the creation of managed threads, including how to pass data to new threads and how to get data back.</span></span>  
  
 [<span data-ttu-id="c8d31-107">Pausando e retomando threads</span><span class="sxs-lookup"><span data-stu-id="c8d31-107">Pausing and Resuming Threads</span></span>](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 <span data-ttu-id="c8d31-108">Discute as implicações de pausar e retomar os threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="c8d31-108">Discusses the ramifications of pausing and resuming managed threads.</span></span>  
  
 [<span data-ttu-id="c8d31-109">Destruindo threads</span><span class="sxs-lookup"><span data-stu-id="c8d31-109">Destroying Threads</span></span>](../../../docs/standard/threading/destroying-threads.md)  
 <span data-ttu-id="c8d31-110">Discute as implicações da destruição de threads gerenciados e como tratar um <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="c8d31-110">Discusses the ramifications of destroying managed threads, and how to handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 [<span data-ttu-id="c8d31-111">Agendando threads</span><span class="sxs-lookup"><span data-stu-id="c8d31-111">Scheduling Threads</span></span>](../../../docs/standard/threading/scheduling-threads.md)  
 <span data-ttu-id="c8d31-112">Discute as prioridades de thread e como eles afetam o agendamento de thread.</span><span class="sxs-lookup"><span data-stu-id="c8d31-112">Discusses thread priorities and how they affect thread scheduling.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c8d31-113">Referência</span><span class="sxs-lookup"><span data-stu-id="c8d31-113">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="c8d31-114">Fornece a documentação de referência para a classe <xref:System.Threading.Thread>, que representa um thread gerenciado, seja ele proveniente de código não gerenciado ou criado em um aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c8d31-114">Provides reference documentation for the <xref:System.Threading.Thread> class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.Threading.ThreadStart>  
 <span data-ttu-id="c8d31-115">Fornece documentação de referência para o delegado <xref:System.Threading.ThreadStart> que representa os procedimentos do thread sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c8d31-115">Provides reference documentation for the <xref:System.Threading.ThreadStart> delegate that represents parameterless thread procedures.</span></span>  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 <span data-ttu-id="c8d31-116">Fornece uma maneira fácil de passar dados para um procedimento de thread, embora sem tipagem forte.</span><span class="sxs-lookup"><span data-stu-id="c8d31-116">Provides an easy way to pass data to a thread procedure, although without strong typing.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c8d31-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c8d31-117">Related Sections</span></span>  
 [<span data-ttu-id="c8d31-118">Threads e threading</span><span class="sxs-lookup"><span data-stu-id="c8d31-118">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="c8d31-119">Apresenta uma introdução ao threading gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c8d31-119">Provides an introduction to managed threading.</span></span>
