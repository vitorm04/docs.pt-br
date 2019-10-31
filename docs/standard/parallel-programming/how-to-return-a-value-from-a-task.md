---
title: Como retornar um valor de uma tarefa
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: 495f68114bfe960b8182be4ab76b72043b2d0cc7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141665"
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="de042-102">Como retornar um valor de uma tarefa</span><span class="sxs-lookup"><span data-stu-id="de042-102">How to: Return a Value from a Task</span></span>
<span data-ttu-id="de042-103">Este exemplo mostra como usar o tipo <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> para retornar um valor da propriedade <xref:System.Threading.Tasks.Task%601.Result%2A>.</span><span class="sxs-lookup"><span data-stu-id="de042-103">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="de042-104">Isso requer que o diretório C:\Usuários\Público\Imagens\Imagens de Exemplo\ exista e contenha arquivos.</span><span class="sxs-lookup"><span data-stu-id="de042-104">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de042-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de042-105">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="de042-106">A propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> bloqueia o thread de chamada até que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="de042-106">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="de042-107">Para ver como passar o resultado de um <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> para uma tarefa de continuação, confira [Encadeamento de tarefas usando tarefas de continuação](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="de042-107">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de042-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de042-108">See also</span></span>

- [<span data-ttu-id="de042-109">Programação assíncrona baseada em tarefa</span><span class="sxs-lookup"><span data-stu-id="de042-109">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
- [<span data-ttu-id="de042-110">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="de042-110">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
