---
title: Encadeando tarefas com tarefas de continuação
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, continuations
ms.assetid: 0b45e9a2-de28-46ce-8212-1817280ed42d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27d97d38c903cbb33097db0e109758d98527e00f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591931"
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
 Uma continuação é uma tarefa que é criada no estado <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>. Ela é ativada automaticamente quando sua tarefa ou tarefas antecessoras são concluídas. Chamar <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> em uma continuação no código do usuário gera uma exceção <xref:System.InvalidOperationException?displayProperty=nameWithType>.  
  
 Uma continuação é um <xref:System.Threading.Tasks.Task> e não bloqueia o thread em que é iniciada. Chame o método <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> para bloquear até que a tarefa de continuação seja concluída.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Criação de uma continuação para uma única antecessora  
 Você cria uma continuação que é executada quando seu antecessor é concluído chamando o método <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. O exemplo a seguir mostra o padrão básico (por questões de clareza, o tratamento de exceções será omitido). Ela executa uma tarefa antecessora, `taskA`, que retorna um objeto <xref:System.DayOfWeek> que indica o nome do dia da semana atual. Quando a antecessora termina, a tarefa de continuação, `taskB`, recebe a antecessora e exibe uma cadeia de caracteres que inclui seu resultado.  
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Criação de uma continuação de vários antecessoras  
 Você também pode criar uma continuação que será executada quando qualquer uma ou todo um grupo de tarefas tiver sido concluído. Para executar uma continuação quando todas as tarefas antecedentes são concluídas, você chama o método estático (`Shared` no Visual Basic) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ou o método de instância <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>. Para executar uma continuação quando qualquer uma das tarefas antecedentes é concluída, você chama o método estático (`Shared` no Visual Basic) <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ou o método de instância <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType>.  
  
 Observe que as chamadas para as sobrecargas <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> não bloqueiam o thread de chamada.  No entanto, normalmente você chama tudo, exceto os métodos <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> para recuperar a propriedade <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> retornada, o que bloqueia o thread de chamada.  
  
 O exemplo a seguir chama o método <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> para criar uma tarefa de continuação que reflete os resultados das dez tarefas antecedentes. Cada tarefa antecessora eleva ao quadrado um valor de índice que varia de um a dez. Se os antecedentes tiverem sido concluídos com êxito (se sua propriedade <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> for <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>), a propriedade <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> da continuação será uma matriz dos valores <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> retornados por cada antecessor. O exemplo os adiciona para calcular a soma dos quadrados de todos os números entre um e dez.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Opções de continuação  
 Ao criar uma continuação de tarefa única, você pode usar uma sobrecarga <xref:System.Threading.Tasks.Task.ContinueWith%2A> que utiliza um valor de enumeração <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> para especificar as condições sob as quais a continuação é iniciada. Por exemplo, você pode especificar que a continuação só será executada se a antecessora for concluída com êxito ou apenas se ela for concluída em um estado de falha. Se a condição não for verdadeira quando a antecessora estiver pronta para invocar a continuação, a continuação fará a transição diretamente para o estado <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> e não poderá ser iniciada depois disso.  
  
 Vários métodos de continuação de várias tarefas, como sobrecargas do método <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>, também incluem um parâmetro <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType>. Somente um subconjunto de todos os membros de enumeração <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> é válido, no entanto. Você pode especificar valores <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> que têm contrapartes na enumeração <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType>, como <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType> e <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>. Se você especificar qualquer uma das opções `NotOn` ou `OnlyOn` com uma continuação de várias tarefas, uma exceção <xref:System.ArgumentOutOfRangeException> será gerada em tempo de execução.  
  
 Para saber mais sobre opções de continuação de tarefas, confira o tópico <xref:System.Threading.Tasks.TaskContinuationOptions>.  
  
