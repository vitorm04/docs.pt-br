---
title: "Encadeando tarefas com tarefas de continuação"
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
helpviewer_keywords: tasks, continuations
ms.assetid: 0b45e9a2-de28-46ce-8212-1817280ed42d
caps.latest.revision: "30"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7037e0c91ee6ae83b70d6a26e72b87095456063b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="chaining-tasks-by-using-continuation-tasks"></a>Encadeando tarefas com tarefas de continuação
Na programação assíncrona, é muito comum para uma operação assíncrona, após a conclusão, invocar uma segunda operação e passar dados para ela. Tradicionalmente, isso foi feito usando os métodos de retorno de chamada. Na Biblioteca de Tarefas Paralelas, a mesma funcionalidade é fornecida pelas *tarefas de continuação*. Uma tarefa de continuação (também conhecida como uma continuação) é uma tarefa assíncrona invocada por outra tarefa, que é conhecida como a *antecessora*, quando a antecessora termina.  
  
 As continuações são relativamente fáceis de usar, mas mesmo assim são muito poderosas e flexíveis. Por exemplo, você pode:  
  
-   Passe dados da antecessora para a continuação.  
  
-   Especifique as condições precisas sob a qual a continuação será invocada ou não invocada.  
  
-   Cancele uma continuação antes que ela comece ou cooperativamente enquanto ela estiver em execução.  
  
-   Forneça dicas sobre como a continuação deve ser agendada.  
  
-   Invoque várias continuações da mesma antecessora.  
  
-   Invoque uma continuação quando todas ou qualquer uma das diversas antecessoras for concluída.  
  
-   Encadeie continuações uma após a outra para qualquer comprimento arbitrário.  
  
-   Use uma continuação para manipular exceções lançadas pela antecessora.  
  
## <a name="about-continuations"></a>Sobre continuações  
 Uma continuação é uma tarefa que é criada no <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation> estado. Ela é ativada automaticamente quando sua tarefa ou tarefas antecessoras são concluídas. Chamando <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> em uma continuação no código do usuário gera um <xref:System.InvalidOperationException?displayProperty=nameWithType> exceção.  
  
 Uma continuação é um <xref:System.Threading.Tasks.Task> e não bloqueia o thread em que ele for iniciado. Chamar o <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> método para bloquear até que a tarefa de continuação seja concluído.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Criação de uma continuação para uma única antecessora  
 Criar uma continuação que é executado quando seu antecessor foi concluída chamando o <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> método. O exemplo a seguir mostra o padrão básico (por questões de clareza, o tratamento de exceções será omitido). Ele executa uma tarefa antecedente, `taskA`, que retorna um <xref:System.DayOfWeek> objeto que indica o nome do dia da semana atual. Quando a antecessora termina, a tarefa de continuação, `taskB`, recebe a antecessora e exibe uma cadeia de caracteres que inclui seu resultado.  
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Criação de uma continuação de vários antecessoras  
 Você também pode criar uma continuação que será executada quando qualquer uma ou todo um grupo de tarefas tiver sido concluído. Para executar uma continuação quando tem concluído todas as tarefas antecedente, chamar estático (`Shared` no Visual Basic) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> método ou a instância <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> método. Para executar uma continuação quando qualquer uma das tarefas antecedente for concluída, você chama estático (`Shared` no Visual Basic) <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> método ou a instância <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> método.  
  
 Observe que as chamadas para o <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> sobrecargas não bloqueiam o thread de chamada.  No entanto, você normalmente chama tudo, exceto o <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> métodos para recuperar retornado <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> propriedade, que bloqueia o thread de chamada.  
  
 A exemplo a seguir chama o <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> método para criar uma tarefa de continuação que reflete os resultados de suas tarefas antecedente dez. Cada tarefa antecessora eleva ao quadrado um valor de índice que varia de um a dez. Se o antecedentes concluída com êxito (seus <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> é de propriedade <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>), o <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> propriedade a continuação é uma matriz do <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> valores retornados por cada antecessor. O exemplo os adiciona para calcular a soma dos quadrados de todos os números entre um e dez.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Opções de continuação  
 Quando você cria uma única tarefa continuação, você pode usar um <xref:System.Threading.Tasks.Task.ContinueWith%2A> sobrecarga que utiliza um <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> valor de enumeração para especificar as condições sob as quais a continuação inicia. Por exemplo, você pode especificar que a continuação só será executada se a antecessora for concluída com êxito ou apenas se ela for concluída em um estado de falha. Se a condição não for verdadeira quando o antecessor está pronto para invocar a continuação, a continuação faz a transição diretamente para o <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> de estado e não pode ser iniciado depois disso.  
  
 Um número de métodos de continuação várias tarefas, como sobrecargas do <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> método, também incluem um <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> parâmetro. Somente um subconjunto de todos os <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> membros de enumeração são válidos, no entanto. Você pode especificar <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> valores que têm contrapartes no <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> enumeração, como <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType>, e <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>. Se você especificar qualquer uma da `NotOn` ou `OnlyOn` opções com uma continuação de várias tarefas, uma <xref:System.ArgumentOutOfRangeException> exceção será lançada em tempo de execução.  
  
 Para obter mais informações sobre opções de continuação de tarefas, consulte o <xref:System.Threading.Tasks.TaskContinuationOptions> tópico.  
  
