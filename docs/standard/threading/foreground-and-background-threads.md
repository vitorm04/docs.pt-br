---
title: Threads em primeiro plano e em segundo plano
description: Determinar ou alterar se um thread é um thread em segundo plano ou um thread em primeiro plano usando a propriedade Thread. IsBackground no .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET], foreground
- threading [.NET], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
ms.openlocfilehash: 3b468d2de382719496d5dfaf4c704d43f3e748c3
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188062"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="f63ff-103">Threads em primeiro e segundo plano</span><span class="sxs-lookup"><span data-stu-id="f63ff-103">Foreground and background threads</span></span>

<span data-ttu-id="f63ff-104">Um thread gerenciado é um thread em segundo plano ou um thread em primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="f63ff-104">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="f63ff-105">Threads em segundo plano são idênticos aos threads em primeiro plano com uma exceção: um thread em segundo plano não mantém o ambiente de execução gerenciado em execução.</span><span class="sxs-lookup"><span data-stu-id="f63ff-105">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="f63ff-106">Uma vez que todos os threads em primeiro plano foram interrompidos em um processo gerenciado (onde o arquivo .exe é um assembly gerenciado), o sistema interrompe todos os threads em segundo plano e desliga.</span><span class="sxs-lookup"><span data-stu-id="f63ff-106">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f63ff-107">Quando o runtime interrompe um thread em segundo plano porque o processo está sendo desligado, nenhuma exceção é lançada no thread.</span><span class="sxs-lookup"><span data-stu-id="f63ff-107">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="f63ff-108">No entanto, quando os threads são interrompidos porque o método <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> descarrega o domínio do aplicativo, um <xref:System.Threading.ThreadAbortException> é lançado em ambos os threads em primeiro plano e em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="f63ff-108">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="f63ff-109">Use a propriedade <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> para determinar se um thread é um thread em segundo plano ou em primeiro plano, ou para alterar seu status.</span><span class="sxs-lookup"><span data-stu-id="f63ff-109">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="f63ff-110">Um thread pode ser alterado para um thread em segundo plano a qualquer momento, definindo a propriedade <xref:System.Threading.Thread.IsBackground%2A> para `true`.</span><span class="sxs-lookup"><span data-stu-id="f63ff-110">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f63ff-111">O status em primeiro plano ou em segundo plano de um thread não afeta o resultado de uma exceção sem tratamento no thread.</span><span class="sxs-lookup"><span data-stu-id="f63ff-111">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="f63ff-112">Uma exceção sem tratamento em threads de primeiro plano ou em segundo plano resulta no encerramento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f63ff-112">An unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="f63ff-113">Confira [Exceções em threads gerenciados](exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="f63ff-113">See [Exceptions in Managed Threads](exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="f63ff-114">Threads pertencentes ao pool de threads gerenciados (ou seja, threads cuja propriedade <xref:System.Threading.Thread.IsThreadPoolThread%2A> é `true`) são threads em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="f63ff-114">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="f63ff-115">Todos os threads que entram no ambiente de execução gerenciado do código não gerenciado são marcados como threads em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="f63ff-115">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="f63ff-116">Todos os threads gerados ao criar e iniciar um novo objeto <xref:System.Threading.Thread> são, por padrão, threads em primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="f63ff-116">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="f63ff-117">Se você usar um thread para monitorar uma atividade, como uma conexão de soquete, defina sua propriedade <xref:System.Threading.Thread.IsBackground%2A> como `true` para que o thread não impeça o encerramento do processo.</span><span class="sxs-lookup"><span data-stu-id="f63ff-117">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f63ff-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="f63ff-118">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