## <a name="passing-data-to-a-continuation"></a>Passagem de dados para uma continuação  
 O método <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> passa uma referência ao antecessor para o representante de usuário de continuação como um argumento. Se o antecessor for um objeto <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, e a tarefa tiver sido executada ser concluída, a continuação poderá acessar a propriedade <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> da tarefa.  
  
 A propriedade <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> realiza o bloqueio até que a tarefa seja concluída. No entanto, se a tarefa foi cancelada ou falhou, a tentativa de acessar a propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> gera uma exceção <xref:System.AggregateException>. Você pode evitar esse problema usando a opção <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion>, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Se você quiser que a continuação seja executada mesmo se a antecessora não tiver sido concluída com êxito, deverá se proteger contra a exceção. Uma abordagem é testar a propriedade <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> do antecedente e só tentar acessar a propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> se o status não é <xref:System.Threading.Tasks.TaskStatus.Faulted> ou <xref:System.Threading.Tasks.TaskStatus.Canceled>. Você também pode examinar a propriedade <xref:System.Threading.Tasks.Task.Exception%2A> do antecessor. Para saber mais, veja [Tratamento de exceção](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md). O exemplo a seguir modifica o exemplo anterior para acessar a propriedade <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> do antecessor somente se o status é <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Cancelamento de uma continuação  
 A propriedade <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> de uma continuação é definida como <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> nas seguintes situações:  
  
-   Gera uma exceção <xref:System.OperationCanceledException> em resposta a uma solicitação de cancelamento. Assim como acontece com qualquer tarefa, se a exceção contiver o mesmo token que foi passado para a continuação, ela será tratada como uma confirmação do cancelamento cooperativa.  
  
-   A continuação recebe um <xref:System.Threading.CancellationToken?displayProperty=nameWithType> cuja propriedade <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> é `true`. Nesse caso, a continuação não é iniciada e faz a transição para o estado <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType>.  
  
-   A continuação nunca é executada porque a condição definida por seu argumento <xref:System.Threading.Tasks.TaskContinuationOptions> não foi atendida. Por exemplo, se um antecessor entrar em um estado <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType>, sua continuação que recebeu a opção <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> não será executada, mas fará a transição para o estado <xref:System.Threading.Tasks.TaskStatus.Canceled>.  
  
 Se uma tarefa e sua continuação representam duas partes da mesma operação lógica, você pode passar o mesmo token de cancelamento para as duas tarefas, conforme mostrado no exemplo a seguir. Ele consiste em uma antecessora que gera uma lista de inteiros divisíveis por 33, que é passada para a continuação. Por sua vez, a continuação exibe a lista. A antecessora e a continuação pausam regularmente por intervalos aleatórios. Além disso, um objeto <xref:System.Threading.Timer?displayProperty=nameWithType> é usado para executar o método `Elapsed` após um intervalo de tempo limite de cinco segundos. Isso chama o método <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType>, o que faz com que a tarefa em execução no momento chame o método <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType>. O método <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> é chamado ou não quando o antecessor ou sua continuação está em execução, dependendo da duração das pausas geradas aleatoriamente. Se a antecessora for cancelada, a continuação não será iniciada. Se a antecessora não for cancelada, o token ainda poderá ser usado para cancelar a continuação.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Você também pode impedir a execução de uma continuação caso sua antecessora seja cancelada sem o fornecimento da continuação de um token de cancelamento especificando a opção <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> quando a continuação for criada. Este é um exemplo simples.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Depois que uma continuação entra no estado <xref:System.Threading.Tasks.TaskStatus.Canceled>, pode afetar as continuações seguintes, dependendo do <xref:System.Threading.Tasks.TaskContinuationOptions> especificado para as continuações.  
  
 As continuações descartadas não serão iniciadas.  
  
