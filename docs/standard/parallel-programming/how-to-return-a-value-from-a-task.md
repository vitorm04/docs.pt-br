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
# <a name="how-to-return-a-value-from-a-task"></a>Como retornar um valor de uma tarefa
Este exemplo mostra como usar o tipo <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> para retornar um valor da propriedade <xref:System.Threading.Tasks.Task%601.Result%2A>. Isso requer que o diretório C:\Usuários\Público\Imagens\Imagens de Exemplo\ exista e contenha arquivos.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 A propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> bloqueia o thread de chamada até que a tarefa seja concluída.  
  
 Para ver como passar o resultado de um <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> para uma tarefa de continuação, confira [Encadeamento de tarefas usando tarefas de continuação](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Consulte também

- [Programação assíncrona baseada em tarefa](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
- [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
