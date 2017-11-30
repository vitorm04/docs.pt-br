---
title: Como retornar um valor de uma tarefa
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
helpviewer_keywords: tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ade2aadc7d76c12c633f84eeb9eced7a637d5df9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="77a20-102">Como retornar um valor de uma tarefa</span><span class="sxs-lookup"><span data-stu-id="77a20-102">How to: Return a Value from a Task</span></span>
<span data-ttu-id="77a20-103">Este exemplo mostra como usar o <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> tipo retornar um valor de <xref:System.Threading.Tasks.Task%601.Result%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="77a20-103">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="77a20-104">Isso requer o diretório C:\Users\Public\Pictures\Sample Pictures\ existe e que ele contém arquivos.</span><span class="sxs-lookup"><span data-stu-id="77a20-104">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77a20-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77a20-105">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="77a20-106">O <xref:System.Threading.Tasks.Task%601.Result%2A> propriedade bloqueia o thread de chamada até que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="77a20-106">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="77a20-107">Para ver como passar o resultado de uma <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> para uma tarefa de continuação, consulte [encadeamento de tarefas por tarefas de continuação usando](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="77a20-107">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77a20-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77a20-108">See Also</span></span>  
 [<span data-ttu-id="77a20-109">Programação assíncrona baseada em tarefa</span><span class="sxs-lookup"><span data-stu-id="77a20-109">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
 [<span data-ttu-id="77a20-110">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="77a20-110">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