## <a name="continuations-and-child-tasks"></a>Continuações e tarefas filhas  
 Uma continuação não é executada até que a antecessora e todas suas tarefas filhas anexadas sejam concluídas. A continuação não espera a conclusão de tarefas filhas desanexadas. Os dois exemplos a seguir ilustram tarefas filhas anexadas e desanexadas de uma antecessora que cria uma continuação. No exemplo a seguir, a continuação é executada somente após a conclusão de todas as tarefas filhas e executar o exemplo várias vezes produzirá uma saída idêntica em todas elas. Observe que o exemplo inicia o antecessor chamando o método <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>, pois, por padrão, o método <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> cria uma tarefa pai de opção de criação de tarefa cujo padrão é <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Se as tarefas filhas forem desanexadas da antecessora, no entanto, a continuação será executada assim que a antecessor tiver sido finalizada, independentemente do estado das tarefas filhas. Como resultado, várias execuções do exemplo a seguir podem produzir uma saída variável que depende de como o agendador de tarefas tratou cada tarefa filha.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 O status final da tarefa antecessora depende do status final de quaisquer tarefas filhas anexadas. O status de tarefas filhas desanexadas não afeta a principal. Para obter mais informações, consulte [Tarefas filho anexadas e desanexadas](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Associação de estado a continuações  
 Você pode associar o estado arbitrário a uma continuação da tarefa. O método <xref:System.Threading.Tasks.Task.ContinueWith%2A> fornece versões sobrecarregadas que utilizam um valor <xref:System.Object> que representa o estado de continuação. Mais tarde, você pode acessar esse objeto de estado usando a propriedade <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType>. Esse objeto de estado será `null` se você não fornecer um valor.  
  
 O estado de continuação é útil quando você converte o código existente que usa o [APM (Modelo de Programação Assíncrona)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) para usar o TPL. No APM, você normalmente fornece o estado do objeto no método **Begin***Method* e acessa posteriormente esse estado usando a propriedade <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType>. Usando o método <xref:System.Threading.Tasks.Task.ContinueWith%2A>, você pode preservar esse estado ao converter o código que usa o APM para usar a TPL.  
  
 O estado de continuação também pode ser útil quando você trabalha com objetos <xref:System.Threading.Tasks.Task> no depurador do Visual Studio. Por exemplo, na janela **Tarefas Paralelas**, a coluna **Tarefa** exibe a representação de cadeia de caracteres do objeto de estado para cada tarefa. Para saber mais sobre a janela **Tarefas Paralelas**, veja [Uso da janela Tarefas](/visualstudio/debugger/using-the-tasks-window).  
  
 O exemplo a seguir mostra como usar o estado de continuação. Ele cria uma cadeia de tarefas de continuação. Cada tarefa fornece a hora atual, um objeto <xref:System.DateTime>, para o parâmetro `state` do método <xref:System.Threading.Tasks.Task.ContinueWith%2A>. Cada objeto <xref:System.DateTime> representa a hora em que a tarefa de continuação é criada. Cada tarefa gera como resultado um segundo objeto <xref:System.DateTime> que representa a hora de conclusão da tarefa. Depois de concluir todas as tarefas, este exemplo exibe a hora de criação e a hora em que cada continuação a tarefa é concluída.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Tratamento de exceções geradas de continuações  
 Uma relação antecessora-continuação não é uma relação pai-filho. As exceções geradas por continuações não são propagadas para o antecessor. Portanto, trate as exceções geradas por continuações como você lidaria com elas em qualquer outra tarefa, da seguinte maneira:  
  
-   Você pode usar o método <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A> ou <xref:System.Threading.Tasks.Task.WaitAny%2A>, ou seu equivalente genérico, para aguardar a continuação. Você pode esperar por uma antecessora e suas continuações na mesma instrução `try`, conforme mostrado no exemplo a seguir.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
-   Você pode usar uma segunda continuação para observar a propriedade <xref:System.Threading.Tasks.Task.Exception%2A> da primeira continuação. No exemplo a seguir, uma tarefa tenta ler um arquivo inexistente. Em seguida, a continuação exibe informações sobre a exceção na tarefa antecessora.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     Como ele foi executado com a opção <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType>, a continuação será executada somente se uma exceção ocorrer no antecessor. Portanto, ele pode presumir que a propriedade <xref:System.Threading.Tasks.Task.Exception%2A> do antecessor não é `null`. Se a continuação for executada, caso uma exceção seja ou não gerada na antecessora, ela deverá verificar se a propriedade <xref:System.Threading.Tasks.Task.Exception%2A> da antecessora não é `null` antes de tentar tratar a exceção, como mostrado pelo fragmento de código a seguir.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Para saber mais, veja [Tratamento de exceções](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) e [NIB: Como tratar exceções geradas por tarefas](https://msdn.microsoft.com/library/d6c47ec8-9de9-4880-beb3-ff19ae51565d).  
  
-   Se a continuação for uma tarefa filha anexada que foi criada usando a opção <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, suas exceções serão propagadas pelo pai para o thread de chamada, como será o caso em qualquer outra filha anexada. Para obter mais informações, consulte [Tarefas filho anexadas e desanexadas](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Consulte também  
 [TPL (Biblioteca de Paralelismo de Tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
