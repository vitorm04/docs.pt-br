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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af0f82e66da1c8db5e17863dfad861c8a7d195e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45618747"
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="8bf73-102">Como retornar um valor de uma tarefa</span><span class="sxs-lookup"><span data-stu-id="8bf73-102">How to: Return a Value from a Task</span></span>
<span data-ttu-id="8bf73-103">Este exemplo mostra como usar o tipo <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> para retornar um valor da propriedade <xref:System.Threading.Tasks.Task%601.Result%2A>.</span><span class="sxs-lookup"><span data-stu-id="8bf73-103">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="8bf73-104">Isso requer que o diretório C:\Usuários\Público\Imagens\Imagens de Exemplo\ exista e contenha arquivos.</span><span class="sxs-lookup"><span data-stu-id="8bf73-104">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bf73-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8bf73-105">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="8bf73-106">A propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> bloqueia o thread de chamada até que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="8bf73-106">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="8bf73-107">Para ver como passar o resultado de um <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> para uma tarefa de continuação, confira [Encadeamento de tarefas usando tarefas de continuação](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="8bf73-107">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf73-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8bf73-108">See also</span></span>

- [<span data-ttu-id="8bf73-109">Programação assíncrona baseada em tarefa</span><span class="sxs-lookup"><span data-stu-id="8bf73-109">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
- [<span data-ttu-id="8bf73-110">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="8bf73-110">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
