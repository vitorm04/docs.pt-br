---
title: Tarefas filho anexadas e desanexadas
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
helpviewer_keywords: tasks, child tasks
ms.assetid: c95788bf-90a6-4e96-b7bc-58e36a228cc5
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1a0c664dffc2986d4d6985fd2b71cd8055bf2c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="attached-and-detached-child-tasks"></a>Tarefas filho anexadas e desanexadas
Um *tarefa filho* (ou *tarefa aninhada*) é um <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> instância que é criada no delegado de usuário de outra tarefa, que é conhecido como o *tarefa pai de*. Uma tarefa filho pode ser desanexada ou anexada. Um *tarefa filho desanexado* é uma tarefa que é executado independentemente de seu pai. Um *anexado tarefa filho* é uma tarefa aninhada que é criada com o <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opção cujo pai não explicitamente ou por padrão proibido-lo de que está sendo anexado. Uma tarefa pode criar qualquer número de filho anexadas e desanexadas tarefas, limitadas apenas pelos recursos do sistema.  
  
 A tabela a seguir lista as diferenças básicas entre os dois tipos de tarefas filho.  
  
|Categoria|Tarefas filho desanexado|Tarefas filho anexado|  
|--------------|--------------------------|--------------------------|  
|Pai aguarda a conclusão de tarefas filho.|Não|Sim|  
|Pai propaga exceções lançadas por tarefas filho.|Não|Sim|  
|Status do pai depende do status do filho.|Não|Sim|  
  
 Na maioria dos cenários, é recomendável que você use tarefas desanexadas filho, porque suas relações com outras tarefas menos complexas. Isto é por tarefas criadas dentro do pai tarefas desanexadas por padrão, e você deve especificar explicitamente o <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opção para criar uma tarefa filho anexado.  
  
