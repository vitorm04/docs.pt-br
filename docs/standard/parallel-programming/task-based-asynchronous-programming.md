---
title: Programação assíncrona baseada em tarefas – .NET
description: Neste artigo, saiba mais sobre a programação assíncrona baseada em tarefas por meio da TPL (biblioteca paralela de tarefas) no .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
ms.openlocfilehash: d735cb56c5914dd33ba694c95a8e92446ca47088
ms.sourcegitcommit: 6d09ae36acba0b0e2ba47999f8f1a725795462a2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92925240"
---
# <a name="task-based-asynchronous-programming"></a>Programação assíncrona baseada em tarefas

A TPL (Biblioteca de Paralelismo de Tarefas) é baseada no conceito de uma *tarefa* , que representa uma operação assíncrona. De certa forma, uma tarefa é semelhante a um thread ou a um item de trabalho <xref:System.Threading.ThreadPool>, mas em um nível mais alto de abstração. O termo *paralelismo de tarefas* refere-se a uma ou mais tarefas independentes que são executadas simultaneamente. As tarefas fornecem dois benefícios principais:

- Uso mais eficiente e mais dimensionável de recursos do sistema.

     Nos bastidores, as tarefas são colocadas na fila <xref:System.Threading.ThreadPool>, a qual foi aprimorada com algoritmos que determinam e se ajustam ao número de segmentos e que fornecem o balanceamento de carga para maximizar o rendimento. Isso torna as tarefas relativamente simples, e você pode criar muitas delas para habilitar um paralelismo refinado.

- Controle mais programático do que é possível com um thread ou um item de trabalho.

     As tarefas e a estrutura criada em torno delas fornecem um rico conjunto de APIs que oferecem suporte a espera, cancelamentos, continuações, tratamento de exceções robusto, status detalhado, agendamento personalizado e mais.

Por esses dois motivos, a TPL é a API preferida para escrever código multithread, assíncrono e paralelo no .NET.

## <a name="creating-and-running-tasks-implicitly"></a>Criando e executando tarefas de forma implícita

O método <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> fornece uma maneira conveniente de executar simultaneamente um número qualquer de instruções arbitrárias. Basta passar um delegado <xref:System.Action> para cada item de trabalho. A maneira mais fácil de criar esses delegados é usar expressões lambda. A expressão lambda pode chamar um método chamado ou fornecer o código embutido. O exemplo a seguir mostra uma chamada <xref:System.Threading.Tasks.Parallel.Invoke%2A> básica que cria e inicia duas tarefas executadas simultaneamente. A primeira tarefa é representada por uma expressão lambda que chama um método denominado `DoSomeWork`. A segunda tarefa é representada por uma expressão lambda que chama um método denominado `DoSomeOtherWork`.

> [!NOTE]
> Esta documentação usa expressões lambda para definir delegados na TLP. Se você não estiver familiarizado com expressões lambda em C# ou Visual Basic, consulte [expressões lambda em PLINQ e TPL](lambda-expressions-in-plinq-and-tpl.md).