## <a name="passing-data-to-a-continuation"></a>Passagem de dados para uma continuação  
 O <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> método passa uma referência para o antecessor para o representante de usuário de continuação como um argumento. Se for o antecessor um <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> objeto e a tarefa executaram até que ela foi concluída, e a continuação pode acessar o <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> propriedade da tarefa.  
  
 O <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> propriedade bloqueia até que a tarefa foi concluída. No entanto, se a tarefa foi cancelada ou com falha, a tentativa de acessar o <xref:System.Threading.Tasks.Task%601.Result%2A> propriedade lança um <xref:System.AggregateException> exceção. Você pode evitar esse problema usando o <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion> opção, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Se você quiser que a continuação seja executada mesmo se a antecessora não tiver sido concluída com êxito, deverá se proteger contra a exceção. Uma abordagem é testar o <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> tentativa de acessar a propriedade do antecedente e somente o <xref:System.Threading.Tasks.Task%601.Result%2A> propriedade se o status não for <xref:System.Threading.Tasks.TaskStatus.Faulted> ou <xref:System.Threading.Tasks.TaskStatus.Canceled>. Você também pode examinar o <xref:System.Threading.Tasks.Task.Exception%2A> propriedade o antecessor. Para saber mais, veja [Tratamento de exceção](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md). O exemplo a seguir modifica o exemplo anterior para acesso do antecessor <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> propriedade somente se o status for <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Cancelamento de uma continuação  
 O <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> propriedade de uma continuação é definida como <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> nas seguintes situações:  
  
-   Ele gera um <xref:System.OperationCanceledException> exceção em resposta a uma solicitação de cancelamento. Assim como acontece com qualquer tarefa, se a exceção contiver o mesmo token que foi passado para a continuação, ela será tratada como uma confirmação do cancelamento cooperativa.  
  
-   A continuação do é passada uma <xref:System.Threading.CancellationToken?displayProperty=nameWithType> cujo <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> é de propriedade `true`. Nesse caso, a continuação não iniciar, e ela faz a transição para o <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> estado.  
  
-   A continuação nunca será executado porque a condição definida seu <xref:System.Threading.Tasks.TaskContinuationOptions> argumento não foi atendido. Por exemplo, se um antecessor entra em um <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> estado sua continuação passado a <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> opção não será executado, mas fará a transição para o <xref:System.Threading.Tasks.TaskStatus.Canceled> estado.  
  
 Se uma tarefa e sua continuação representam duas partes da mesma operação lógica, você pode passar o mesmo token de cancelamento para as duas tarefas, conforme mostrado no exemplo a seguir. Ele consiste em uma antecessora que gera uma lista de inteiros divisíveis por 33, que é passada para a continuação. Por sua vez, a continuação exibe a lista. A antecessora e a continuação pausam regularmente por intervalos aleatórios. Além disso, um <xref:System.Threading.Timer?displayProperty=nameWithType> objeto é usado para executar o `Elapsed` método após um intervalo de tempo limite de cinco segundos. Isso chama o <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> método, o que faz com que a tarefa em execução no momento chamar o <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType> método. Se o <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> método é chamado quando o antecessor ou sua continuação está em execução depende a duração da pausa a gerado aleatoriamente. Se a antecessora for cancelada, a continuação não será iniciada. Se a antecessora não for cancelada, o token ainda poderá ser usado para cancelar a continuação.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Você também pode impedir um token de cancelamento de uma continuação da execução se seu antecessor for cancelado sem fornecer a continuação especificando o <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> opção quando você cria a continuação. Este é um exemplo simples.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Depois que uma continuação entra no <xref:System.Threading.Tasks.TaskStatus.Canceled> de estado, ele pode afetar continuações a seguem, dependendo da <xref:System.Threading.Tasks.TaskContinuationOptions> que foram especificados para as continuações.  
  
 As continuações descartadas não serão iniciadas.  
  
