---
title: Como desencapsular uma tarefa aninhada
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
helpviewer_keywords: tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2da3de912abb693c4342e1ede02f273348e4b571
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="43e2c-102">Como desencapsular uma tarefa aninhada</span><span class="sxs-lookup"><span data-stu-id="43e2c-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="43e2c-103">Você pode retornar uma tarefa de um método e esperar ou continuar da tarefa, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="43e2c-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="43e2c-104">No exemplo anterior, o <xref:System.Threading.Tasks.Task%601.Result%2A> é de propriedade do tipo `string` (`String` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="43e2c-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="43e2c-105">No entanto, em alguns cenários, você talvez queira criar uma tarefa dentro de outra tarefa e, em seguida, retornar a tarefa aninhada.</span><span class="sxs-lookup"><span data-stu-id="43e2c-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="43e2c-106">Nesse caso, o `TResult` da tarefa delimitador é uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="43e2c-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="43e2c-107">No exemplo a seguir, a propriedade de resultado é um `Task<Task<string>>` em c# ou `Task(Of Task(Of String))` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="43e2c-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="43e2c-108">Embora seja possível gravar código para decodificar a tarefa externa e recuperar a tarefa original e sua <xref:System.Threading.Tasks.Task%601.Result%2A> propriedade, esse código não é fácil escrever porque você deve lidar com exceções e solicitações de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="43e2c-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="43e2c-109">Nessa situação, é recomendável que você use uma da <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> métodos de extensão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="43e2c-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="43e2c-110">O <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> métodos podem ser usados para transformar qualquer `Task<Task>` ou `Task<Task<TResult>>` (`Task(Of Task)` ou `Task(Of Task(Of TResult))` no Visual Basic) para um `Task` ou `Task<TResult>` (`Task(Of TResult)` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="43e2c-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="43e2c-111">A nova tarefa totalmente representa a tarefa aninhada interna e inclui o estado de cancelamento e todas as exceções.</span><span class="sxs-lookup"><span data-stu-id="43e2c-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43e2c-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43e2c-112">Example</span></span>  
 <span data-ttu-id="43e2c-113">O exemplo a seguir demonstra como usar o <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> métodos de extensão.</span><span class="sxs-lookup"><span data-stu-id="43e2c-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="43e2c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43e2c-114">See Also</span></span>  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
 [<span data-ttu-id="43e2c-115">Programação assíncrona baseada em tarefa</span><span class="sxs-lookup"><span data-stu-id="43e2c-115">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
