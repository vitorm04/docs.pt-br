---
title: "Tratamento de exceções (biblioteca de tarefas paralelas)"
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
helpviewer_keywords: tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e62498376d321d8ff22a53315b9d5f18a8865056
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-handling-task-parallel-library"></a>Tratamento de exceções (biblioteca de tarefas paralelas)
Exceções sem tratamento que são geradas pelo código do usuário que está em execução dentro de uma tarefa são propagadas de volta para o thread de chamada, exceto em determinados cenários descritos neste tópico. Exceções sejam propagadas ao usar um estático ou instância <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> ou <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` métodos e tratá-los, colocando a chamada em um `try` / `catch` instrução. Se uma tarefa é o pai do tarefas filho anexado, ou se você estiver esperando em várias tarefas, várias exceções foi geradas.  
  
 Para propagar todas as exceções de volta para o thread de chamada, a infraestrutura de tarefa encapsula-los em um <xref:System.AggregateException> instância. O <xref:System.AggregateException> exceção tem um <xref:System.AggregateException.InnerExceptions%2A> propriedade que pode ser enumerada para examinar todas as exceções originais que foram lançadas e lidar com (ou não tratar) cada um deles individualmente. Você também pode manipular as exceções originais usando o <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> método.  
  
 Mesmo que apenas uma exceção for lançada, ainda é encapsulado em um <xref:System.AggregateException> exceção, como mostra o exemplo a seguir.  
  
 [!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
 [!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]  
  
 Você pode evitar uma exceção sem tratamento capturando apenas o <xref:System.AggregateException> e não observando qualquer uma das exceções internas. No entanto, recomendamos que você não faça isso porque ele é semelhante a captura de base de <xref:System.Exception> tipo em cenários de não paralelas. Para capturar uma exceção sem executar ações específicas para recuperá-lo pode deixar o programa em um estado indeterminado.  
  
 Se você não deseja chamar o <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> ou <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` método para aguardar a conclusão da tarefa, você também pode recuperar o <xref:System.AggregateException> exceção a partir da tarefa <xref:System.Threading.Tasks.Task.Exception%2A> propriedade, como mostra o exemplo a seguir. Para obter mais informações, consulte o [observando exceções usando a propriedade Task.Exception](#ExceptionProp) neste tópico.  
  
 [!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
 [!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]  
  
 Se você não espera uma tarefa que propaga uma exceção ou acesso seu <xref:System.Threading.Tasks.Task.Exception%2A> propriedade, a exceção é escalada de acordo com a política de exceção do .NET quando a tarefa é coletado como lixo.  
  
 Quando as exceções são permitidos para voltar para o thread de junção de bolhas, é possível que uma tarefa pode continuar a processar alguns itens depois que a exceção é gerada.  
  
> [!NOTE]
>  Quando "Apenas meu código" estiver habilitado, o Visual Studio, em alguns casos quebrar a linha que lança a exceção e exibir uma mensagem de erro que diz "exceção não tratada pelo código do usuário". Esse erro é benigno. Você pode pressionar F5 para continuar e ver o comportamento de tratamento de exceção que é demonstrado nesses exemplos. Para impedir que o Visual Studio quebra no primeiro erro, simplesmente desmarque o **habilitar apenas meu código** caixa de seleção em **ferramentas, opções, depuração, geral**.  
  
## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Tarefas filho anexado e AggregateExceptions aninhados  
 Se uma tarefa tem uma tarefa filho anexado que lança uma exceção, essa exceção é encapsulada em um <xref:System.AggregateException> antes que ela é propagada para a tarefa pai, que encapsula a essa exceção em seu próprio <xref:System.AggregateException> antes de ele propaga volta para o thread de chamada. Nesses casos, o <xref:System.AggregateException.InnerExceptions%2A> propriedade o <xref:System.AggregateException> exceção detectada no <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> ou <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` ou <xref:System.Threading.Tasks.Task.WaitAny%2A> ou <xref:System.Threading.Tasks.Task.WaitAll%2A> método contém um ou mais <xref:System.AggregateException> instâncias, não o exceções originais que causou a falha. Para evitar a iteração aninhada <xref:System.AggregateException> exceções, você pode usar o <xref:System.AggregateException.Flatten%2A> método para remover todos os aninhada <xref:System.AggregateException> exceções, para que o <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> propriedade contém as exceções originais. No exemplo a seguir, aninhados <xref:System.AggregateException> instâncias são mescladas e tratadas em um loop.  
  
 [!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
 [!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]  
  
 Você também pode usar o <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> método relançar as exceções internas de vários <xref:System.AggregateException> instâncias geradas por várias tarefas em um único <xref:System.AggregateException> instância, como mostra o exemplo a seguir.  
  
 [!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
 [!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]  
  
## <a name="exceptions-from-detached-child-tasks"></a>Exceções de tarefas desanexadas filho  
 Por padrão, as tarefas filho são criadas como desanexado. Exceções geradas por tarefas desanexadas devem ser manipuladas ou lançada novamente na tarefa pai imediato; eles não serão propagados para o thread de chamada nas mesmas tarefas filho forma como anexados propagada de volta. O pai mais alto pode rethrow manualmente uma exceção desanexado filho para fazer com que ele seja encapsulada em um <xref:System.AggregateException> e propagadas de volta para o thread de chamada.  
  
 [!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
 [!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]  
  
 Mesmo que você use uma continuação para observar uma exceção em uma tarefa filho, a exceção ainda deve ser observada pela tarefa pai.  
  
## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Exceções que indicam o cancelamento cooperativo  
 Quando o código do usuário em uma tarefa responde a uma solicitação de cancelamento, o procedimento correto é gerar um <xref:System.OperationCanceledException> passando o token de cancelamento no qual a solicitação foi comunicada. Antes de tentar propagar a exceção, a instância da tarefa compara o token na exceção ao que foi passado a ele quando ele foi criado. Se eles forem iguais, a tarefa propaga um <xref:System.Threading.Tasks.TaskCanceledException> encapsulado no <xref:System.AggregateException>, e pode ser visto quando as exceções internas são examinadas. No entanto, se a tarefa não está aguardando o thread de chamada, essa exceção específica não será propagada. Para obter mais informações, consulte [Cancelamento de tarefas](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
 [!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
 [!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]  
  
## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>Usando o método de identificador para filtrar exceções internas  
 Você pode usar o <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> método para filtrar as exceções que podem ser tratados como "manipulado" sem usar nenhuma lógica adicional. O delegado de usuário que é fornecida para o <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> método, você pode examinar o tipo de exceção, seu <xref:System.Exception.Message%2A> propriedade ou outras informações sobre ela que permitirá que você determine se ele é benigno. Todas as exceções para o qual o delegado retorna `false` são lançada novamente em uma nova <xref:System.AggregateException> instância imediatamente após o <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> método retorna.  
  
 O exemplo a seguir é funcionalmente equivalente ao primeiro exemplo neste tópico, que examina cada exceção no <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> coleção.  Em vez disso, esse manipulador de exceção chama o <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> o método objeto para cada exceção e as únicas exceções relança que não são `CustomException` instâncias.  
  
 [!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
 [!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]  
  
 A seguir está um exemplo mais completo que usa o <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> método para fornecer um tratamento especial para um <xref:System.UnauthorizedAccessException> exceção ao enumerar arquivos.  
  
 [!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
 [!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]  
  
<a name="ExceptionProp"></a>   
## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Observando exceções usando a propriedade Task.Exception  
 Se uma tarefa é concluída no <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> estado, seu <xref:System.Threading.Tasks.Task.Exception%2A> propriedade pode ser examinada para descobrir qual exceção específica causou a falha. Uma boa maneira de observar o <xref:System.Threading.Tasks.Task.Exception%2A> propriedade é usar uma continuação que é executado somente se a tarefa antecedente falhas, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
 [!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]  
  
 Em um aplicativo real, o delegado de continuação foi possível registrar informações detalhadas sobre a exceção e possivelmente gerar novas tarefas para recuperar da exceção.  
  
## <a name="unobservedtaskexception-event"></a>Evento UnobservedTaskException  
 Em alguns cenários, como ao hospedar plug-ins não confiáveis, exceções benignas podem ser comuns, e pode ser muito difícil manualmente observe todos eles. Nesses casos, você pode manipular o <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType> evento. O <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType> instância que é passada para o manipulador pode ser usada para impedir que a exceção não observada sejam propagadas de volta para o thread de junção.  
  
## <a name="see-also"></a>Consulte também  
 [TPL (Biblioteca de Paralelismo de Tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