## <a name="detached-child-tasks"></a>Tarefas filho desanexado  
 Embora uma tarefa filho é criada por uma tarefa pai, por padrão é independente da tarefa pai. No exemplo a seguir, uma tarefa pai cria uma tarefa simples filho. Se você executar o exemplo de código várias vezes, você pode perceber que a saída do exemplo é diferente do mostrado, e também que a saída pode mudar cada vez que você executar o código. Isso ocorre porque as tarefas de pai e filho execute independentemente um do outro; o filho é uma tarefa desanexada. O exemplo espera apenas para a tarefa pai ser concluída e a tarefa filho pode não ser executada ou encerra concluída antes que o aplicativo de console.  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 Se a tarefa filho é representada por um <xref:System.Threading.Tasks.Task%601> objeto em vez de <xref:System.Threading.Tasks.Task> do objeto, você pode garantir que a tarefa pai aguardará o filho concluir, acessando o <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> propriedade do filho mesmo se ele é uma tarefa filho desanexado. O <xref:System.Threading.Tasks.Task%601.Result%2A> propriedade bloqueia até que a tarefa for concluída, como mostra o exemplo a seguir.  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>Tarefas filho anexado  
 Ao contrário das tarefas filho desanexado, tarefas filho anexado estreitamente sincronizadas com o pai. Você pode alterar a tarefa filho desanexado no exemplo anterior para uma tarefa filho conectados usando o <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opção na instrução de criação de tarefa, conforme mostrado no exemplo a seguir. Nesse código, a tarefa filho conectados é concluída antes de seu pai. Como resultado, a saída do exemplo é ao mesmo sempre que você executar o código.  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 Você pode usar tarefas filho anexados para criar gráficos totalmente sincronizados de operações assíncronas.  
  
 No entanto, uma tarefa filho pode anexar a seu pai somente se seu pai não proíbe tarefas filho anexado. Tarefas de pai podem impedir explicitamente tarefas filho anexando a elas, especificando o <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opção no construtor de classe da tarefa pai ou o <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> método. Tarefas de pai implicitamente impedir tarefas filho anexando a elas, se elas forem criadas chamando o <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> método. O exemplo a seguir ilustra essa situação. Ele é idêntico ao exemplo anterior, exceto que a tarefa pai é criada chamando o <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType> método em vez de <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType> método. Como a tarefa filho não é possível conectar a seu pai, a saída do exemplo é imprevisível. Como a criação de tarefa padrão de opções para o <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> sobrecargas incluem <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, este exemplo é funcionalmente equivalente ao primeiro exemplo na seção "Desanexado tarefas filho".  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>Exceções em tarefas filho  
 Se uma tarefa filho desanexado lança uma exceção, essa exceção deve ser observada ou manipulada diretamente na tarefa pai assim como ocorre com qualquer tarefa não aninhada. Se uma tarefa filho anexado lança uma exceção, a exceção será propagada automaticamente para a tarefa pai e de volta para o thread que espera ou tenta acessar a tarefa <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> propriedade. Portanto, usando tarefas filho anexado, você pode tratar todas as exceções em apenas um ponto na chamada para <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> no thread de chamada. Para saber mais, veja [Tratamento de exceção](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="cancellation-and-child-tasks"></a>Tarefas filho e de cancelamento  
 Cancelamento da tarefa é cooperativo. Ou seja, para ser anulável, todas as tarefas filho anexado ou desanexado devem monitorar o status do token de cancelamento. Se você quiser cancelar um pai e todos os seus filhos usando uma solicitação de cancelamento, você passa o mesmo token como um argumento para todas as tarefas e fornece cada tarefa a lógica para responder à solicitação de cada tarefa. Para obter mais informações, consulte [Cancelamento de tarefas](../../../docs/standard/parallel-programming/task-cancellation.md) e [Como cancelar uma tarefa e seus filhos](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
### <a name="when-the-parent-cancels"></a>Quando o pai cancela  
 Se um pai se Cancelar antes do início de sua tarefa filho, o filho nunca é iniciado. Se um pai em si Cancelar após sua tarefa filho já foi iniciado, o filho é executado até a conclusão, a menos que ele tem sua própria lógica de cancelamento. Para obter mais informações, consulte [Cancelamento de tarefas](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="when-a-detached-child-task-cancels"></a>Quando uma tarefa filho desanexado cancela  
 Se uma tarefa filho desanexado cancela a mesmo usando o mesmo token que foi passado para o pai e o pai não aguarda a tarefa filho, nenhuma exceção é propagada, pois a exceção é tratada como o cancelamento de cooperação benigno. Esse comportamento é o mesmo que todas as tarefas de nível superior.  
  
### <a name="when-an-attached-child-task-cancels"></a>Quando uma tarefa filho anexado cancela  
 Quando uma tarefa filho anexado cancela a mesmo usando o mesmo token que foi passado para sua tarefa pai, uma <xref:System.Threading.Tasks.TaskCanceledException> é propagada para o thread de junção dentro de um <xref:System.AggregateException>. Você deve aguardar a tarefa pai para que você possa tratar todas as exceções benignas além de todas as exceções de falha são propagadas para cima em um gráfico de tarefas filho anexado.  
  
 Para saber mais, veja [Tratamento de exceção](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>Impedindo que uma tarefa filho se anexe ao seu pai  
 Uma exceção sem tratamento que é gerada por uma tarefa filho é propagada para a tarefa pai. Você pode usar esse comportamento para observar todas as exceções de tarefa filho da tarefa de uma raiz, em vez de percorrer uma árvore de tarefas. No entanto, a propagação de exceção pode ser problemática quando uma tarefa pai não espera anexo do código. Por exemplo, considere um aplicativo que chama um componente de biblioteca de terceiros de um <xref:System.Threading.Tasks.Task> objeto. Se o componente de biblioteca de terceiros também cria um <xref:System.Threading.Tasks.Task> de objeto e especifica <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> para anexá-lo à tarefa pai, todas as exceções sem tratamento que ocorrem na tarefa filho se propaga para o pai. Isso pode resultar em comportamento inesperado no aplicativo principal.  
  
 Para impedir a anexar a sua tarefa pai de uma tarefa filho, especifique o <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opção quando você cria o pai <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> objeto. Quando uma tarefa tenta anexar a seu pai e especifica o pai do <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opção, a tarefa filho não poderá anexar a um pai e será executado apenas como se o <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opção não foi especificada.  
  
 Você também poderá impedir que uma tarefa filho se anexe ao seu pai quando a tarefa filho não for concluída de maneira oportuna. Porque uma tarefa pai não for concluída até o término de todas as tarefas filho, uma tarefa filho de execução longa pode causar o aplicativo geral para baixo desempenho. Para obter um exemplo que mostra como melhorar o desempenho do aplicativo, impedindo a anexar a sua tarefa pai de uma tarefa, consulte [como: evitar que uma tarefa filho anexar ao seu pai](../../../docs/standard/parallel-programming/how-to-prevent-a-child-task-from-attaching-to-its-parent.md).  
  
## <a name="see-also"></a>Consulte também  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)  
 [Paralelismo de dados](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
