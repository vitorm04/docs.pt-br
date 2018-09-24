---
title: Como cancelar uma tarefa e seus filhos
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb520169f8e7925862d415a4dfb65af09263b0d2
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46004225"
---
# <a name="how-to-cancel-a-task-and-its-children"></a><span data-ttu-id="f0520-102">Como cancelar uma tarefa e seus filhos</span><span class="sxs-lookup"><span data-stu-id="f0520-102">How to: Cancel a Task and Its Children</span></span>
<span data-ttu-id="f0520-103">Estes exemplos mostram como realizar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="f0520-103">These examples show how to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="f0520-104">Crie e inicie uma tarefa cancelável.</span><span class="sxs-lookup"><span data-stu-id="f0520-104">Create and start a cancelable task.</span></span>  
  
2.  <span data-ttu-id="f0520-105">Passe um token de cancelamento para o representante de usuário e, opcionalmente, para a instância da tarefa.</span><span class="sxs-lookup"><span data-stu-id="f0520-105">Pass a cancellation token to your user delegate and optionally to the task instance.</span></span>  
  
3.  <span data-ttu-id="f0520-106">Observe e responda à solicitação de cancelamento de seu representante de usuário.</span><span class="sxs-lookup"><span data-stu-id="f0520-106">Notice and respond to the cancellation request in your user delegate.</span></span>  
  
4.  <span data-ttu-id="f0520-107">Opcionalmente, observe no thread de chamada que a tarefa foi cancelada.</span><span class="sxs-lookup"><span data-stu-id="f0520-107">Optionally notice on the calling thread that the task was canceled.</span></span>  
  
 <span data-ttu-id="f0520-108">O thread de chamada não força o término da tarefa. Ele apenas sinaliza que o cancelamento é solicitado.</span><span class="sxs-lookup"><span data-stu-id="f0520-108">The calling thread does not forcibly end the task; it only signals that cancellation is requested.</span></span> <span data-ttu-id="f0520-109">Se a tarefa já estiver em execução, cabe ao representante de usuário observar a solicitação e responder adequadamente.</span><span class="sxs-lookup"><span data-stu-id="f0520-109">If the task is already running, it is up to the user delegate to notice the request and respond appropriately.</span></span> <span data-ttu-id="f0520-110">Se cancelamento for solicitado antes da execução da tarefa, o representante de usuário nunca será executado e o objeto de tarefa fará a transição para o estado Cancelado.</span><span class="sxs-lookup"><span data-stu-id="f0520-110">If cancellation is requested before the task runs, then the user delegate is never executed and the task object transitions into the Canceled state.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0520-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f0520-111">Example</span></span>  
 <span data-ttu-id="f0520-112">Este exemplo mostra como terminar uma <xref:System.Threading.Tasks.Task> e suas tarefas filho em resposta a uma solicitação de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="f0520-112">This example shows how to terminate a <xref:System.Threading.Tasks.Task> and its children in response to a cancellation request.</span></span> <span data-ttu-id="f0520-113">Ele também mostra que quando um representante de usuário termina lançando um <xref:System.Threading.Tasks.TaskCanceledException>, o thread de chamada pode optar por usar o método <xref:System.Threading.Tasks.Task.Wait%2A> ou o método <xref:System.Threading.Tasks.Task.WaitAll%2A> para aguardar a conclusão das tarefas.</span><span class="sxs-lookup"><span data-stu-id="f0520-113">It also shows that when a user delegate terminates by throwing a <xref:System.Threading.Tasks.TaskCanceledException>, the calling thread can optionally use the <xref:System.Threading.Tasks.Task.Wait%2A> method or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the tasks to finish.</span></span> <span data-ttu-id="f0520-114">Nesse caso, você deve usar um bloco `try/catch` para lidar com as exceções no thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="f0520-114">In this case, you must use a `try/catch` block to handle the exceptions on the calling thread.</span></span>  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <span data-ttu-id="f0520-115">A classe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> está totalmente integrada com o modelo de cancelamento que se baseia nos tipos <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> e <xref:System.Threading.CancellationToken?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0520-115">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class is fully integrated with the cancellation model that is based on the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="f0520-116">Para saber mais, confira [Cancelamento em threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md) e [Cancelamento de tarefas](../../../docs/standard/parallel-programming/task-cancellation.md).</span><span class="sxs-lookup"><span data-stu-id="f0520-116">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md) and [Task Cancellation](../../../docs/standard/parallel-programming/task-cancellation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0520-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0520-117">See also</span></span>

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>  
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>  
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>  
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>  
- [<span data-ttu-id="f0520-118">Programação assíncrona baseada em tarefa</span><span class="sxs-lookup"><span data-stu-id="f0520-118">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
- [<span data-ttu-id="f0520-119">Tarefas filho anexadas e desanexadas</span><span class="sxs-lookup"><span data-stu-id="f0520-119">Attached and Detached Child Tasks</span></span>](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)  
- [<span data-ttu-id="f0520-120">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="f0520-120">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
