---
title: Consumindo o padrão assíncrono baseado em tarefa
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e89545b5fa29f6e5bf99bb9b85322d7ee14422a4
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929016"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="50a41-102">Consumindo o padrão assíncrono baseado em tarefa</span><span class="sxs-lookup"><span data-stu-id="50a41-102">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="50a41-103">Quando você usa o TAP (padrão assíncrono baseado em tarefa) para trabalhar com operações assíncronas, você pode usar retornos de chamada para obter uma espera sem bloqueio.</span><span class="sxs-lookup"><span data-stu-id="50a41-103">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span>  <span data-ttu-id="50a41-104">Para tarefas, isso é conseguido por meio de métodos como <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="50a41-104">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="50a41-105">O suporte assíncrono baseado em linguagem oculta retornos de chamada ao permitir que operações assíncronas sejam colocadas em espera no fluxo de controle normal, sendo que o código gerado pelo compilador fornece esse mesmo suporte de nível de API.</span><span class="sxs-lookup"><span data-stu-id="50a41-105">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="50a41-106">Suspendendo a execução com Await</span><span class="sxs-lookup"><span data-stu-id="50a41-106">Suspending Execution with Await</span></span>
 <span data-ttu-id="50a41-107">Começando com o .NET Framework 4.5, você pode usar a palavra-chave [await](../../csharp/language-reference/operators/await.md) em C# e o [Operador Await](../../visual-basic/language-reference/operators/await-operator.md) no Visual Basic para aguardar os objetos <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601> de modo assíncrono.</span><span class="sxs-lookup"><span data-stu-id="50a41-107">Starting with the .NET Framework 4.5, you can use the [await](../../csharp/language-reference/operators/await.md) keyword in C# and the [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="50a41-108">Quando você está aguardando um <xref:System.Threading.Tasks.Task>, a expressão `await` é do tipo `void`.</span><span class="sxs-lookup"><span data-stu-id="50a41-108">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="50a41-109">Quando você está aguardando um <xref:System.Threading.Tasks.Task%601>, a expressão `await` é do tipo `TResult`.</span><span class="sxs-lookup"><span data-stu-id="50a41-109">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="50a41-110">Uma expressão `await` deve ocorrer dentro do corpo de um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="50a41-110">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="50a41-111">Para obter mais informações sobre suporte às linguagens C# e Visual Basic no .NET Framework 4.5, consulte as especificações das linguagens C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="50a41-111">For more information about C# and Visual Basic language support in the .NET Framework 4.5, see the C# and Visual Basic language specifications.</span></span>

 <span data-ttu-id="50a41-112">Nos bastidores, a funcionalidade await instala um retorno de chamada na tarefa pelo uso de uma continuação.</span><span class="sxs-lookup"><span data-stu-id="50a41-112">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="50a41-113">Esse retorno de chamada retoma o método assíncrono no ponto de suspensão.</span><span class="sxs-lookup"><span data-stu-id="50a41-113">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="50a41-114">Quando o método assíncrono é retomado, se a operação de espera foi concluída com êxito e era uma <xref:System.Threading.Tasks.Task%601>, o respectivo `TResult` é retornado.</span><span class="sxs-lookup"><span data-stu-id="50a41-114">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="50a41-115">Se o <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> que foi aguardado terminou no estado <xref:System.Threading.Tasks.TaskStatus.Canceled>, uma exceção <xref:System.OperationCanceledException> será lançada.</span><span class="sxs-lookup"><span data-stu-id="50a41-115">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="50a41-116">Se o <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> que foi aguardado terminou no estado <xref:System.Threading.Tasks.TaskStatus.Faulted>, uma exceção que causou a falha será lançada.</span><span class="sxs-lookup"><span data-stu-id="50a41-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="50a41-117">Uma `Task` pode falhar como resultado de várias exceções, mas apenas uma dessas exceções é propagada.</span><span class="sxs-lookup"><span data-stu-id="50a41-117">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="50a41-118">No entanto, a propriedade <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> retorna uma exceção <xref:System.AggregateException> que contém todos os erros.</span><span class="sxs-lookup"><span data-stu-id="50a41-118">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="50a41-119">Se um contexto de sincronização (objeto <xref:System.Threading.SynchronizationContext>) é associado ao thread que estava executando o método assíncrono no momento da suspensão (por exemplo, se a propriedade <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> não é `null`), o método assíncrono é retomado no mesmo contexto de sincronização usando o método <xref:System.Threading.SynchronizationContext.Post%2A> do contexto.</span><span class="sxs-lookup"><span data-stu-id="50a41-119">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context’s <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="50a41-120">Caso contrário, ele utiliza o Agendador de Tarefas (objeto <xref:System.Threading.Tasks.TaskScheduler>) que era atual no momento da suspensão.</span><span class="sxs-lookup"><span data-stu-id="50a41-120">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="50a41-121">Normalmente, esse é que o agendador de tarefas padrão (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), que tem como alvo o pool de threads.</span><span class="sxs-lookup"><span data-stu-id="50a41-121">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="50a41-122">O Agendador de Tarefas determina se a operação assíncrona aguardada deve continuar do ponto em que foi concluída ou se a retomada deve ser agendada.</span><span class="sxs-lookup"><span data-stu-id="50a41-122">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="50a41-123">O agendador padrão geralmente permite que a continuação seja executada no thread em que a operação aguardada foi concluída.</span><span class="sxs-lookup"><span data-stu-id="50a41-123">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="50a41-124">Quando um método assíncrono é chamado, ele executa o corpo da função de modo síncrono até a primeira expressão await em uma instância aguardável que ainda não tenha foi concluída, no ponto em que a invocação retorna ao chamador.</span><span class="sxs-lookup"><span data-stu-id="50a41-124">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="50a41-125">Se o método assíncrono não retornar `void`, um objeto <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> será retornado para representar o cálculo em andamento.</span><span class="sxs-lookup"><span data-stu-id="50a41-125">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="50a41-126">Em um método assíncrono não nulo, se uma instrução return for encontrada ou o final do corpo do método for atingido, a tarefa será concluída no estado final <xref:System.Threading.Tasks.TaskStatus.RanToCompletion>.</span><span class="sxs-lookup"><span data-stu-id="50a41-126">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="50a41-127">Se uma exceção sem tratamento fizer com que o controle deixe o corpo do método assíncrono, a tarefa terminará no estado <xref:System.Threading.Tasks.TaskStatus.Faulted>.</span><span class="sxs-lookup"><span data-stu-id="50a41-127">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="50a41-128">Se essa exceção for um <xref:System.OperationCanceledException>, a tarefa terminará no estado <xref:System.Threading.Tasks.TaskStatus.Canceled>.</span><span class="sxs-lookup"><span data-stu-id="50a41-128">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="50a41-129">Dessa maneira, a exceção ou o resultado é eventualmente publicado.</span><span class="sxs-lookup"><span data-stu-id="50a41-129">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="50a41-130">Há diversas variações importantes desse comportamento.</span><span class="sxs-lookup"><span data-stu-id="50a41-130">There are several important variations of this behavior.</span></span>  <span data-ttu-id="50a41-131">Por motivos de desempenho, se uma tarefa já foi concluída até o momento em que a tarefa é aguardada, o controle não é suspenso e a função continua a executar.</span><span class="sxs-lookup"><span data-stu-id="50a41-131">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="50a41-132">Além disso, retornar para o contexto original nem sempre é o comportamento desejado e pode ser alterado; isso é descrito mais detalhadamente na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="50a41-132">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="50a41-133">Configurando a suspensão e retomada com Yield e ConfigureAwait</span><span class="sxs-lookup"><span data-stu-id="50a41-133">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>
 <span data-ttu-id="50a41-134">Vários métodos fornecem mais controle sobre a execução de um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="50a41-134">Several methods provide more control over an asynchronous method’s execution.</span></span> <span data-ttu-id="50a41-135">Por exemplo, você pode usar o método <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> para introduzir um ponto de rendimento para o método assíncrono:</span><span class="sxs-lookup"><span data-stu-id="50a41-135">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="50a41-136">Isso é equivalente a postar assincronamente ou agendar de volta para o contexto atual.</span><span class="sxs-lookup"><span data-stu-id="50a41-136">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 <span data-ttu-id="50a41-137">Você também pode usar o método <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> para controlar melhor a suspensão e a retomada de um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="50a41-137">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="50a41-138">Conforme mencionado anteriormente, por padrão, o contexto atual é capturado no momento em que um método assíncrono é suspenso e esse contexto capturado é usado para invocar a continuação do método assíncrono após a retomada.</span><span class="sxs-lookup"><span data-stu-id="50a41-138">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method’s continuation upon resumption.</span></span>  <span data-ttu-id="50a41-139">Em muitos casos, esse é o comportamento exato desejado.</span><span class="sxs-lookup"><span data-stu-id="50a41-139">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="50a41-140">Em outros casos, você pode não se importar com o contexto de continuação e pode obter o melhor desempenho ao evitar essas postagens de volta para o contexto original.</span><span class="sxs-lookup"><span data-stu-id="50a41-140">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="50a41-141">Para habilitar isso, use o método <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> para informar à operação de espera que não capture e retome no contexto, mas sim continue a execução no ponto em que a operação assíncrona que estava sendo aguardada foi concluída, seja qual for esse ponto:</span><span class="sxs-lookup"><span data-stu-id="50a41-141">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="50a41-142">Cancelando uma operação assíncrona</span><span class="sxs-lookup"><span data-stu-id="50a41-142">Canceling an Asynchronous Operation</span></span>
 <span data-ttu-id="50a41-143">A partir do NET Framework 4, os métodos TAP que dão suporte ao cancelamento fornecem pelo menos uma sobrecarga que aceita um token de cancelamento (objeto <xref:System.Threading.CancellationToken>).</span><span class="sxs-lookup"><span data-stu-id="50a41-143">Starting with the .NET Framework 4, TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="50a41-144">Um token de cancelamento é criado por meio de uma origem de token de cancelamento (objeto <xref:System.Threading.CancellationTokenSource>).</span><span class="sxs-lookup"><span data-stu-id="50a41-144">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="50a41-145">A propriedade <xref:System.Threading.CancellationTokenSource.Token%2A> da fonte retorna o token de cancelamento que sinalizará quando o método <xref:System.Threading.CancellationTokenSource.Cancel%2A> da fonte será chamado.</span><span class="sxs-lookup"><span data-stu-id="50a41-145">The source’s <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="50a41-146">Por exemplo, se você desejar baixar uma única página da Web e você deseja ser capaz de cancelar a operação, crie um objeto <xref:System.Threading.CancellationTokenSource>, passe o token desse objeto para o método TAP e, em seguida, chame o método <xref:System.Threading.CancellationTokenSource.Cancel%2A> da origem quando estiver pronto para cancelar a operação:</span><span class="sxs-lookup"><span data-stu-id="50a41-146">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="50a41-147">Para cancelar várias invocações assíncronas, você pode passar o mesmo token para todas as invocações:</span><span class="sxs-lookup"><span data-stu-id="50a41-147">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="50a41-148">Ou então, você pode passar o mesmo token para um subconjunto seletivo de operações:</span><span class="sxs-lookup"><span data-stu-id="50a41-148">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="50a41-149">Solicitações de cancelamento podem ser iniciadas de qualquer thread.</span><span class="sxs-lookup"><span data-stu-id="50a41-149">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="50a41-150">Você pode passar o valor <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> a qualquer método que aceite um token de cancelamento para indicar que o cancelamento nunca será solicitado.</span><span class="sxs-lookup"><span data-stu-id="50a41-150">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="50a41-151">Isso faz a propriedade <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> retornar `false`, e o método chamado pode ser otimizado adequadamente.</span><span class="sxs-lookup"><span data-stu-id="50a41-151">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="50a41-152">Para fins de teste, você também pode passar um token de cancelamento previamente cancelado que é instanciado pelo uso do construtor que aceita um valor booliano para indicar se o token deve iniciar em um estado não cancelável ou já cancelado.</span><span class="sxs-lookup"><span data-stu-id="50a41-152">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="50a41-153">Essa abordagem para o cancelamento tem várias vantagens:</span><span class="sxs-lookup"><span data-stu-id="50a41-153">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="50a41-154">Você pode passar o mesmo token de cancelamento para qualquer número de operações síncronas e assíncronas.</span><span class="sxs-lookup"><span data-stu-id="50a41-154">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="50a41-155">A mesma solicitação de cancelamento pode ser proliferada para qualquer número de ouvintes.</span><span class="sxs-lookup"><span data-stu-id="50a41-155">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="50a41-156">O desenvolvedor da API assíncrona tem total controle com relação ao cancelamento poder ou não ser solicitado e a quando isso pode entrar em vigor.</span><span class="sxs-lookup"><span data-stu-id="50a41-156">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="50a41-157">O código que consome a API pode, seletivamente, determinar as invocações assíncronas para as quais as solicitações de cancelamento serão propagadas.</span><span class="sxs-lookup"><span data-stu-id="50a41-157">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="50a41-158">Monitorando o progresso</span><span class="sxs-lookup"><span data-stu-id="50a41-158">Monitoring Progress</span></span>
 <span data-ttu-id="50a41-159">Alguns métodos assíncronos expõem progresso através de uma interface de progresso passada para o método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="50a41-159">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="50a41-160">Por exemplo, considere uma função que baixa de forma assíncrona uma cadeia de caracteres de texto e, durante esse processo, emite atualizações de progresso que incluem o percentual de download concluído até o momento.</span><span class="sxs-lookup"><span data-stu-id="50a41-160">For example, consider a function which asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="50a41-161">Tal método poderia ser consumido em um aplicativo do WPF (Windows Presentation Foundation) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="50a41-161">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="50a41-162">Usando os combinadores baseados em tarefas internos</span><span class="sxs-lookup"><span data-stu-id="50a41-162">Using the Built-in Task-based Combinators</span></span>
 <span data-ttu-id="50a41-163">O namespace <xref:System.Threading.Tasks> inclui vários métodos para compor tarefas e trabalhar com elas.</span><span class="sxs-lookup"><span data-stu-id="50a41-163">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="50a41-164">Task.Run</span><span class="sxs-lookup"><span data-stu-id="50a41-164">Task.Run</span></span>
 <span data-ttu-id="50a41-165">A classe <xref:System.Threading.Tasks.Task> inclui vários métodos <xref:System.Threading.Tasks.Task.Run%2A> que permitem descarregar com facilidade o trabalho como um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> para o pool de threads, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="50a41-165">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 <span data-ttu-id="50a41-166">Alguns desses métodos <xref:System.Threading.Tasks.Task.Run%2A>, como a sobrecarga de <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, existe como um atalho para o método <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="50a41-166">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="50a41-167">Outras sobrecargas, como <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, permitem que você use await dentro do trabalho descarregado, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="50a41-167">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 <span data-ttu-id="50a41-168">Essas sobrecargas são logicamente equivalentes a usar o método <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> junto com o método de extensão <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> na biblioteca de paralelismo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="50a41-168">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="50a41-169">Task.FromResult</span><span class="sxs-lookup"><span data-stu-id="50a41-169">Task.FromResult</span></span>
 <span data-ttu-id="50a41-170">Use o método <xref:System.Threading.Tasks.Task.FromResult%2A> em cenários nos quais os dados talvez já estejam disponíveis e apenas precisem ser retornados de um método de retorno de tarefas elevado para uma <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="50a41-170">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a><span data-ttu-id="50a41-171">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="50a41-171">Task.WhenAll</span></span>
 <span data-ttu-id="50a41-172">Use o método <xref:System.Threading.Tasks.Task.WhenAll%2A> para aguardar de forma assíncrona várias operações assíncronas que são representadas como tarefas.</span><span class="sxs-lookup"><span data-stu-id="50a41-172">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="50a41-173">O método tem várias sobrecargas que dão suporte a um conjunto de tarefas não genéricas ou um conjunto não uniforme de tarefas genéricas (por exemplo, aguardar de forma assíncrona várias operações que retornam nulo ou aguardar vários métodos que retornam um valor em que cada valor pode ter um tipo diferente) e dão suporte a um conjunto uniforme de tarefas genéricas (como aguardar de forma assíncrona vários métodos que retornam `TResult`).</span><span class="sxs-lookup"><span data-stu-id="50a41-173">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="50a41-174">Digamos que você deseja enviar mensagens de email para vários clientes.</span><span class="sxs-lookup"><span data-stu-id="50a41-174">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="50a41-175">Você pode sobrepor o envio de mensagens de modo que você não aguarde a conclusão de uma mensagem antes de enviar a próxima.</span><span class="sxs-lookup"><span data-stu-id="50a41-175">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="50a41-176">Você também pode descobrir quando as operações de envio foram concluídas e se ocorreu algum erro:</span><span class="sxs-lookup"><span data-stu-id="50a41-176">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="50a41-177">Esse código não tratará explicitamente exceções que possam ocorrer, mas permitirá que as exceções sejam propagadas para fora do `await` na tarefa resultante de <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="50a41-177">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="50a41-178">Para tratar as exceções, você pode usar código como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="50a41-178">To handle the exceptions, you can use code such as the following:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 <span data-ttu-id="50a41-179">Nesse caso, se alguma operação assíncrona falhar, todas as exceções serão consolidadas em uma exceção <xref:System.AggregateException>, que é armazenada no <xref:System.Threading.Tasks.Task> que é retornado do método <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="50a41-179">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="50a41-180">No entanto, apenas uma dessas exceções é propagada pela palavra-chave `await`.</span><span class="sxs-lookup"><span data-stu-id="50a41-180">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="50a41-181">Se você quiser examinar todas as exceções, poderá reescrever o código anterior da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="50a41-181">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 <span data-ttu-id="50a41-182">Vamos considerar um exemplo em que baixamos vários arquivos da Web de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="50a41-182">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="50a41-183">Nesse caso, todas as operações assíncronas têm tipos de resultado homogêneos e é fácil acessar os resultados:</span><span class="sxs-lookup"><span data-stu-id="50a41-183">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="50a41-184">Você pode usar as mesmas técnicas de tratamento de exceções discutidas no cenário anterior, em que nulo é retornado:</span><span class="sxs-lookup"><span data-stu-id="50a41-184">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

