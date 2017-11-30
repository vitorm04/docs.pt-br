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
# <a name="how-to-cancel-a-task-and-its-children"></a>Como cancelar uma tarefa e seus filhos
Estes exemplos mostram como executar as seguintes tarefas:  
  
1.  Criar e iniciar uma tarefa pode ser cancelada.  
  
2.  Passe um token de cancelamento para o delegado de usuário e, opcionalmente, a instância da tarefa.  
  
3.  Observe e responder à solicitação de cancelamento de seu representante de usuário.  
  
4.  Opcionalmente, observe no thread de chamada que a tarefa foi cancelada.  
  
 O thread de chamada não forçará terminar a tarefa; Ele apenas sinaliza que o cancelamento é solicitado. Se a tarefa já está em execução, cabe ao representante do usuário Observe que a solicitação e responder adequadamente. Se cancelamento for solicitado antes da execução da tarefa, em seguida, o representante do usuário nunca será executado e o objeto de tarefa faz a transição para o estado cancelado.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como terminar uma <xref:System.Threading.Tasks.Task> e seus filhos em resposta a uma solicitação de cancelamento. Ele também mostra que quando um usuário delegar termina, lançando um <xref:System.Threading.Tasks.TaskCanceledException>, o thread de chamada pode optar por usar o <xref:System.Threading.Tasks.Task.Wait%2A> método ou <xref:System.Threading.Tasks.Task.WaitAll%2A> método aguardar concluir as tarefas. Nesse caso, você deve usar um `try/catch` bloco para manipular as exceções no thread de chamada.  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 O <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classe está totalmente integrada com o modelo de cancelamento que se baseia o <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> e <xref:System.Threading.CancellationToken?displayProperty=nameWithType> tipos. Para obter mais informações, consulte [cancelamento em Threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md) e [cancelamento da tarefa](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>  
 <xref:System.Threading.CancellationToken?displayProperty=nameWithType>  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>  
 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>  
 [Programação assíncrona baseada em tarefa](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
 [Tarefas filho anexadas e desanexadas](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)  
 [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
