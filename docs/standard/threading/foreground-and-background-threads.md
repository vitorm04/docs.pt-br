---
title: Threads em primeiro plano e em segundo plano
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dbad5da42f5ed4e03751534a3a183615a9757cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960028"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="40567-102">Threads em primeiro plano e em segundo plano</span><span class="sxs-lookup"><span data-stu-id="40567-102">Foreground and Background Threads</span></span>
<span data-ttu-id="40567-103">Um thread gerenciado é um thread em segundo plano ou um thread em primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="40567-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="40567-104">Threads em segundo plano são idênticos aos threads em primeiro plano com uma exceção: um thread em segundo plano não mantém o ambiente de execução gerenciado em execução.</span><span class="sxs-lookup"><span data-stu-id="40567-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="40567-105">Uma vez que todos os threads em primeiro plano foram interrompidos em um processo gerenciado (onde o arquivo .exe é um assembly gerenciado), o sistema interrompe todos os threads em segundo plano e desliga.</span><span class="sxs-lookup"><span data-stu-id="40567-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40567-106">Quando o tempo de execução interrompe um thread em segundo plano porque o processo está sendo desligado, nenhuma exceção é lançada no thread.</span><span class="sxs-lookup"><span data-stu-id="40567-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="40567-107">No entanto, quando os threads são interrompidos porque o método <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> descarrega o domínio do aplicativo, um <xref:System.Threading.ThreadAbortException> é lançado em ambos os threads em primeiro plano e em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="40567-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="40567-108">Use a propriedade <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> para determinar se um thread é um thread em segundo plano ou em primeiro plano, ou para alterar seu status.</span><span class="sxs-lookup"><span data-stu-id="40567-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="40567-109">Um thread pode ser alterado para um thread em segundo plano a qualquer momento, definindo a propriedade <xref:System.Threading.Thread.IsBackground%2A> para `true`.</span><span class="sxs-lookup"><span data-stu-id="40567-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="40567-110">O status em primeiro plano ou em segundo plano de um thread não afeta o resultado de uma exceção sem tratamento no thread.</span><span class="sxs-lookup"><span data-stu-id="40567-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="40567-111">No .NET Framework versão 2.0, uma exceção sem tratamento em threads de primeiro plano ou segundo plano resulta no encerramento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40567-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="40567-112">Confira [Exceções em threads gerenciados](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="40567-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="40567-113">Threads pertencentes ao pool de threads gerenciados (ou seja, threads cuja propriedade <xref:System.Threading.Thread.IsThreadPoolThread%2A> é `true`) são threads em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="40567-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="40567-114">Todos os threads que entram no ambiente de execução gerenciado do código não gerenciado são marcados como threads em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="40567-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="40567-115">Todos os threads gerados ao criar e iniciar um novo objeto <xref:System.Threading.Thread> são, por padrão, threads em primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="40567-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="40567-116">Se você usar um thread para monitorar uma atividade, como uma conexão de soquete, defina sua propriedade <xref:System.Threading.Thread.IsBackground%2A> como `true` para que o thread não impeça o encerramento do processo.</span><span class="sxs-lookup"><span data-stu-id="40567-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40567-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40567-117">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