```csharp
Task [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a><span data-ttu-id="50a41-185">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="50a41-185">Task.WhenAny</span></span>
 <span data-ttu-id="50a41-186">Você pode usar o método <xref:System.Threading.Tasks.Task.WhenAny%2A> para aguardar de forma assíncrona apenas uma de várias operações assíncronas que são representadas como tarefas.</span><span class="sxs-lookup"><span data-stu-id="50a41-186">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="50a41-187">Esse método tem quatro casos de uso principais:</span><span class="sxs-lookup"><span data-stu-id="50a41-187">This method serves four primary use cases:</span></span>

- <span data-ttu-id="50a41-188">Redundância:  executar uma operação várias vezes e selecionar aquela que termina primeiro (por exemplo, entrando em contato com vários serviços Web de cotação de ações que produzirão um único resultado e selecionar aquele que termina mais rápido).</span><span class="sxs-lookup"><span data-stu-id="50a41-188">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="50a41-189">Intercalação:  iniciar várias operações e aguardar que todas elas sejam concluídas, mas processando-as conforme são concluídas.</span><span class="sxs-lookup"><span data-stu-id="50a41-189">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="50a41-190">Limitação:  permitir que operações adicionais comecem conforme outras forem concluídas.</span><span class="sxs-lookup"><span data-stu-id="50a41-190">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="50a41-191">Essa é uma extensão do cenário de intercalação.</span><span class="sxs-lookup"><span data-stu-id="50a41-191">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="50a41-192">Esgotamento precoce:  por exemplo, uma operação representada pela tarefa t1 pode ser agrupada em uma tarefa <xref:System.Threading.Tasks.Task.WhenAny%2A> com outra tarefa t2. Você pode esperar a tarefa <xref:System.Threading.Tasks.Task.WhenAny%2A>.</span><span class="sxs-lookup"><span data-stu-id="50a41-192">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="50a41-193">A tarefa t2 pode representar um tempo limite, um cancelamento ou algum outro sinal que faça com que a tarefa <xref:System.Threading.Tasks.Task.WhenAny%2A> seja concluída antes de t1.</span><span class="sxs-lookup"><span data-stu-id="50a41-193">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="50a41-194">Redundância</span><span class="sxs-lookup"><span data-stu-id="50a41-194">Redundancy</span></span>
 <span data-ttu-id="50a41-195">Considere um caso em que você deseja tomar uma decisão sobre a possibilidade de comprar uma ação.</span><span class="sxs-lookup"><span data-stu-id="50a41-195">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="50a41-196">Há diversos serviços Web de recomendação de compra de ações nos quais você confia, mas dependendo da carga diária, cada serviço pode acabar sendo lento em horários diferentes.</span><span class="sxs-lookup"><span data-stu-id="50a41-196">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="50a41-197">Você pode usar o método <xref:System.Threading.Tasks.Task.WhenAny%2A> para receber uma notificação quando qualquer operação for concluída:</span><span class="sxs-lookup"><span data-stu-id="50a41-197">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 <span data-ttu-id="50a41-198">Ao contrário de <xref:System.Threading.Tasks.Task.WhenAll%2A>, que retorna os resultados não encapsulados de todas as tarefas concluídas com êxito, o <xref:System.Threading.Tasks.Task.WhenAny%2A> retorna a tarefa que foi concluída.</span><span class="sxs-lookup"><span data-stu-id="50a41-198">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="50a41-199">Se uma tarefa falhar, será importante saber que ela falhou e, se uma tarefa for bem-sucedida, será importante saber a qual tarefa o valor retornado é associado.</span><span class="sxs-lookup"><span data-stu-id="50a41-199">If a task fails, it’s important to know that it failed, and if a task succeeds, it’s important to know which task the return value is associated with.</span></span>  <span data-ttu-id="50a41-200">Portanto, você precisa acessar o resultado da tarefa retornada ou aguardá-la ainda mais, conforme mostra este exemplo.</span><span class="sxs-lookup"><span data-stu-id="50a41-200">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="50a41-201">Assim como acontece com o <xref:System.Threading.Tasks.Task.WhenAll%2A>, você precisa ser capaz de acomodar as exceções.</span><span class="sxs-lookup"><span data-stu-id="50a41-201">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="50a41-202">Devido a você receber novamente a tarefa concluída, você poderá esperar a tarefa retornada para então propagar os erros e aplicar `try/catch` a eles adequadamente; por exemplo:</span><span class="sxs-lookup"><span data-stu-id="50a41-202">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 <span data-ttu-id="50a41-203">Além disso, mesmo que uma primeira tarefa seja concluída com êxito, as tarefas subsequentes poderão falhar.</span><span class="sxs-lookup"><span data-stu-id="50a41-203">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="50a41-204">Neste ponto, você tem várias opções para lidar com exceções:  Você pode esperar até que todas as tarefas iniciadas sejam concluídas, caso em que você pode usar o método <xref:System.Threading.Tasks.Task.WhenAll%2A>, ou pode decidir que todas as exceções são importantes e devem ser registradas em log.</span><span class="sxs-lookup"><span data-stu-id="50a41-204">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="50a41-205">Para isso, você pode usar as continuações para receber uma notificação quando tarefas foram concluídas de forma assíncrona:</span><span class="sxs-lookup"><span data-stu-id="50a41-205">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="50a41-206">ou:</span><span class="sxs-lookup"><span data-stu-id="50a41-206">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="50a41-207">ou até mesmo:</span><span class="sxs-lookup"><span data-stu-id="50a41-207">or even:</span></span>

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 <span data-ttu-id="50a41-208">Finalmente, você talvez queira cancelar todas as operações restantes:</span><span class="sxs-lookup"><span data-stu-id="50a41-208">Finally, you may want to cancel all the remaining operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a><span data-ttu-id="50a41-209">Intercalação</span><span class="sxs-lookup"><span data-stu-id="50a41-209">Interleaving</span></span>
 <span data-ttu-id="50a41-210">Considere um caso em que você está baixando imagens da Web e processando cada imagem (por exemplo, adicionando a imagem a um controle de interface do usuário).</span><span class="sxs-lookup"><span data-stu-id="50a41-210">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span>  <span data-ttu-id="50a41-211">Você precisa fazer o processamento sequencialmente no thread da interface do usuário, mas você quer baixar as imagens tão simultaneamente quanto possível.</span><span class="sxs-lookup"><span data-stu-id="50a41-211">You have to do the processing sequentially on the UI thread, but you want to download the images as concurrently as possible.</span></span> <span data-ttu-id="50a41-212">Além disso, você não deseja esperar para adicionar as imagens à interface do usuário após elas serem todas baixadas – você deseja adicioná-las conforme o download de cada uma delas é concluído:</span><span class="sxs-lookup"><span data-stu-id="50a41-212">Also, you don’t want to hold up adding the images to the UI until they’re all downloaded—you want to add them as they complete:</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 <span data-ttu-id="50a41-213">Você também pode aplicar interpolação para um cenário que envolve o processamento de recursos computacionais no <xref:System.Threading.ThreadPool> das imagens baixadas; por exemplo:</span><span class="sxs-lookup"><span data-stu-id="50a41-213">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a><span data-ttu-id="50a41-214">Limitação</span><span class="sxs-lookup"><span data-stu-id="50a41-214">Throttling</span></span>
 <span data-ttu-id="50a41-215">Considere o exemplo de intercalação, exceto que o usuário está baixando um número tão grande de imagens que os downloads precisam ser limitados; por exemplo, você deseja que apenas um número específico de downloads ocorram simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="50a41-215">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="50a41-216">Para conseguir isso, você pode iniciar um subconjunto das operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="50a41-216">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="50a41-217">Conforme as operações forem concluídas, você pode iniciar operações adicionais para assumir o lugar delas:</span><span class="sxs-lookup"><span data-stu-id="50a41-217">As operations complete, you can start additional operations to take their place:</span></span>

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a><span data-ttu-id="50a41-218">Saída precoce</span><span class="sxs-lookup"><span data-stu-id="50a41-218">Early Bailout</span></span>
 <span data-ttu-id="50a41-219">Considere a possibilidade de que você está aguardando de forma assíncrona que uma operação seja concluída e, simultaneamente, respondendo a uma solicitação de cancelamento do usuário (por exemplo, o usuário clicou em um botão para cancelar).</span><span class="sxs-lookup"><span data-stu-id="50a41-219">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user’s cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="50a41-220">O código a seguir ilustra esse cenário:</span><span class="sxs-lookup"><span data-stu-id="50a41-220">The following code illustrates this scenario:</span></span>

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 <span data-ttu-id="50a41-221">Essa implementação reabilita a interface do usuário assim que você decide sair, mas não as cancela as operações assíncronas subjacentes.</span><span class="sxs-lookup"><span data-stu-id="50a41-221">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span>  <span data-ttu-id="50a41-222">Outra alternativa seria cancelar as operações pendentes quando você decide sair, mas não restabelecer a interface do usuário até que as operações sejam realmente concluídas, possivelmente devido a um encerramento precoce devido à solicitação de cancelamento:</span><span class="sxs-lookup"><span data-stu-id="50a41-222">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations actually complete, potentially due to ending early due to the cancellation request:</span></span>

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 <span data-ttu-id="50a41-223">Outro exemplo de saída precoce envolve o uso do método <xref:System.Threading.Tasks.Task.WhenAny%2A> junto com o método <xref:System.Threading.Tasks.Task.Delay%2A>, conforme discutido na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="50a41-223">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="50a41-224">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="50a41-224">Task.Delay</span></span>
 <span data-ttu-id="50a41-225">Você pode usar o método <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> para apresentar pausas em uma execução de um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="50a41-225">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method’s execution.</span></span>  <span data-ttu-id="50a41-226">Isso é útil para muitos tipos de funcionalidades, incluindo o build de loops de sondagem e o atraso da manipulação da entrada do usuário por um período de tempo predeterminado.</span><span class="sxs-lookup"><span data-stu-id="50a41-226">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="50a41-227">O método <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> também pode ser útil em combinação com o <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> para implementação de tempos limite em esperas.</span><span class="sxs-lookup"><span data-stu-id="50a41-227">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="50a41-228">Se uma tarefa que for parte de uma operação assíncrona maior (por exemplo, um serviço Web ASP.NET) levar muito tempo para concluir, a operação geral poderá ser afetada, especialmente se ela falhar e nunca for concluída.</span><span class="sxs-lookup"><span data-stu-id="50a41-228">If a task that’s part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="50a41-229">Por esse motivo, é importante ser capaz de atingir o tempo limite ao aguardar uma operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="50a41-229">For this reason, it’s important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="50a41-230">Os métodos <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> aceitam valores de tempo limite, mas os correspondentes <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> e os métodos <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> mencionados anteriormente não.</span><span class="sxs-lookup"><span data-stu-id="50a41-230">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="50a41-231">Em vez disso, você pode usar <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> em conjunto para implementar um tempo limite.</span><span class="sxs-lookup"><span data-stu-id="50a41-231">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="50a41-232">Por exemplo, em seu aplicativo de interface do usuário, digamos que você deseja baixar uma imagem e desabilitar a interface do usuário durante esse download.</span><span class="sxs-lookup"><span data-stu-id="50a41-232">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="50a41-233">No entanto, se o download levar muito tempo, você desejará reabilitar a interface do usuário e descartar o download:</span><span class="sxs-lookup"><span data-stu-id="50a41-233">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 <span data-ttu-id="50a41-234">O mesmo aplica-se a vários downloads, porque <xref:System.Threading.Tasks.Task.WhenAll%2A> retorna uma tarefa:</span><span class="sxs-lookup"><span data-stu-id="50a41-234">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a><span data-ttu-id="50a41-235">Compilando combinadores baseados em tarefa</span><span class="sxs-lookup"><span data-stu-id="50a41-235">Building Task-based Combinators</span></span>
 <span data-ttu-id="50a41-236">Já que uma tarefa é capaz de representar totalmente uma operação assíncrona e fornecer recursos síncronos e assíncronos para ingressar na operação, recuperar seus resultados e assim por diante, você pode compilar bibliotecas úteis de combinadores que compõem tarefas para compilar padrões maiores.</span><span class="sxs-lookup"><span data-stu-id="50a41-236">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span>  <span data-ttu-id="50a41-237">Conforme discutido na seção anterior, o .NET Framework inclui vários combinadores internos, mas você também pode compilar os seus próprios combinadores.</span><span class="sxs-lookup"><span data-stu-id="50a41-237">As discussed in the previous section, the .NET Framework includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="50a41-238">As seções a seguir fornecem vários exemplos de tipos e métodos combinadores potenciais.</span><span class="sxs-lookup"><span data-stu-id="50a41-238">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="50a41-239">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="50a41-239">RetryOnFault</span></span>
 <span data-ttu-id="50a41-240">Em muitas situações, talvez você queira repetir uma operação se uma tentativa anterior falhar.</span><span class="sxs-lookup"><span data-stu-id="50a41-240">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="50a41-241">Para código síncrono, você pode compilar um método auxiliar como `RetryOnFault` no exemplo a seguir para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="50a41-241">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="50a41-242">Você pode compilar um método auxiliar quase idêntico para operações assíncronas implementadas com TAP e, assim, retornar tarefas:</span><span class="sxs-lookup"><span data-stu-id="50a41-242">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="50a41-243">Você pode usar este combinador para codificar repetições na lógica do aplicativo, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="50a41-243">You can then use this combinator to encode retries into the application’s logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="50a41-244">Você pode estender ainda mais a função `RetryOnFault`.</span><span class="sxs-lookup"><span data-stu-id="50a41-244">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="50a41-245">Por exemplo, a função poderá aceitar outro `Func<Task>` que será invocado entre as tentativas para determinar quando tentar novamente a operação, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="50a41-245">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 <span data-ttu-id="50a41-246">Você pode então usar a função da seguinte maneira, para aguardar um segundo antes de repetir a operação:</span><span class="sxs-lookup"><span data-stu-id="50a41-246">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="50a41-247">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="50a41-247">NeedOnlyOne</span></span>
 <span data-ttu-id="50a41-248">Às vezes, você pode tirar proveito da redundância para melhorar a latência e as chances de sucesso de uma operação.</span><span class="sxs-lookup"><span data-stu-id="50a41-248">Sometimes, you can take advantage of redundancy to improve an operation’s latency and chances for success.</span></span>  <span data-ttu-id="50a41-249">Considere vários serviços Web que fornecem cotações de ações, mas em diferentes horas do dia, cada serviço pode fornecer diferentes níveis de qualidade e tempos de resposta.</span><span class="sxs-lookup"><span data-stu-id="50a41-249">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="50a41-250">Para lidar com essas flutuações, você poderá emitir solicitações para todos os serviços Web e, assim que você obtiver uma resposta de um deles, cancelar as solicitações restantes.</span><span class="sxs-lookup"><span data-stu-id="50a41-250">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="50a41-251">Você pode implementar uma função auxiliar para facilitar a implementação desse padrão comum de inicialização de várias operações, aguardar uma delas e, em seguida, cancelar o restante.</span><span class="sxs-lookup"><span data-stu-id="50a41-251">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="50a41-252">A função `NeedOnlyOne` no exemplo a seguir ilustra esse cenário:</span><span class="sxs-lookup"><span data-stu-id="50a41-252">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 <span data-ttu-id="50a41-253">Você pode então usar essa função conforme demonstrado a seguir:</span><span class="sxs-lookup"><span data-stu-id="50a41-253">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="50a41-254">Operações intercaladas</span><span class="sxs-lookup"><span data-stu-id="50a41-254">Interleaved Operations</span></span>
 <span data-ttu-id="50a41-255">Há um problema de desempenho potencial com o uso do método <xref:System.Threading.Tasks.Task.WhenAny%2A> para dar suporte a um cenário de intercalação quando você está trabalhando com grandes conjuntos de tarefas.</span><span class="sxs-lookup"><span data-stu-id="50a41-255">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with very large sets of tasks.</span></span>  <span data-ttu-id="50a41-256">Todas as chamadas para <xref:System.Threading.Tasks.Task.WhenAny%2A> fazem uma continuação ser registrada com cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="50a41-256">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="50a41-257">Para um número N de tarefas, isso resulta em O(N2) continuações criadas durante o tempo de vida da operação de intercalação.</span><span class="sxs-lookup"><span data-stu-id="50a41-257">For N number of tasks, this results in O(N2) continuations created over the lifetime of the interleaving operation.</span></span>  <span data-ttu-id="50a41-258">Se você estiver trabalhando com um grande conjunto de tarefas, você poderá usar um combinador (`Interleaved` no exemplo a seguir) para solucionar o problema de desempenho:</span><span class="sxs-lookup"><span data-stu-id="50a41-258">If you're working with a large set of tasks, you can use a combinator  (`Interleaved` in the following example) to address the performance issue:</span></span>

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 <span data-ttu-id="50a41-259">Você poderá usar o combinador para processar os resultados das tarefas conforme elas forem concluídas, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="50a41-259">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="50a41-260">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="50a41-260">WhenAllOrFirstException</span></span>
 <span data-ttu-id="50a41-261">Em determinados cenários de dispersão/coleta, convém esperar por todas as tarefas em um conjunto, a menos que uma delas falhe, caso em que você desejará interromper a espera assim que a exceção ocorrer.</span><span class="sxs-lookup"><span data-stu-id="50a41-261">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="50a41-262">Você pode realizar isso com um método combinador tal como `WhenAllOrFirstException` no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="50a41-262">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a><span data-ttu-id="50a41-263">Compilando estruturas de dados com base em tarefa</span><span class="sxs-lookup"><span data-stu-id="50a41-263">Building Task-based Data Structures</span></span>
 <span data-ttu-id="50a41-264">Além da capacidade de compilar combinadores baseados em tarefas personalizados, ter uma estrutura de dados em <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601>, que representa tanto os resultados de uma operação assíncrona quanto a sincronização necessária para unir a ela, torna esse um tipo muito poderoso no qual compilar estruturas de dados personalizadas a serem usados em cenários assíncronos.</span><span class="sxs-lookup"><span data-stu-id="50a41-264">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a very powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="50a41-265">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="50a41-265">AsyncCache</span></span>
 <span data-ttu-id="50a41-266">Um aspecto importante de uma tarefa é que ela pode ser enviada para vários consumidores, todos os quais podem esperar por ela, registrar continuações com ela, obter seu resultado ou exceções (no caso de <xref:System.Threading.Tasks.Task%601>) e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="50a41-266">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="50a41-267">Isso torna <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601> perfeitamente adequado para ser usado em uma infraestrutura de cache assíncrona.</span><span class="sxs-lookup"><span data-stu-id="50a41-267">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="50a41-268">Aqui está um exemplo de um cache assíncrono pequeno mas poderoso, construído com base na <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="50a41-268">Here’s an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 <span data-ttu-id="50a41-269">A classe [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) aceita, como delegado para o seu construtor, uma função que recebe um `TKey` e retorna um <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="50a41-269">The [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="50a41-270">Quaisquer valores do cache previamente acessados são armazenados no dicionário interno e `AsyncCache` garante que apenas uma tarefa seja gerada por chave, mesmo que o cache seja acessado simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="50a41-270">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="50a41-271">Por exemplo, você pode compilar um cache para páginas da Web baixadas:</span><span class="sxs-lookup"><span data-stu-id="50a41-271">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="50a41-272">Você pode em seguida usar esse cache em métodos assíncronos sempre que precisar do conteúdo de uma página da Web.</span><span class="sxs-lookup"><span data-stu-id="50a41-272">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="50a41-273">A classe `AsyncCache` garante que você esteja baixando o mínimo possível de páginas e armazena os resultados em cache.</span><span class="sxs-lookup"><span data-stu-id="50a41-273">The `AsyncCache` class ensures that you’re downloading as few pages as possible, and caches the results.</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="50a41-274">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="50a41-274">AsyncProducerConsumerCollection</span></span>
 <span data-ttu-id="50a41-275">Você também pode usar tarefas para compilar estruturas de dados para coordenar atividades assíncronas.</span><span class="sxs-lookup"><span data-stu-id="50a41-275">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="50a41-276">Considere um dos padrões de design paralelos clássicos: produtor/consumidor.</span><span class="sxs-lookup"><span data-stu-id="50a41-276">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="50a41-277">Nesse padrão, produtores geram dados que são consumidos pelos consumidores e produtores e consumidores podem executar em paralelo.</span><span class="sxs-lookup"><span data-stu-id="50a41-277">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="50a41-278">Por exemplo, o consumidor processa o item 1, que anteriormente foi gerado por um produtor que agora está produzindo o item 2.</span><span class="sxs-lookup"><span data-stu-id="50a41-278">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="50a41-279">Para o padrão de produtor/consumidor, você precisa invariavelmente que alguma estrutura de dados armazene o trabalho criado pelos produtores para que os consumidores possam ser notificados sobre novos dados e localizá-los quando disponíveis.</span><span class="sxs-lookup"><span data-stu-id="50a41-279">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="50a41-280">Eis aqui uma estrutura de dados simples criada sobre tarefas que permitem que os métodos assíncronos sejam usados como produtores e consumidores:</span><span class="sxs-lookup"><span data-stu-id="50a41-280">Here’s a simple data structure built on top of tasks that enables asynchronous methods to be used as producers and consumers:</span></span>

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 <span data-ttu-id="50a41-281">Com essa estrutura de dados estabelecida, você pode escrever código como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="50a41-281">With that data structure in place, you can write code such as the following:</span></span>

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

<span data-ttu-id="50a41-282">O namespace <xref:System.Threading.Tasks.Dataflow> inclui o tipo <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>, que pode ser usado de maneira semelhante, mas sem a necessidade de criar um tipo de coleção personalizado:</span><span class="sxs-lookup"><span data-stu-id="50a41-282">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> <span data-ttu-id="50a41-283">O namespace <xref:System.Threading.Tasks.Dataflow> está disponível no .NET Framework 4.5 por meio de **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="50a41-283">The <xref:System.Threading.Tasks.Dataflow> namespace is available in the .NET Framework 4.5 through **NuGet**.</span></span> <span data-ttu-id="50a41-284">Para instalar o assembly que contém o namespace <xref:System.Threading.Tasks.Dataflow>, abra seu projeto no Visual Studio, escolha **Gerenciar Pacotes NuGet** no menu Projeto e procure online pelo pacote Microsoft.Tpl.Dataflow.</span><span class="sxs-lookup"><span data-stu-id="50a41-284">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the Microsoft.Tpl.Dataflow package.</span></span>

## <a name="see-also"></a><span data-ttu-id="50a41-285">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50a41-285">See also</span></span>

- [<span data-ttu-id="50a41-286">TAP (Padrão Assíncrono Baseado em Tarefa)</span><span class="sxs-lookup"><span data-stu-id="50a41-286">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="50a41-287">Implementando o padrão assíncrono baseado em tarefa</span><span class="sxs-lookup"><span data-stu-id="50a41-287">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="50a41-288">Interoperabilidade com outros tipos e padrões assíncronos</span><span class="sxs-lookup"><span data-stu-id="50a41-288">Interop with Other Asynchronous Patterns and Types</span></span>](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