[!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
[!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]

> [!NOTE]
> O número de instâncias de <xref:System.Threading.Tasks.Task> que são criadas em segundo plano por <xref:System.Threading.Tasks.Parallel.Invoke%2A> não é necessariamente igual ao número de delegados que são fornecidos. A TPL pode usar várias otimizações, principalmente com números grandes de delegados.

Para obter mais informações, consulte [Como usar Parallel.Invoke para executar operações em paralelo](how-to-use-parallel-invoke-to-execute-parallel-operations.md).

Para obter maior controle sobre a execução da tarefa ou para retornar um valor da tarefa, é necessário trabalhar com objetos <xref:System.Threading.Tasks.Task> de forma mais explícita.

## <a name="creating-and-running-tasks-explicitly"></a>Criando e executando tarefas de forma explícita

Uma tarefa que não retorna um valor é representada pela classe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>. Uma tarefa que retorna um valor é representada pela classe <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, a qual herda de <xref:System.Threading.Tasks.Task>. O objeto da tarefa lida com os detalhes da infraestrutura e fornece métodos e propriedades que são acessíveis a partir do segmento de chamada em todo o tempo de vida da tarefa. Por exemplo, você pode acessar a propriedade <xref:System.Threading.Tasks.Task.Status%2A> de uma tarefa a qualquer momento para determinar se ela começou a ser executada, se foi executada até a conclusão, se foi cancelada ou se uma exceção foi gerada. O status é representado por uma enumeração <xref:System.Threading.Tasks.TaskStatus>.

Quando você cria uma tarefa, fornece a ela um delegado de usuário que encapsula o código que a tarefa irá executar. O delegado pode ser expresso como um delegado nomeado, um método anônimo ou uma expressão lambda. As expressões lambda podem conter uma chamada para um método nomeado, conforme mostrado no exemplo a seguir. Observe que o exemplo inclui uma chamada para o método <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> para garantir que a tarefa termine a execução antes do aplicativo de modo console terminar.

[!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
[!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]

Você também pode usar os métodos <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> para criar e iniciar uma tarefa em uma única operação. Para gerenciar a tarefa, os métodos <xref:System.Threading.Tasks.Task.Run%2A> usam o agendador de tarefas padrão, independentemente de qual agendador de tarefas é associado ao segmento atual. Os métodos <xref:System.Threading.Tasks.Task.Run%2A> são a maneira preferencial para criar e iniciar tarefas quando mais controle sobre a criação e o agendamento da tarefa não é necessário.

[!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
[!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]

Você também pode usar o método <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> para criar e iniciar uma tarefa em uma operação. Use este método quando a criação e o agendamento não precisarem ser separados e você precisar de opções adicionais de criação de tarefas ou do uso de um agendador específico, ou ainda quando você precisar passar estado adicional na tarefa que você pode recuperar através da propriedade <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType>, conforme mostrado no exemplo a seguir.

[!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

<xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601> expõem uma propriedade <xref:System.Threading.Tasks.Task.Factory%2A> estática que retorna uma instância padrão de <xref:System.Threading.Tasks.TaskFactory> para que você possa chamar o método como `Task.Factory.StartNew()`. Além disso, no exemplo a seguir, como as tarefas são do tipo <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, cada uma possui uma propriedade pública <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> que contém o resultado do cálculo. As tarefas são executadas de forma assíncrona e podem ser concluídas em qualquer ordem. Se a propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> for acessada antes que a computação seja concluída, a propriedade bloqueará o thread de chamada até o valor estar disponível.

[!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
[!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]

Para obter mais informações, consulte [Como retornar um valor de uma tarefa](how-to-return-a-value-from-a-task.md).

Ao usar uma expressão lambda para criar um delegado, você tem acesso a todas as variáveis que são visíveis nesse ponto em seu código-fonte. No entanto, em alguns casos, especialmente dentro de loops, um lambda não captura a variável conforme o esperado. Ele captura somente o valor final, e não o valor no qual ele se transforma após cada iteração. O exemplo a seguir ilustra o problema. Ele passa um contador de loops para uma expressão lambda que instancia um objeto `CustomData` e usa o contador de loops como o identificador do objeto. Conforme mostra a saída do exemplo, cada objeto `CustomData` possui um identificador idêntico.

[!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
[!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]

Você pode acessar o valor em cada iteração ao fornecer um objeto de estado para uma tarefa através do respectivo construtor. O exemplo a seguir modifica o exemplo anterior usando o contador de loops ao criar o objeto `CustomData`, que, em seguida, é transmitido para a expressão lambda.  Como mostra a saída do exemplo, cada objeto `CustomData` agora tem um identificador exclusivo com base no valor do contador de loops no momento em que o objeto foi instanciado.

[!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
[!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]

Este estado é transmitido como um argumento para o delegado da tarefa e pode ser acessado do objeto de tarefa via propriedade <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType>.  O exemplo a seguir é uma variação do exemplo anterior. Ele usa a propriedade <xref:System.Threading.Tasks.Task.AsyncState%2A> para exibir informações sobre os objetos `CustomData` passados para a expressão lambda.

[!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

## <a name="task-id"></a>ID da Tarefa

Cada tarefa recebe um ID inteiro que a identifica exclusivamente em um domínio de aplicativo e que pode ser acessado pela propriedade <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType>. A ID é útil para exibir informações sobre a tarefa nas janelas **Pilhas Paralelas** e **Tarefas** do depurador do Visual Studio. O ID é criado lentamente, o que significa que ele não é criado até que seja solicitado; portanto, uma tarefa pode ter um ID diferente toda vez que o programa é executado. Para obter mais informações sobre como exibir IDs de tarefa no depurador, consulte [Usando a janela Tarefas](/visualstudio/debugger/using-the-tasks-window) e [Usando a janela Pilhas Paralelas](/visualstudio/debugger/using-the-parallel-stacks-window).

## <a name="task-creation-options"></a>Opções de criação de tarefa

A maioria das APIs que criam tarefas fornecem sobrecargas que aceitam um parâmetro <xref:System.Threading.Tasks.TaskCreationOptions>. Ao especificar uma ou mais dessas opções, você informa ao agendador de tarefas como agendar a tarefa no pool de threads. As opções podem ser combinadas com o uso de **uma operação or** bit a bit.

O exemplo a seguir mostra uma tarefa que tem <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> as <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness> Opções e.

[!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
[!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]

## <a name="tasks-threads-and-culture"></a>Tarefas, threads e cultura

Cada thread tem uma cultura associada e cultura de interface do usuário, que são definidas pelas <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> Propriedades e, respectivamente. A cultura de um thread é usada em operações como formatação, análise, classificação e comparação de cadeia de caracteres. A cultura de interface do usuário de um thread é usada na pesquisa de recursos.

A menos que você especifique uma cultura padrão para todos os threads em um domínio de aplicativo usando as <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> Propriedades e, a cultura padrão e a cultura de interface do usuário de um thread são definidas pela cultura do sistema. Se você definir a cultura de um thread de forma explícita e iniciar um novo thread, o novo thread não herdará a cultura do thread de chamada; em vez disso, sua cultura será a cultura padrão do sistema. No entanto, na programação baseada em tarefas, as tarefas usam a cultura do thread de chamada, mesmo que a tarefa seja executada de forma assíncrona em um thread diferente.

O exemplo a seguir fornece uma ilustração simples. Ele altera a cultura atual do aplicativo para francês (França) (ou, se francês (França) já for a cultura atual, para inglês (Estados Unidos)). Depois, ele chama um delegado chamado `formatDelegate` que retorna alguns números formatados como valores de moeda na nova cultura. Se o delegado for invocado por uma tarefa de forma síncrona ou assíncrona, a tarefa usará a cultura do thread de chamada.

:::code language="csharp" source="snippets/cs/asyncculture1.cs" id="1":::

:::code language="vbnet" source="snippets/vb/asyncculture1.vb" id="1":::

> [!NOTE]
> Nas versões do .NET Framework antes do .NET Framework 4,6, a cultura de uma tarefa é determinada pela cultura do thread em que ele *é executado* , não pela cultura do *thread de chamada* . Para tarefas assíncronas, isso significa que a cultura usada pela tarefa pode ser diferente para a cultura do thread de chamada.

Para saber mais sobre a cultura e tarefas assíncronas, veja a seção “Cultura e operações assíncronas baseadas em tarefas assíncronas” no tópico <xref:System.Globalization.CultureInfo>.

## <a name="creating-task-continuations"></a>Criando continuações de tarefa

Os métodos <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> permitem que você especifique uma tarefa para iniciar quando a *tarefa antecedente* terminar. O delegado da tarefa de continuação recebe uma referência à tarefa antecedente para que possa examinar o status da tarefa antecedente e, ao recuperar o valor da propriedade <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType>, pode usar a saída do antecedente como entrada para a continuação.

No exemplo a seguir, a tarefa `getData` é iniciada por uma chamada feita ao método <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType>. A tarefa `processData` é iniciada automaticamente quando `getData` termina, e `displayData` é iniciada quando `processData` termina. `getData` produz uma matriz de inteiros que é acessível para a tarefa `processData` por meio da propriedade `getData` da tarefa <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType>. A tarefa `processData` processa a matriz e retorna um resultado cujo tipo é derivado do tipo retornado pela expressão lambda passada ao método <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType>. A tarefa `displayData` é executada automaticamente quando `processData` é concluído e o objeto <xref:System.Tuple%603> retornado pela expressão lambda `processData` é acessível para a tarefa de `displayData` através da propriedade `processData` da tarefa <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType>. A tarefa `displayData` recebe o resultado da tarefa `processData` e gera um resultado cujo tipo é inferido de maneira semelhante e que é disponibilizado para o programa na propriedade <xref:System.Threading.Tasks.Task%601.Result%2A>.

[!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
[!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]

Como <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> é um método de instância, é possível encadear as chamadas de método juntas em vez de criar uma instância de um objeto de <xref:System.Threading.Tasks.Task%601> para cada tarefa antecedente. O exemplo a seguir é funcionalmente idêntico ao exemplo anterior, exceto que ele encadeia chamadas ao método <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. Observe que o objeto de <xref:System.Threading.Tasks.Task%601> retornado pela cadeia de chamadas de métodos é a tarefa final de continuação.

[!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
[!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]

Os métodos <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> e <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> permitem que você continue de várias tarefas.

Para obter mais informações, consulte [Encadeando tarefas com tarefas de continuação](chaining-tasks-by-using-continuation-tasks.md).

## <a name="creating-detached-child-tasks"></a>Criando tarefas filho desanexadas

Quando o código do usuário que está executando em uma tarefa cria uma nova tarefa e não especifica a opção de <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>, a nova tarefa não é sincronizada com a tarefa pai de nenhuma forma especial. Esse tipo de tarefa não sincronizada é chamada de *tarefa aninhada desanexada* ou *tarefa filho desanexada* . O exemplo a seguir mostra uma tarefa que cria uma tarefa filha desanexada.

[!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
[!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]

Observe que a tarefa pai não espera a tarefa filha desanexada terminar.

## <a name="creating-child-tasks"></a>Criando tarefas filho

Quando o código de usuário que está sendo executado em uma tarefa cria uma tarefa com a <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opção, a nova tarefa é conhecida como uma *tarefa filho anexada* da tarefa pai. Você pode usar a opção <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> para expressar o paralelismo estruturado das tarefas, porque a tarefa pai espera implicitamente todas as tarefas filhas anexadas terminarem. O exemplo a seguir mostra uma tarefa pai que cria dez tarefas filhas anexadas. Observe que, embora o exemplo chame o método <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> para aguardar que a tarefa pai seja concluída, ele não precisará aguardar explicitamente que as tarefas filhas anexadas sejam concluídas.

[!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
[!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]

Uma tarefa pai pode usar a opção <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> para impedir que outras tarefas se anexem à tarefa pai. Para obter mais informações, consulte [Tarefas filho anexadas e desanexadas](attached-and-detached-child-tasks.md).

## <a name="waiting-for-tasks-to-finish"></a>Aguardando a conclusão das tarefas

Os tipos <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> fornecem várias sobrecargas dos métodos <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> que permitem aguardar a conclusão de uma tarefa. Além disso, as sobrecargas dos métodos estáticos <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> permitem que você aguarde a conclusão de qualquer uma ou de todas as matrizes de tarefas.

Normalmente, você esperaria uma tarefa por um destes motivos:

- O thread principal depende do resultado final calculado por uma tarefa.

- Você precisa tratar exceções que podem ser geradas pela tarefa.

- O aplicativo pode terminar antes que todas as tarefas concluam a execução. Por exemplo, aplicativos de console terminarão assim que todos os códigos síncronos em `Main` (o ponto de entrada do aplicativo) tiverem sido executados.

O exemplo a seguir mostra o padrão básico que não envolve tratamento de exceções.

[!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
[!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]

Para obter um exemplo que mostra o tratamento de exceções, consulte [Tratamento de exceções](exception-handling-task-parallel-library.md).

Algumas sobrecargas permitem especificar um tempo limite, e outras usam um <xref:System.Threading.CancellationToken> adicional como um parâmetro de entrada para que a espera possa ser cancelada programaticamente ou em resposta a uma entrada do usuário.

Ao aguardar uma tarefa, você espera implicitamente todas as filhos da tarefa que foram criadas usando a opção <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType>. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> retorna imediatamente se a tarefa já foi concluída. Todas as exceções geradas por uma tarefa serão geradas por um método <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, mesmo se o método <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> tiver sido chamado após o término da tarefa.

## <a name="composing-tasks"></a>Compondo tarefas

As classes <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601> fornecem vários métodos que podem ajudá-lo na composição de várias tarefas para implementar padrões comuns e melhorar o uso dos recursos de linguagem assíncronos que são fornecidos por C#, Visual Basic e F#. Esta seção descreve os métodos <xref:System.Threading.Tasks.Task.WhenAll%2A>, <xref:System.Threading.Tasks.Task.WhenAny%2A>, <xref:System.Threading.Tasks.Task.Delay%2A> e <xref:System.Threading.Tasks.Task.FromResult%2A>.

### <a name="taskwhenall"></a>Task.WhenAll

O método <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> espera assincronamente a conclusão de vários objetos <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. Ele fornece versões sobrecarregadas que permitem aguardar conjuntos não uniformes de tarefas. Por exemplo, você pode aguardar vários objetos <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601> para concluir após uma chamada de método.

### <a name="taskwhenany"></a>Task.WhenAny

O método <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> espera assincronamente a conclusão de um de vários objetos <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. Assim como no método <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>, esse método oferece as versões sobrecarregadas que permitem aguardar conjuntos não uniformes de tarefas. O método <xref:System.Threading.Tasks.Task.WhenAny%2A> é especialmente útil nos cenários a seguir.

- Operações redundantes. Considere um algoritmo ou uma operação que possam ser executados de várias maneiras. Você pode usar o método <xref:System.Threading.Tasks.Task.WhenAny%2A> para selecionar a operação que termina primeiro e então cancelar as operações restantes.

- Operações intercaladas. Você pode iniciar várias operações que todos devem concluir e usar o método <xref:System.Threading.Tasks.Task.WhenAny%2A> para processar resultados à medida que cada operação termina. Após uma operação ser concluída, você poderá começar uma ou mais tarefas adicionais.

- Operações controladas. Você pode usar o método <xref:System.Threading.Tasks.Task.WhenAny%2A> para estender o cenário anterior ao limitar o número de operações simultâneas.

- Operações expiradas. Você pode usar o método <xref:System.Threading.Tasks.Task.WhenAny%2A> para selecionar entre uma ou mais tarefas e uma tarefa que termine após uma hora específica, como uma tarefa que é retornada pelo método <xref:System.Threading.Tasks.Task.Delay%2A>. O método <xref:System.Threading.Tasks.Task.Delay%2A> é descrito na seção a seguir.

### <a name="taskdelay"></a>Task.Delay

O método <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> gera um objeto <xref:System.Threading.Tasks.Task> que se encerra após o tempo especificado. Você pode usar esse método para compilar os loop que, ocasionalmente, procuram dados, introduzem tempos limites, atrasam manipulação de entrada do usuário por um período pré-determinado e assim por diante.

### <a name="tasktfromresult"></a>Task(T).FromResult

Ao usar o método <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType>, você pode criar um objeto <xref:System.Threading.Tasks.Task%601> com um resultado pré-calculado. Este método é útil quando você executa uma operação assíncrona que retorna um objeto <xref:System.Threading.Tasks.Task%601> e o resultado do objeto <xref:System.Threading.Tasks.Task%601> já está calculado. Para obter um exemplo que use <xref:System.Threading.Tasks.Task.FromResult%2A> para recuperar os resultados de operações de download assíncronas mantidas em um cache, veja [Como criar tarefas pré-computadas](how-to-create-pre-computed-tasks.md).

## <a name="handling-exceptions-in-tasks"></a>Tratando exceções em tarefas

Quando uma tarefa gera uma ou mais exceções, as exceções são envolvidas em uma exceção <xref:System.AggregateException>. Essa exceção é propagada de volta para o thread que se associa à tarefa, que normalmente é o thread que está aguardando a conclusão da tarefa ou o thread que acessa a propriedade <xref:System.Threading.Tasks.Task%601.Result%2A>. Esse comportamento serve para impor a política do .NET Framework de que todas as exceções sem tratamento devem, por padrão, encerrar o processo. O código de chamada pode tratar as exceções usando uma destas opções em um bloco `try`/`catch`:

- O método <xref:System.Threading.Tasks.Task.Wait%2A>

- O método <xref:System.Threading.Tasks.Task.WaitAll%2A>

- O método <xref:System.Threading.Tasks.Task.WaitAny%2A>

- A propriedade <xref:System.Threading.Tasks.Task%601.Result%2A>

O thread de associação também pode manipular exceções ao acessar a propriedade <xref:System.Threading.Tasks.Task.Exception%2A> antes que a tarefa seja coletada pela lixeira. Ao acessar essa propriedade, você impede que a exceção sem tratamento dispare o comportamento de propagação de exceção que finaliza o processo quando o objeto é encerrado.

Para obter mais informações sobre exceções e tarefas, consulte [Tratamento de exceções](exception-handling-task-parallel-library.md).

## <a name="canceling-tasks"></a>Cancelando tarefas

A classe <xref:System.Threading.Tasks.Task> oferece suporte ao cancelamento cooperativo e é totalmente integrada às classes <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> e <xref:System.Threading.CancellationToken?displayProperty=nameWithType>, as quais foram introduzidas no .NET Framework 4. Muitos dos construtores na classe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> recebem um objeto <xref:System.Threading.CancellationToken> como um parâmetro de entrada. Várias das sobrecargas <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> e <xref:System.Threading.Tasks.Task.Run%2A> também incluem um parâmetro <xref:System.Threading.CancellationToken>.

Você pode criar o token e enviar a solicitação de cancelamento algum tempo depois usando a classe <xref:System.Threading.CancellationTokenSource>. Passe o token para <xref:System.Threading.Tasks.Task> como um argumento e também referencie o mesmo token em seu delegado de usuário, o qual faz o trabalho de responder a uma solicitação de cancelamento.

Para obter mais informações, consulte [Cancelamento de tarefas](task-cancellation.md) e [Como cancelar uma tarefa e seus filhos](how-to-cancel-a-task-and-its-children.md).

## <a name="the-taskfactory-class"></a>A classe TaskFactory

A classe <xref:System.Threading.Tasks.TaskFactory> fornece métodos estáticos que encapsulam alguns padrões comuns para criar e iniciar tarefas e tarefas de continuação de linha.

- O padrão mais comum é <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>, que cria e inicia uma tarefa em uma instrução.

- Quando você cria tarefas de continuação de vários antecedentes, use o método <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> ou o método <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> ou seus equivalentes na classe <xref:System.Threading.Tasks.Task%601>. Para obter mais informações, consulte [Encadeando tarefas com tarefas de continuação](chaining-tasks-by-using-continuation-tasks.md).

- Para encapsular os métodos `BeginX` e `EndX` do modelo de programação assíncrona em uma instância de <xref:System.Threading.Tasks.Task> ou de <xref:System.Threading.Tasks.Task%601>, use os métodos <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A>. Para obter mais informações, consulte [Programação assíncrona do .NET Framework tradicional e TPL](tpl-and-traditional-async-programming.md).

O <xref:System.Threading.Tasks.TaskFactory> padrão pode ser acessado como uma propriedade estática na classe <xref:System.Threading.Tasks.Task> ou na classe <xref:System.Threading.Tasks.Task%601>. Você também pode criar uma instância <xref:System.Threading.Tasks.TaskFactory> diretamente e especificar várias opções que incluem <xref:System.Threading.CancellationToken>, uma opção <xref:System.Threading.Tasks.TaskCreationOptions>, uma opção <xref:System.Threading.Tasks.TaskContinuationOptions> ou um <xref:System.Threading.Tasks.TaskScheduler>. As opções especificadas quando você cria a fábrica de tarefas serão aplicadas a todas as tarefas criadas por ela, a menos que <xref:System.Threading.Tasks.Task> seja criada usando a enumeração <xref:System.Threading.Tasks.TaskCreationOptions>. Nesse caso, as opções de tarefa substituem as da fábrica de tarefas.

## <a name="tasks-without-delegates"></a>Tarefas sem representantes

Em alguns casos, convém usar <xref:System.Threading.Tasks.Task> para encapsular qualquer operação assíncrona executada por um componente externo em vez de seu próprio delegado de usuário. Se a operação for baseada no padrão Begin/End do modelo de programação assíncrona, você poderá usar os métodos <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A>. Se esse não for o caso, você poderá usar o objeto <xref:System.Threading.Tasks.TaskCompletionSource%601> para envolver a operação em uma tarefa e obter assim alguns benefícios de programabilidade <xref:System.Threading.Tasks.Task>, por exemplo, suporte a propagação e continuações de exceção. Para obter mais informações, consulte <xref:System.Threading.Tasks.TaskCompletionSource%601>.

## <a name="custom-schedulers"></a>Agendadores personalizados

A maioria dos desenvolvedores de aplicativos ou bibliotecas não se importa com o processador em que a tarefa é executada, como ele sincroniza seu trabalho com outras tarefas e como ela é agendada em <xref:System.Threading.ThreadPool?displayProperty=nameWithType>. Eles apenas exigem que ela seja executada da maneira mais eficiente possível no computador host. Se você exigir um controle mais aguçado sobre os detalhes de programação, a Biblioteca Paralela de Tarefas permite definir algumas configurações no agendador de tarefas padrão e permite até mesmo fornecer um agendador personalizado. Para obter mais informações, consulte <xref:System.Threading.Tasks.TaskScheduler>.

## <a name="related-data-structures"></a>Estruturas de dados relacionados

A TPL possui vários novos tipos públicos que são úteis em cenários paralelos e sequenciais. Esses incluem várias classes de coleção thread-safe, rápida e dimensionável no namespace <xref:System.Collections.Concurrent?displayProperty=nameWithType>, e vários novos tipos de sincronização, por exemplo, <xref:System.Threading.Semaphore?displayProperty=nameWithType> e <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, que são mais eficientes do que seus antecessores para tipos específicos de cargas de trabalho. Outros novos tipos no .NET Framework 4, por exemplo, <xref:System.Threading.Barrier?displayProperty=nameWithType> e <xref:System.Threading.SpinLock?displayProperty=nameWithType>, fornecem a funcionalidade que não estava disponível em versões anteriores. Para obter mais informações, consulte [Estruturas de dados para programação paralela](data-structures-for-parallel-programming.md).

## <a name="custom-task-types"></a>Tipos de tarefa personalizados

Recomendamos que você não herde de <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ou de <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Em vez disso, recomenda-se usar a propriedade <xref:System.Threading.Tasks.Task.AsyncState%2A> para associar dados adicionais ou o estado a um objeto <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. Você também pode usar os métodos de extensão para estender a funcionalidade de <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601>. Para obter mais informações sobre métodos de extensão, consulte [Métodos de extensão](../../csharp/programming-guide/classes-and-structs/extension-methods.md) e [Métodos de extensão](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).

Se você deve herdar de <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> , não é possível usar <xref:System.Threading.Tasks.Task.Run%2A> , ou as <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> classes, ou <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> para criar instâncias de seu tipo de tarefa personalizada porque esses mecanismos criam apenas <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> objetos e. Além disso, você não pode usar os mecanismos de continuação de tarefas fornecidos por <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.TaskFactory> e <xref:System.Threading.Tasks.TaskFactory%601> para criar instâncias de seu tipo de tarefa personalizada porque esses mecanismos também criam apenas objetos <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601>.

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-|-|
|[Encadeando tarefas com tarefas de continuação](chaining-tasks-by-using-continuation-tasks.md)|Descreve como as continuações funcionam.|
|[Tarefas filho anexadas e desanexadas](attached-and-detached-child-tasks.md)|Descreve a diferença entre tarefas filhas anexadas e desanexadas.|
|[Cancelamento da tarefa](task-cancellation.md)|Descreve o suporte a cancelamento interno do objeto <xref:System.Threading.Tasks.Task>.|
|[Tratamento de Exceção](exception-handling-task-parallel-library.md)|Descreve como as exceções são manipuladas em threads simultâneos.|
|[Como: usar Parallel.Invoke para executar operações paralelas](how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Descreve como usar o <xref:System.Threading.Tasks.Parallel.Invoke%2A>.|
|[Como: Retornar um valor de uma tarefa](how-to-return-a-value-from-a-task.md)|Descreve como retornar valores de tarefas.|
|[Como: Cancelar uma tarefa e seus filhos](how-to-cancel-a-task-and-its-children.md)|Descreve como cancelar tarefas.|
|[Como: criar tarefas pré-computadas](how-to-create-pre-computed-tasks.md)|Descreve como usar o método <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> para recuperar os resultados das operações de download assíncronas armazenados em um cache.|
|[Como: percorrer uma árvore binária com tarefas paralelas](how-to-traverse-a-binary-tree-with-parallel-tasks.md)|Descreve como usar tarefas para percorrer uma árvore binária.|
|[Como: Desencapsular uma tarefa aninhada](how-to-unwrap-a-nested-task.md)|Demonstra como usar o método de extensão <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>.|
|[Paralelismo de dados](data-parallelism-task-parallel-library.md)|Descreve como usar <xref:System.Threading.Tasks.Parallel.For%2A> e <xref:System.Threading.Tasks.Parallel.ForEach%2A> para criar loops paralelos sobre dados.|
|[Programação paralela](index.md)|Nó de nível superior para a programação paralela do .NET Framework.|

## <a name="see-also"></a>Veja também

- [Programação paralela](index.md)
- [Exemplos de programação paralela com o & do .NET Core .NET Standard](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)
