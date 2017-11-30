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
# <a name="how-to-return-a-value-from-a-task"></a>Como retornar um valor de uma tarefa
Este exemplo mostra como usar o <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> tipo retornar um valor de <xref:System.Threading.Tasks.Task%601.Result%2A> propriedade. Isso requer o diretório C:\Users\Public\Pictures\Sample Pictures\ existe e que ele contém arquivos.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 O <xref:System.Threading.Tasks.Task%601.Result%2A> propriedade bloqueia o thread de chamada até que a tarefa seja concluída.  
  
 Para ver como passar o resultado de uma <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> para uma tarefa de continuação, consulte [encadeamento de tarefas por tarefas de continuação usando](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Consulte também  
 [Programação assíncrona baseada em tarefa](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
 [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
