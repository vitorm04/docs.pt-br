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
helpviewer_keywords: tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4717e3a077648d9db51fe39228209617b384bd0c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Como: Evitar que uma tarefa filho se anexe ao seu pai
Este documento demonstra como impedir a anexar à tarefa pai de uma tarefa filho. Impedindo que uma tarefa filho se anexe ao seu pai é útil quando você chama um componente que foi criado por um terceiro e que também usa as tarefas. Por exemplo, um componente de terceiros que usa o <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opção para criar um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> objeto pode causar problemas no seu código, se ela for demorada ou gera uma exceção sem tratamento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir compara os efeitos de usar as opções padrão para os efeitos de impedir que uma tarefa filho anexe ao pai. O exemplo cria um <xref:System.Threading.Tasks.Task> objeto que chama em uma biblioteca de terceiros que também usa um <xref:System.Threading.Tasks.Task> objeto. A biblioteca de terceiros usa a <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opção para criar o <xref:System.Threading.Tasks.Task> objeto. O aplicativo usa o <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opção para criar a tarefa pai. Essa opção instrui o tempo de execução para remover o <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> especificação de tarefas filho.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Como uma tarefa pai não for concluída até o término de todas as tarefas filho, uma tarefa filho de execução longa pode causar o desempenho geral do aplicativo. Neste exemplo, quando o aplicativo usa as opções padrão para criar a tarefa pai, a tarefa filho deve ser concluído antes de concluir a tarefa pai. Quando o aplicativo usa o <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opção, o filho não está anexada ao pai. Portanto, o aplicativo pode executar trabalho adicional após a conclusão da tarefa pai e antes que ele deve aguardar a conclusão da tarefa do filho.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Copie o código de exemplo e cole-o em um projeto do Visual Studio ou colá-lo em um arquivo chamado `DenyChildAttach.cs` (`DenyChildAttach.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), e, em seguida, execute o seguinte comando em uma janela de Prompt de comando do Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe DenyChildAttach.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe DenyChildAttach.vb**  
  
## <a name="robust-programming"></a>Programação robusta  
  
## <a name="see-also"></a>Consulte também  
 [Programação assíncrona baseada em tarefa](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
