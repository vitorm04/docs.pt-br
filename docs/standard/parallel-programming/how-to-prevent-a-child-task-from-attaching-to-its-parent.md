---
title: 'Como: Evitar que uma tarefa filho se anexe ao seu pai'
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
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2cab2fb9c26a8ddaa868cafebac718e5dfd6baa0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Como: Evitar que uma tarefa filho se anexe ao seu pai
Este documento demonstra como evitar que uma tarefa filho se anexe à tarefa principal. Impedir que uma tarefa filho seja anexada à tarefa pai é útil quando você chama um componente que é gravado por um terceiro e que também usa tarefas. Por exemplo, um componente de terceiros que usa a opção <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> para criar um objeto <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> pode causar problemas em seu código se ele for de longa duração ou lançar uma exceção não controlada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir compara os efeitos de usar as opções padrão com os efeitos de impedir que uma tarefa filho seja anexada ao pai. O exemplo cria um objeto <xref:System.Threading.Tasks.Task> que chama para uma biblioteca de terceiros que também usa um objeto <xref:System.Threading.Tasks.Task>. A biblioteca de terceiros usa a opção <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> para criar o objeto <xref:System.Threading.Tasks.Task>. O aplicativo usa a opção <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> para criar a tarefa pai. Essa opção instrui o tempo de execução para remover a especificação <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> em tarefas filho.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Como a tarefa pai não termina até que todas as tarefas filho sejam concluídas, uma tarefa filho de longa duração pode fazer com que o aplicativo geral tenha um baixo desempenho. Neste exemplo, quando o aplicativo usa as opções padrão para criar a tarefa pai, a tarefa filho deve terminar antes da conclusão da tarefa pai. Quando o aplicativo usa a opção <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, a tarefa filho não está anexada à tarefa pai. Portanto, o aplicativo pode executar trabalhos adicionais após a conclusão da tarefa pai e antes de aguardar a conclusão da tarefa filho.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Copie o código de exemplo e cole-o em um projeto do Visual Studio, ou cole-o em um arquivo chamado `DenyChildAttach.cs` (`DenyChildAttach.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) e execute o seguinte comando em uma janela do Prompt de comando do Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe DenyChildAttach.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe DenyChildAttach.vb**  
  
## <a name="robust-programming"></a>Programação robusta  
  
## <a name="see-also"></a>Consulte também  
 [Programação assíncrona baseada em tarefa](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
