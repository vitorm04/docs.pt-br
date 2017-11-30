---
title: Threads em primeiro plano e em segundo plano
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ad427fc2c1175c0d9b333aa418aea039f11a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="d737d-102">Threads em primeiro plano e em segundo plano</span><span class="sxs-lookup"><span data-stu-id="d737d-102">Foreground and Background Threads</span></span>
<span data-ttu-id="d737d-103">Um thread gerenciado é um thread em segundo plano ou em um thread de primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="d737d-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="d737d-104">Threads em segundo plano são idênticos aos threads de primeiro plano com uma exceção: um thread em segundo plano não manter o ambiente de execução gerenciado em execução.</span><span class="sxs-lookup"><span data-stu-id="d737d-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="d737d-105">Depois que todos os threads de primeiro plano tem sido interrompidos em um processo gerenciado (onde o arquivo .exe é um assembly gerenciado), o sistema interrompe todos os threads em segundo plano e desligado.</span><span class="sxs-lookup"><span data-stu-id="d737d-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d737d-106">Quando o tempo de execução para um thread em segundo plano porque o processo está sendo desligado, nenhuma exceção é lançada no thread.</span><span class="sxs-lookup"><span data-stu-id="d737d-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="d737d-107">No entanto, quando threads foram interrompidos, pois o <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> método descarrega o domínio de aplicativo, um <xref:System.Threading.ThreadAbortException> é gerada em threads de primeiro plano e plano de fundo.</span><span class="sxs-lookup"><span data-stu-id="d737d-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="d737d-108">Use o <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> propriedade para determinar se um thread é um plano de fundo ou um thread de primeiro plano ou para alterar seu status.</span><span class="sxs-lookup"><span data-stu-id="d737d-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="d737d-109">Um thread pode ser alterado para um thread em segundo plano a qualquer momento, definindo seu <xref:System.Threading.Thread.IsBackground%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="d737d-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d737d-110">O status de primeiro plano ou plano de fundo de um thread não afeta o resultado de uma exceção sem tratamento no thread.</span><span class="sxs-lookup"><span data-stu-id="d737d-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="d737d-111">No .NET Framework versão 2.0, uma exceção sem tratamento em threads de primeiro plano ou segundo plano resulta no encerramento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d737d-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="d737d-112">Consulte [exceções em Threads gerenciados](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="d737d-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="d737d-113">Threads que pertencem ao pool de threads gerenciados (ou seja, threads cujo <xref:System.Threading.Thread.IsThreadPoolThread%2A> é de propriedade `true`) threads em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d737d-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="d737d-114">Todos os threads que insira o ambiente de execução gerenciado de código não gerenciado são marcados como threads em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d737d-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="d737d-115">Todos os threads gerados ao criar e iniciar um novo <xref:System.Threading.Thread> objeto são por threads de primeiro plano padrão.</span><span class="sxs-lookup"><span data-stu-id="d737d-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="d737d-116">Se você usar um thread para monitorar uma atividade, como uma conexão de soquete, defina seu <xref:System.Threading.Thread.IsBackground%2A> propriedade `true` para que o thread não impede que o processo de encerramento.</span><span class="sxs-lookup"><span data-stu-id="d737d-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d737d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d737d-117">See Also</span></span>  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>
