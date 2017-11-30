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
# <a name="how-to-unwrap-a-nested-task"></a>Como desencapsular uma tarefa aninhada
Você pode retornar uma tarefa de um método e esperar ou continuar da tarefa, conforme mostrado no exemplo a seguir:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 No exemplo anterior, o <xref:System.Threading.Tasks.Task%601.Result%2A> é de propriedade do tipo `string` (`String` no Visual Basic).  
  
 No entanto, em alguns cenários, você talvez queira criar uma tarefa dentro de outra tarefa e, em seguida, retornar a tarefa aninhada. Nesse caso, o `TResult` da tarefa delimitador é uma tarefa. No exemplo a seguir, a propriedade de resultado é um `Task<Task<string>>` em c# ou `Task(Of Task(Of String))` no Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Embora seja possível gravar código para decodificar a tarefa externa e recuperar a tarefa original e sua <xref:System.Threading.Tasks.Task%601.Result%2A> propriedade, esse código não é fácil escrever porque você deve lidar com exceções e solicitações de cancelamento. Nessa situação, é recomendável que você use uma da <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> métodos de extensão, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 O <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> métodos podem ser usados para transformar qualquer `Task<Task>` ou `Task<Task<TResult>>` (`Task(Of Task)` ou `Task(Of Task(Of TResult))` no Visual Basic) para um `Task` ou `Task<TResult>` (`Task(Of TResult)` no Visual Basic). A nova tarefa totalmente representa a tarefa aninhada interna e inclui o estado de cancelamento e todas as exceções.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como usar o <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> métodos de extensão.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
 [Programação assíncrona baseada em tarefa](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
