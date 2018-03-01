---
title: "Programação assíncrona em F #"
description: "Saiba como programação assíncrona em F # é realizada por meio de um modelo de programação de nível de linguagem natural para a linguagem e fácil de usar."
keywords: .NET, .NET Core
author: cartermp
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9196bfc-b8a8-4d33-8b53-0dcbd58a69d8
ms.openlocfilehash: c3fde46e804b7acac78d3ce5454a3c6f806e24e7
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="async-programming-in-f"></a><span data-ttu-id="4baca-104">Programação assíncrona em F #</span><span class="sxs-lookup"><span data-stu-id="4baca-104">Async Programming in F#</span></span> #

> [!NOTE]
> <span data-ttu-id="4baca-105">Alguns imprecisões foram descobertos neste artigo.</span><span class="sxs-lookup"><span data-stu-id="4baca-105">Some inaccuracies have been discovered in this article.</span></span>  <span data-ttu-id="4baca-106">Ele está sendo reconfigurado.</span><span class="sxs-lookup"><span data-stu-id="4baca-106">It is being rewritten.</span></span>  <span data-ttu-id="4baca-107">Consulte [problema #666](https://github.com/dotnet/docs/issues/666) para saber mais sobre as alterações.</span><span class="sxs-lookup"><span data-stu-id="4baca-107">See [Issue #666](https://github.com/dotnet/docs/issues/666) to learn about the changes.</span></span>

<span data-ttu-id="4baca-108">Programação em F # assíncrona pode ser feita por meio de um modelo de programação de nível de linguagem foi projetado para ser fácil de usar e a linguagem natural.</span><span class="sxs-lookup"><span data-stu-id="4baca-108">Async programming in F# can be accomplished through a language-level programming model designed to be easy to use and natural to the language.</span></span>

<span data-ttu-id="4baca-109">O núcleo de programação assíncrona em F # é `Async<'T>`, uma representação de trabalho que pode ser disparado para ser executado em segundo plano, onde `'T` é o tipo retornado por meio de especiais `return` palavra-chave ou `unit` se o fluxo de trabalho assíncrono não tem nenhum resultado a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="4baca-109">The core of async programming in F# is `Async<'T>`, a representation of work that can be triggered to run in the background, where `'T` is either the type returned via the special `return` keyword or `unit` if the async workflow has no result to return.</span></span>

<span data-ttu-id="4baca-110">O conceito de chave para entender é que o tipo da expressão um async é `Async<'T>`, que é simplesmente uma _especificação_ do trabalho a ser feito em um contexto assíncrono.</span><span class="sxs-lookup"><span data-stu-id="4baca-110">The key concept to understand is that an async expression’s type is `Async<'T>`, which is merely a _specification_ of work to be done in an asynchronous context.</span></span> <span data-ttu-id="4baca-111">Não será executado até que você o inicie explicitamente com uma das funções iniciais (como `Async.RunSynchronously`).</span><span class="sxs-lookup"><span data-stu-id="4baca-111">It is not executed until you explicitly start it with one of the starting functions (such as `Async.RunSynchronously`).</span></span> <span data-ttu-id="4baca-112">Embora essa seja uma maneira diferente de pensar sobre como fazer o trabalho, ele acaba sendo bem simples na prática.</span><span class="sxs-lookup"><span data-stu-id="4baca-112">Although this is a different way of thinking about doing work, it ends up being quite simple in practice.</span></span>

<span data-ttu-id="4baca-113">Por exemplo, digamos que você deseja baixar o HTML de dotnetfoundation.org sem bloquear o thread principal.</span><span class="sxs-lookup"><span data-stu-id="4baca-113">For example, say you wanted to download the HTML from dotnetfoundation.org without blocking the main thread.</span></span> <span data-ttu-id="4baca-114">Você pode fazer isso assim:</span><span class="sxs-lookup"><span data-stu-id="4baca-114">You can accomplish it like this:</span></span>

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()

        // Execution of fetchHtmlAsync won't continue until the result
        // of AsyncDownloadString is bound.
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

<span data-ttu-id="4baca-115">E pronto!</span><span class="sxs-lookup"><span data-stu-id="4baca-115">And that’s it!</span></span> <span data-ttu-id="4baca-116">Além do uso de `async`, `let!`, e `return`, isso é normal apenas código F #.</span><span class="sxs-lookup"><span data-stu-id="4baca-116">Aside from the use of `async`, `let!`, and `return`, this is just normal F# code.</span></span>

<span data-ttu-id="4baca-117">Há algumas construções sintáticas que vale a pena observar:</span><span class="sxs-lookup"><span data-stu-id="4baca-117">There are a few syntactical constructs which are worth noting:</span></span>

*   <span data-ttu-id="4baca-118">`let!` associa o resultado de uma expressão assíncrona (que é executado em outro contexto).</span><span class="sxs-lookup"><span data-stu-id="4baca-118">`let!` binds the result of an async expression (which runs on another context).</span></span>
*   <span data-ttu-id="4baca-119">`use!` funciona da mesma forma `let!`, mas descarta seus recursos associados quando ele sai do escopo.</span><span class="sxs-lookup"><span data-stu-id="4baca-119">`use!` works just like `let!`, but disposes its bound resources when it goes out of scope.</span></span>
*   <span data-ttu-id="4baca-120">`do!` irá esperar um fluxo de trabalho assíncrona que não retorna nada.</span><span class="sxs-lookup"><span data-stu-id="4baca-120">`do!` will await an async workflow which doesn’t return anything.</span></span>
*   <span data-ttu-id="4baca-121">`return` simplesmente retorna um resultado de uma expressão assíncrona.</span><span class="sxs-lookup"><span data-stu-id="4baca-121">`return` simply returns a result from an async expression.</span></span>
*   <span data-ttu-id="4baca-122">`return!` executa outro fluxo de trabalho assíncrono e retorna seu valor de retorno como resultado.</span><span class="sxs-lookup"><span data-stu-id="4baca-122">`return!` executes another async workflow and returns its return value as a result.</span></span>

<span data-ttu-id="4baca-123">Além disso, normal `let`, `use`, e `do` palavras-chave podem ser usadas junto com as versões assíncronas, como faria em uma função normal.</span><span class="sxs-lookup"><span data-stu-id="4baca-123">Additionally, normal `let`, `use`, and `do` keywords can be used alongside the async versions just as they would in a normal function.</span></span>

## <a name="how-to-start-async-code-in-f"></a><span data-ttu-id="4baca-124">Como iniciar o código assíncrono em F #</span><span class="sxs-lookup"><span data-stu-id="4baca-124">How to start Async Code in F#</span></span> #

<span data-ttu-id="4baca-125">Como mencionado anteriormente, o código assíncrono é uma especificação de trabalho a ser feito em outro contexto que deve ser iniciada explicitamente.</span><span class="sxs-lookup"><span data-stu-id="4baca-125">As mentioned earlier, async code is a specification of work to be done in another context which needs to be explicitly started.</span></span> <span data-ttu-id="4baca-126">Aqui estão duas maneiras principais para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="4baca-126">Here are two primary ways to accomplish this:</span></span>

1.  <span data-ttu-id="4baca-127">`Async.RunSynchronously` Inicie um fluxo de trabalho assíncrono em outro thread e await seu resultado.</span><span class="sxs-lookup"><span data-stu-id="4baca-127">`Async.RunSynchronously` will start an async workflow on another thread and await its result.</span></span>

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

 // Execution will pause until fetchHtmlAsync finishes
 let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2.  <span data-ttu-id="4baca-128">`Async.Start` irá iniciar um fluxo de trabalho assíncrono em outro thread e será **não** await seu resultado.</span><span class="sxs-lookup"><span data-stu-id="4baca-128">`Async.Start` will start an async workflow on another thread, and will **not** await its result.</span></span>

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

<span data-ttu-id="4baca-129">Existem outras maneiras de iniciar um fluxo de trabalho assíncrono disponível para cenários mais específicos.</span><span class="sxs-lookup"><span data-stu-id="4baca-129">There are other ways to start an async workflow available for more specific scenarios.</span></span> <span data-ttu-id="4baca-130">Elas são detalhadas [na referência de Async](https://msdn.microsoft.com/library/ee370232.aspx).</span><span class="sxs-lookup"><span data-stu-id="4baca-130">They are detailed [in the Async reference](https://msdn.microsoft.com/library/ee370232.aspx).</span></span>

### <a name="a-note-on-threads"></a><span data-ttu-id="4baca-131">Uma observação sobre Threads</span><span class="sxs-lookup"><span data-stu-id="4baca-131">A Note on Threads</span></span>

<span data-ttu-id="4baca-132">A frase "em outro thread" é mencionada acima, mas é importante saber que **isso não significa que fluxos de trabalho assíncronos são uma fachada para multithreading**.</span><span class="sxs-lookup"><span data-stu-id="4baca-132">The phrase "on another thread" is mentioned above, but it is important to know that **this does not mean that async workflows are a facade for multithreading**.</span></span> <span data-ttu-id="4baca-133">O fluxo de trabalho, na verdade, "salta" entre threads, empréstimo-los para uma pequena quantidade de tempo para fazer o trabalho útil.</span><span class="sxs-lookup"><span data-stu-id="4baca-133">The workflow actually "jumps" between threads, borrowing them for a small amount of time to do useful work.</span></span> <span data-ttu-id="4baca-134">Quando um fluxo de trabalho assíncrono é efetivamente "Aguardando" (por exemplo, aguardando uma chamada de rede retornar algo), qualquer thread que ele foi empréstimo no momento é liberada até o trabalho útil que vá fazer outra coisa.</span><span class="sxs-lookup"><span data-stu-id="4baca-134">When an async workflow is effectively "waiting" (for example, waiting for a network call to return something), any thread it was borrowing at the time is freed up to go do useful work on something else.</span></span> <span data-ttu-id="4baca-135">Isso permite que os fluxos de trabalho assíncrono utilizar o sistema que estiverem sendo executados em maneira eficaz e torna especialmente forte para cenários de e/s de alto volume.</span><span class="sxs-lookup"><span data-stu-id="4baca-135">This allows async workflows to utilize the system they run on as effectively as possible, and makes them especially strong for high-volume I/O scenarios.</span></span>

## <a name="how-to-add-parallelism-to-async-code"></a><span data-ttu-id="4baca-136">Como adicionar paralelismo código assíncrono</span><span class="sxs-lookup"><span data-stu-id="4baca-136">How to Add Parallelism to Async Code</span></span>

<span data-ttu-id="4baca-137">Às vezes, você pode necessárias para executar várias tarefas assíncronas em paralelo, coletar seus resultados e interpretá-los de algum modo.</span><span class="sxs-lookup"><span data-stu-id="4baca-137">Sometimes you may need to perform multiple asynchronous jobs in parallel, collect their results, and interpret them in some way.</span></span> <span data-ttu-id="4baca-138">`Async.Parallel` permite que você faça isso sem a necessidade de usar a biblioteca paralela de tarefas, que envolve a necessidade de forçar `Task<'T>` e `Async<'T>` tipos.</span><span class="sxs-lookup"><span data-stu-id="4baca-138">`Async.Parallel` allows you to do this without needing to use the Task Parallel Library, which would involve needing to coerce `Task<'T>` and `Async<'T>` types.</span></span>

<span data-ttu-id="4baca-139">O exemplo a seguir usará `Async.Parallel` para baixar o HTML de quatro sites populares em paralelo, aguarde até que essas tarefas a serem concluídas e imprima o HTML que foi baixado.</span><span class="sxs-lookup"><span data-stu-id="4baca-139">The following example will use `Async.Parallel` to download the HTML from four popular sites in parallel, wait for those tasks to complete, and then print the HTML which was downloaded.</span></span>

```fsharp
open System
open System.Net

let urlList = 
    [ "https://www.microsoft.com"
      "https://www.google.com"
      "https://www.amazon.com"
      "https://www.facebook.com" ]

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let getHtmlList urls =
    urls
    |> Seq.map fetchHtmlAsync   // Build an Async<'T> for each site
    |> Async.Parallel           // Returns an Async<'T []>
    |> Async.RunSynchronously   // Wait for the result of the parallel work

let htmlList = getHtmlList urlList

// We now have the downloaded HTML for each site!
for html in htmlList do
    printfn "%s" html
```

## <a name="important-info-and-advice"></a><span data-ttu-id="4baca-140">Conselhos e informações importantes</span><span class="sxs-lookup"><span data-stu-id="4baca-140">Important Info and Advice</span></span>

*   <span data-ttu-id="4baca-141">Anexar "Async" ao final de qualquer função que você irá consumir</span><span class="sxs-lookup"><span data-stu-id="4baca-141">Append "Async" to the end of any functions you’ll consume</span></span>

 <span data-ttu-id="4baca-142">Embora essa seja apenas uma convenção de nomenclatura, ele facilitar as coisas como a descoberta de API.</span><span class="sxs-lookup"><span data-stu-id="4baca-142">Although this is just a naming convention, it does make things like API discoverability easier.</span></span> <span data-ttu-id="4baca-143">Especialmente se houver versões síncronas e assíncronas da rotina mesmo, é uma boa ideia declarar explicitamente que é assíncrona por meio do nome.</span><span class="sxs-lookup"><span data-stu-id="4baca-143">Particularly if there are synchronous and asynchronous versions of the same routine, it’s a good idea to explicitly state which is asynchronous via the name.</span></span>

*   <span data-ttu-id="4baca-144">Ouça o compilador!</span><span class="sxs-lookup"><span data-stu-id="4baca-144">Listen to the compiler!</span></span>

 <span data-ttu-id="4baca-145">Compilador do F # é muito estrito, tornando quase impossível fazer algo o troubling como executar código de "async" sincronicamente.</span><span class="sxs-lookup"><span data-stu-id="4baca-145">F#’s compiler is very strict, making it nearly impossible to do something troubling like run "async" code synchronously.</span></span> <span data-ttu-id="4baca-146">Se você se deparar com um aviso, que é um sinal de que o código não irá executar como você acha que ele será.</span><span class="sxs-lookup"><span data-stu-id="4baca-146">If you come across a warning, that’s a sign that the code won’t execute how you think it will.</span></span> <span data-ttu-id="4baca-147">Se você pode fazer o compilador felizes, seu código provavelmente será executado conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="4baca-147">If you can make the compiler happy, your code will most likely execute as expected.</span></span>

## <a name="for-the-cvb-programmer-looking-into-f"></a><span data-ttu-id="4baca-148">Para o programador de c# /VB C procurando no F #</span><span class="sxs-lookup"><span data-stu-id="4baca-148">For the C#/VB Programmer Looking Into F#</span></span> #

<span data-ttu-id="4baca-149">Esta seção pressupõe que você esteja familiarizado com o modelo assíncrono em c# / VB.</span><span class="sxs-lookup"><span data-stu-id="4baca-149">This section assumes you’re familiar with the async model in C#/VB.</span></span> <span data-ttu-id="4baca-150">Se não, [assíncrono de programação em c#](../../../csharp/async.md) é um ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="4baca-150">If you are not, [Async Programming in C#](../../../csharp/async.md) is a starting point.</span></span>

<span data-ttu-id="4baca-151">Há uma diferença fundamental entre o modelo de async c# /VB C e o modelo de async F #.</span><span class="sxs-lookup"><span data-stu-id="4baca-151">There is a fundamental difference between the C#/VB async model and the F# async model.</span></span>

<span data-ttu-id="4baca-152">Quando você chama uma função que retorna um `Task` ou `Task<'T>`, já que o trabalho começou execução.</span><span class="sxs-lookup"><span data-stu-id="4baca-152">When you call a function which returns a `Task` or `Task<'T>`, that job has already begun execution.</span></span> <span data-ttu-id="4baca-153">O identificador retornado representa uma tarefa assíncrona já em execução.</span><span class="sxs-lookup"><span data-stu-id="4baca-153">The handle returned represents an already-running asynchronous job.</span></span> <span data-ttu-id="4baca-154">Por outro lado, quando você chama uma função async em F #, a `Async<'a>` retornado representa um trabalho que será **gerado** em algum momento.</span><span class="sxs-lookup"><span data-stu-id="4baca-154">In contrast, when you call an async function in F#, the `Async<'a>` returned represents a job which will be **generated** at some point.</span></span> <span data-ttu-id="4baca-155">Noções básicas sobre esse modelo é muito eficiente, porque permite tarefas assíncronas em F # para ser encadeadas, executada condicionalmente e ser iniciada com mais individualizadas do controle.</span><span class="sxs-lookup"><span data-stu-id="4baca-155">Understanding this model is powerful, because it allows for asynchronous jobs in F# to be chained together easier, performed conditionally, and be started with a finer grain of control.</span></span>

<span data-ttu-id="4baca-156">Há algumas semelhanças e diferenças vale a pena observar.</span><span class="sxs-lookup"><span data-stu-id="4baca-156">There are a few other similarities and differences worth noting.</span></span>

### <a name="similarities"></a><span data-ttu-id="4baca-157">Semelhanças</span><span class="sxs-lookup"><span data-stu-id="4baca-157">Similarities</span></span>

*   <span data-ttu-id="4baca-158">`let!`, `use!`, e `do!` são análogos a `await` ao chamar um trabalho assíncrono de dentro um `async{ }` bloco.</span><span class="sxs-lookup"><span data-stu-id="4baca-158">`let!`, `use!`, and `do!` are analogous to `await` when calling an async job from within an `async{ }` block.</span></span>

 <span data-ttu-id="4baca-159">As três palavras-chave só podem ser usadas dentro de um `async { }` bloco, semelhante a como `await` só pode ser chamado dentro de um `async` método.</span><span class="sxs-lookup"><span data-stu-id="4baca-159">The three keywords can only be used within an `async { }` block, similar to how `await` can only be invoked inside an `async` method.</span></span> <span data-ttu-id="4baca-160">Em resumo, `let!` é para quando você deseja capturar e usar um resultado, `use!` é o mesmo, mas algo cujos recursos devem obter limpo depois que ele é usado, e `do!` é para quando você quiser esperar um fluxo de trabalho assíncrono com nenhum valor de retorno para concluir antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4baca-160">In short, `let!` is for when you want to capture and use a result, `use!` is the same but for something whose resources should get cleaned after it’s used, and `do!` is for when you want to wait for an async workflow with no return value to finish before moving on.</span></span>

*   <span data-ttu-id="4baca-161">F # suporta o paralelismo de dados de maneira semelhante.</span><span class="sxs-lookup"><span data-stu-id="4baca-161">F# supports data-parallelism in a similar way.</span></span>

 <span data-ttu-id="4baca-162">Embora ele opera de forma muito diferente, `Async.Parallel` corresponde à `Task.WhenAll` para o cenário de que os resultados de um conjunto de trabalhos assíncronos quando concluem a todos eles.</span><span class="sxs-lookup"><span data-stu-id="4baca-162">Although it operates very differently, `Async.Parallel` corresponds to `Task.WhenAll` for the scenario of wanting the results of a set of async jobs when they all complete.</span></span>

### <a name="differences"></a><span data-ttu-id="4baca-163">Diferenças</span><span class="sxs-lookup"><span data-stu-id="4baca-163">Differences</span></span>

*   <span data-ttu-id="4baca-164">Aninhados `let!` não é permitido; diferentemente aninhados `await`</span><span class="sxs-lookup"><span data-stu-id="4baca-164">Nested `let!` is not allowed, unlike nested `await`</span></span>

 <span data-ttu-id="4baca-165">Ao contrário de `await`, que podem ser aninhado indefinidamente, `let!` não é possível e deve ter seu resultado associado antes de usá-la em outro `let!`, `do!`, ou `use!`.</span><span class="sxs-lookup"><span data-stu-id="4baca-165">Unlike `await`, which can be nested indefinitely, `let!` cannot and must have its result bound before using it inside of another `let!`, `do!`, or `use!`.</span></span>

*   <span data-ttu-id="4baca-166">Suporte ao cancelamento é mais simples em F # que em c# / VB.</span><span class="sxs-lookup"><span data-stu-id="4baca-166">Cancellation support is simpler in F# than in C#/VB.</span></span>

 <span data-ttu-id="4baca-167">Oferecer suporte ao cancelamento de um tarefa no meio do caminho por meio de sua execução em C# /VB requer verificando o `IsCancellationRequested` propriedade ou chamar `ThrowIfCancellationRequested()` em uma `CancellationToken` objeto que é passado para o método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="4baca-167">Supporting cancellation of a task midway through its execution in C#/VB requires checking the `IsCancellationRequested` property or calling `ThrowIfCancellationRequested()` on a `CancellationToken` object that’s passed into the async method.</span></span>

<span data-ttu-id="4baca-168">Em contraste, F # assíncrona fluxos de trabalho são mais naturalmente cancelável.</span><span class="sxs-lookup"><span data-stu-id="4baca-168">In contrast, F# async workflows are more naturally cancellable.</span></span> <span data-ttu-id="4baca-169">Cancelamento é um processo de três etapas simple.</span><span class="sxs-lookup"><span data-stu-id="4baca-169">Cancellation is a simple three-step process.</span></span>

1.  <span data-ttu-id="4baca-170">Crie um novo `CancellationTokenSource`.</span><span class="sxs-lookup"><span data-stu-id="4baca-170">Create a new `CancellationTokenSource`.</span></span>
2.  <span data-ttu-id="4baca-171">Passá-la em uma função inicial.</span><span class="sxs-lookup"><span data-stu-id="4baca-171">Pass it into a starting function.</span></span>
3.  <span data-ttu-id="4baca-172">Chamar `Cancel` no token.</span><span class="sxs-lookup"><span data-stu-id="4baca-172">Call `Cancel` on the token.</span></span>

<span data-ttu-id="4baca-173">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="4baca-173">Example:</span></span>

```fsharp
open System
open System.Net

let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

let token = new CancellationTokenSource()
Async.Start (workflow, token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

<span data-ttu-id="4baca-174">E pronto!</span><span class="sxs-lookup"><span data-stu-id="4baca-174">And that’s it!</span></span>

## <a name="further-resources"></a><span data-ttu-id="4baca-175">Recursos adicionais:</span><span class="sxs-lookup"><span data-stu-id="4baca-175">Further resources:</span></span>

*   [<span data-ttu-id="4baca-176">Fluxos de trabalho assíncrono no MSDN</span><span class="sxs-lookup"><span data-stu-id="4baca-176">Async Workflows on MSDN</span></span>](https://msdn.microsoft.com/library/dd233250.aspx)
*   [<span data-ttu-id="4baca-177">Sequências assíncronas para F #</span><span class="sxs-lookup"><span data-stu-id="4baca-177">Asynchronous Sequences for F#</span></span>](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [<span data-ttu-id="4baca-178">Utilitários de F # dados HTTP</span><span class="sxs-lookup"><span data-stu-id="4baca-178">F# Data HTTP Utilities</span></span>](https://fsharp.github.io/FSharp.Data/library/Http.html)