## <a name="continuations-and-child-tasks"></a>Continuações e tarefas filhas  
 Uma continuação não é executada até que a antecessora e todas suas tarefas filhas anexadas sejam concluídas. A continuação não espera a conclusão de tarefas filhas desanexadas. Os dois exemplos a seguir ilustram tarefas filhas anexadas e desanexadas de uma antecessora que cria uma continuação. No exemplo a seguir, a continuação é executada somente após a conclusão de todas as tarefas filhas e executar o exemplo várias vezes produzirá uma saída idêntica em todas elas. Observe que o exemplo inicia o antecessor chamando o <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> método, desde que por padrão o <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> método cria uma tarefa pai de opção de criação de tarefa cujo padrão é <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Se as tarefas filhas forem desanexadas da antecessora, no entanto, a continuação será executada assim que a antecessor tiver sido finalizada, independentemente do estado das tarefas filhas. Como resultado, várias execuções do exemplo a seguir podem produzir uma saída variável que depende de como o agendador de tarefas tratou cada tarefa filha.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 O status final da tarefa antecessora depende do status final de quaisquer tarefas filhas anexadas. O status de tarefas filhas desanexadas não afeta a principal. Para obter mais informações, consulte [Tarefas filho anexadas e desanexadas](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Associação de estado a continuações  
 Você pode associar o estado arbitrário a uma continuação da tarefa. O <xref:System.Threading.Tasks.Task.ContinueWith%2A> método fornece versões sobrecarregadas cada tirar uma <xref:System.Object> valor que representa o estado de continuação. Mais tarde você pode acessar esse objeto de estado usando o <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> propriedade. Esse objeto de estado será `null` se você não fornecer um valor.  
  
 O estado de continuação é útil quando você converte o código existente que usa o [APM (Modelo de Programação Assíncrona)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) para usar o TPL. Em APM, você normalmente fornece o estado do objeto no  **começar*método** * método e acesso posterior estado usando o <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType> propriedade. Usando o <xref:System.Threading.Tasks.Task.ContinueWith%2A> método, você pode preservar nesse estado quando você converte o código que usa o APM para usar a TPL.  
  
 Estado de continuação também pode ser útil quando você trabalha com <xref:System.Threading.Tasks.Task> objetos no [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] depurador. Por exemplo, na janela **Tarefas Paralelas**, a coluna **Tarefa** exibe a representação de cadeia de caracteres do objeto de estado para cada tarefa. Para saber mais sobre a janela **Tarefas Paralelas**, veja [Uso da janela Tarefas](/visualstudio/debugger/using-the-tasks-window).  
  
 O exemplo a seguir mostra como usar o estado de continuação. Ele cria uma cadeia de tarefas de continuação. Cada tarefa fornece a hora atual, um <xref:System.DateTime> objeto, para o `state` parâmetro o <xref:System.Threading.Tasks.Task.ContinueWith%2A> método. Cada <xref:System.DateTime> objeto representa a hora em que a tarefa de continuação é criada. Cada tarefa gera como resultado um segundo <xref:System.DateTime> objeto que representa a hora em que a tarefa for concluída. Depois de concluir todas as tarefas, este exemplo exibe a hora de criação e a hora em que cada continuação a tarefa é concluída.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Tratamento de exceções geradas de continuações  
 Uma relação antecessora-continuação não é uma relação pai-filho. As exceções geradas por continuações não são propagadas para o antecessor. Portanto, trate as exceções geradas por continuações como você lidaria com elas em qualquer outra tarefa, da seguinte maneira:  
  
-   Você pode usar o <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A>, ou <xref:System.Threading.Tasks.Task.WaitAny%2A> método ou seu equivalente genérico, aguarde a continuação. Você pode esperar por uma antecessora e suas continuações na mesma instrução `try`, conforme mostrado no exemplo a seguir.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
-   Você pode usar uma continuação de segundo para observar o <xref:System.Threading.Tasks.Task.Exception%2A> propriedade a continuação do primeiro. No exemplo a seguir, uma tarefa tenta ler um arquivo inexistente. Em seguida, a continuação exibe informações sobre a exceção na tarefa antecessora.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     Porque ele foi executado com o <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType> opção, a continuação executa somente se uma exceção ocorre no antecessor, e, portanto, ele pode assumir que o antecessor <xref:System.Threading.Tasks.Task.Exception%2A> propriedade não é `null`. Se a continuação é executada ou não uma exceção será lançada no antecessor, seria necessário verificar se o antecessor <xref:System.Threading.Tasks.Task.Exception%2A> não é de propriedade `null` antes de tentar a manipulação da exceção, como o fragmento de código a seguir mostra.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Para saber mais, veja [Tratamento de exceções](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) e [NIB: Como tratar exceções geradas por tarefas](http://msdn.microsoft.com/en-us/d6c47ec8-9de9-4880-beb3-ff19ae51565d).  
  
-   Se a continuação é uma tarefa de filho conectado que foi criada usando o <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> opção, suas exceções serão propagadas pelo pai para o thread de chamada, como é o caso em qualquer outro filho anexado. Para obter mais informações, consulte [Tarefas filho anexadas e desanexadas](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Consulte também  
 [TPL (Biblioteca de Paralelismo de Tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
