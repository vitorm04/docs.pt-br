---
title: Como cancelar uma tarefa e seus filhos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 374068694a3aa9724905964717dc5e77c09fc0ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-task-and-its-children"></a><span data-ttu-id="a5c96-102">Como cancelar uma tarefa e seus filhos</span><span class="sxs-lookup"><span data-stu-id="a5c96-102">How to: Cancel a Task and Its Children</span></span>
<span data-ttu-id="a5c96-103">Estes exemplos mostram como executar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="a5c96-103">These examples show how to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="a5c96-104">Criar e iniciar uma tarefa pode ser cancelada.</span><span class="sxs-lookup"><span data-stu-id="a5c96-104">Create and start a cancelable task.</span></span>  
  
2.  <span data-ttu-id="a5c96-105">Passe um token de cancelamento para o delegado de usuário e, opcionalmente, a instância da tarefa.</span><span class="sxs-lookup"><span data-stu-id="a5c96-105">Pass a cancellation token to your user delegate and optionally to the task instance.</span></span>  
  
3.  <span data-ttu-id="a5c96-106">Observe e responder à solicitação de cancelamento de seu representante de usuário.</span><span class="sxs-lookup"><span data-stu-id="a5c96-106">Notice and respond to the cancellation request in your user delegate.</span></span>  
  
4.  <span data-ttu-id="a5c96-107">Opcionalmente, observe no thread de chamada que a tarefa foi cancelada.</span><span class="sxs-lookup"><span data-stu-id="a5c96-107">Optionally notice on the calling thread that the task was canceled.</span></span>  
  
 <span data-ttu-id="a5c96-108">O thread de chamada não forçará terminar a tarefa; Ele apenas sinaliza que o cancelamento é solicitado.</span><span class="sxs-lookup"><span data-stu-id="a5c96-108">The calling thread does not forcibly end the task; it only signals that cancellation is requested.</span></span> <span data-ttu-id="a5c96-109">Se a tarefa já está em execução, cabe ao representante do usuário Observe que a solicitação e responder adequadamente.</span><span class="sxs-lookup"><span data-stu-id="a5c96-109">If the task is already running, it is up to the user delegate to notice the request and respond appropriately.</span></span> <span data-ttu-id="a5c96-110">Se cancelamento for solicitado antes da execução da tarefa, em seguida, o representante do usuário nunca será executado e o objeto de tarefa faz a transição para o estado cancelado.</span><span class="sxs-lookup"><span data-stu-id="a5c96-110">If cancellation is requested before the task runs, then the user delegate is never executed and the task object transitions into the Canceled state.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5c96-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5c96-111">Example</span></span>  
 <span data-ttu-id="a5c96-112">Este exemplo mostra como terminar uma <xref:System.Threading.Tasks.Task> e seus filhos em resposta a uma solicitação de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="a5c96-112">This example shows how to terminate a <xref:System.Threading.Tasks.Task> and its children in response to a cancellation request.</span></span> <span data-ttu-id="a5c96-113">Ele também mostra que quando um usuário delegar termina, lançando um <xref:System.Threading.Tasks.TaskCanceledException>, o thread de chamada pode optar por usar o <xref:System.Threading.Tasks.Task.Wait%2A> método ou <xref:System.Threading.Tasks.Task.WaitAll%2A> método aguardar concluir as tarefas.</span><span class="sxs-lookup"><span data-stu-id="a5c96-113">It also shows that when a user delegate terminates by throwing a <xref:System.Threading.Tasks.TaskCanceledException>, the calling thread can optionally use the <xref:System.Threading.Tasks.Task.Wait%2A> method or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the tasks to finish.</span></span> <span data-ttu-id="a5c96-114">Nesse caso, você deve usar um `try/catch` bloco para manipular as exceções no thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="a5c96-114">In this case, you must use a `try/catch` block to handle the exceptions on the calling thread.</span></span>  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <span data-ttu-id="a5c96-115">O <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classe está totalmente integrada com o modelo de cancelamento que se baseia o <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> e <xref:System.Threading.CancellationToken?displayProperty=nameWithType> tipos.</span><span class="sxs-lookup"><span data-stu-id="a5c96-115">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class is fully integrated with the cancellation model that is based on the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="a5c96-116">Para obter mais informações, consulte [cancelamento em Threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md) e [cancelamento da tarefa](../../../docs/standard/parallel-programming/task-cancellation.md).</span><span class="sxs-lookup"><span data-stu-id="a5c96-116">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md) and [Task Cancellation](../../../docs/standard/parallel-programming/task-cancellation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c96-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5c96-117">See Also</span></span>  
 <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>  
 <xref:System.Threading.CancellationToken?displayProperty=nameWithType>  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>  
 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>  
 [<span data-ttu-id="a5c96-118">Programação assíncrona baseada em tarefa</span><span class="sxs-lookup"><span data-stu-id="a5c96-118">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
 [<span data-ttu-id="a5c96-119">Tarefas filho anexadas e desanexadas</span><span class="sxs-lookup"><span data-stu-id="a5c96-119">Attached and Detached Child Tasks</span></span>](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)  
 [<span data-ttu-id="a5c96-120">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="a5c96-120">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
