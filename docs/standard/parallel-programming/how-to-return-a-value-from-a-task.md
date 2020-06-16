---
title: 'Como: Retornar um valor de uma tarefa'
description: Consulte como usar o tipo System. Threading. Tasks. Task <TResult> para retornar um valor da propriedade Result no .net.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: 051cef7cac654e4369ec1486884876004370ba0b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767969"
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="fd50f-103">Como: Retornar um valor de uma tarefa</span><span class="sxs-lookup"><span data-stu-id="fd50f-103">How to: Return a Value from a Task</span></span>
<span data-ttu-id="fd50f-104">Este exemplo mostra como usar o tipo <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> para retornar um valor da propriedade <xref:System.Threading.Tasks.Task%601.Result%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd50f-104">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="fd50f-105">Isso requer que o diretório C:\Usuários\Público\Imagens\Imagens de Exemplo\ exista e contenha arquivos.</span><span class="sxs-lookup"><span data-stu-id="fd50f-105">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd50f-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fd50f-106">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="fd50f-107">A propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> bloqueia o thread de chamada até que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="fd50f-107">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="fd50f-108">Para ver como passar o resultado de um <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> para uma tarefa de continuação, confira [Encadeamento de tarefas usando tarefas de continuação](chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="fd50f-108">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd50f-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="fd50f-109">See also</span></span>

- [<span data-ttu-id="fd50f-110">Programação assíncrona baseada em tarefas</span><span class="sxs-lookup"><span data-stu-id="fd50f-110">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="fd50f-111">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="fd50f-111">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
