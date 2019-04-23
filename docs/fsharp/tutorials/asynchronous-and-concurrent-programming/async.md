---
title: Programação assíncrona
description: Saiba como F# programação assíncrona é realizada por meio de um modelo de programação de nível de linguagem que é o idioma natural e fácil de usar.
ms.date: 06/20/2016
ms.openlocfilehash: 6925a0132f9beed6be5f9dded3630b551072bea2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343448"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="b9178-103">Programação assíncrona em F\#</span><span class="sxs-lookup"><span data-stu-id="b9178-103">Async Programming in F\#</span></span>

> [!NOTE]
> <span data-ttu-id="b9178-104">Algumas imprecisões foram descobertos neste artigo.</span><span class="sxs-lookup"><span data-stu-id="b9178-104">Some inaccuracies have been discovered in this article.</span></span>  <span data-ttu-id="b9178-105">Ele está sendo regravado.</span><span class="sxs-lookup"><span data-stu-id="b9178-105">It is being rewritten.</span></span>  <span data-ttu-id="b9178-106">Ver [problema #666](https://github.com/dotnet/docs/issues/666) para saber mais sobre as alterações.</span><span class="sxs-lookup"><span data-stu-id="b9178-106">See [Issue #666](https://github.com/dotnet/docs/issues/666) to learn about the changes.</span></span>

<span data-ttu-id="b9178-107">Assíncrono de programação no F# pode ser feito por meio de um modelo de programação de nível de linguagem projetado para ser fácil de usar e a linguagem natural.</span><span class="sxs-lookup"><span data-stu-id="b9178-107">Async programming in F# can be accomplished through a language-level programming model designed to be easy to use and natural to the language.</span></span>

<span data-ttu-id="b9178-108">O núcleo de async programando em F# é `Async<'T>`, uma representação de trabalho que pode ser disparado para ser executado em segundo plano, onde `'T` é o tipo retornado por meio de especiais `return` palavra-chave ou `unit` se o fluxo de trabalho assíncronos não tem nenhum resultado a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="b9178-108">The core of async programming in F# is `Async<'T>`, a representation of work that can be triggered to run in the background, where `'T` is either the type returned via the special `return` keyword or `unit` if the async workflow has no result to return.</span></span>

<span data-ttu-id="b9178-109">O conceito-chave para entender é que tipo de uma expressão async é `Async<'T>`, que é simplesmente uma _especificação_ de trabalho a ser feito em um contexto assíncrono.</span><span class="sxs-lookup"><span data-stu-id="b9178-109">The key concept to understand is that an async expression’s type is `Async<'T>`, which is merely a _specification_ of work to be done in an asynchronous context.</span></span> <span data-ttu-id="b9178-110">Não é executado até que você o inicie explicitamente com uma das funções de partida (como `Async.RunSynchronously`).</span><span class="sxs-lookup"><span data-stu-id="b9178-110">It is not executed until you explicitly start it with one of the starting functions (such as `Async.RunSynchronously`).</span></span> <span data-ttu-id="b9178-111">Embora essa seja uma maneira diferente de pensar sobre como fazer o trabalho, ele acaba sendo bastante simples na prática.</span><span class="sxs-lookup"><span data-stu-id="b9178-111">Although this is a different way of thinking about doing work, it ends up being quite simple in practice.</span></span>

<span data-ttu-id="b9178-112">Por exemplo, digamos que você quiser baixar o HTML de dotnetfoundation.org sem bloquear o thread principal.</span><span class="sxs-lookup"><span data-stu-id="b9178-112">For example, say you wanted to download the HTML from dotnetfoundation.org without blocking the main thread.</span></span> <span data-ttu-id="b9178-113">Você pode fazer isso como este:</span><span class="sxs-lookup"><span data-stu-id="b9178-113">You can accomplish it like this:</span></span>

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

<span data-ttu-id="b9178-114">E pronto!</span><span class="sxs-lookup"><span data-stu-id="b9178-114">And that’s it!</span></span> <span data-ttu-id="b9178-115">Além do uso de `async`, `let!`, e `return`, isso é apenas normal F# código.</span><span class="sxs-lookup"><span data-stu-id="b9178-115">Aside from the use of `async`, `let!`, and `return`, this is just normal F# code.</span></span>

<span data-ttu-id="b9178-116">Há algumas construções sintáticas que vale a pena observar:</span><span class="sxs-lookup"><span data-stu-id="b9178-116">There are a few syntactical constructs which are worth noting:</span></span>

*   <span data-ttu-id="b9178-117">`let!` associa o resultado de uma expressão assíncrona (que é executado em outro contexto).</span><span class="sxs-lookup"><span data-stu-id="b9178-117">`let!` binds the result of an async expression (which runs on another context).</span></span>
*   <span data-ttu-id="b9178-118">`use!` funciona da mesma forma `let!`, mas descarta os seus recursos associados quando ele sai do escopo.</span><span class="sxs-lookup"><span data-stu-id="b9178-118">`use!` works just like `let!`, but disposes its bound resources when it goes out of scope.</span></span>
*   <span data-ttu-id="b9178-119">`do!` irá esperar um fluxo de trabalho de async que não retorna nada.</span><span class="sxs-lookup"><span data-stu-id="b9178-119">`do!` will await an async workflow which doesn’t return anything.</span></span>
*   <span data-ttu-id="b9178-120">`return` simplesmente retorna um resultado de uma expressão assíncrona.</span><span class="sxs-lookup"><span data-stu-id="b9178-120">`return` simply returns a result from an async expression.</span></span>
*   <span data-ttu-id="b9178-121">`return!` executa outro fluxo de trabalho assíncrono e retorna seu valor de retorno como resultado.</span><span class="sxs-lookup"><span data-stu-id="b9178-121">`return!` executes another async workflow and returns its return value as a result.</span></span>

<span data-ttu-id="b9178-122">Além disso, normal `let`, `use`, e `do` palavras-chave podem ser usadas junto com as versões assíncronas, assim como fariam em uma função normal.</span><span class="sxs-lookup"><span data-stu-id="b9178-122">Additionally, normal `let`, `use`, and `do` keywords can be used alongside the async versions just as they would in a normal function.</span></span>

## <a name="how-to-start-async-code-in-f"></a><span data-ttu-id="b9178-123">Como iniciar o código assíncrono no F\#</span><span class="sxs-lookup"><span data-stu-id="b9178-123">How to start Async Code in F\#</span></span>

<span data-ttu-id="b9178-124">Como mencionado anteriormente, o código assíncrono é uma especificação de trabalho a ser feito em outro contexto que deve ser iniciada explicitamente.</span><span class="sxs-lookup"><span data-stu-id="b9178-124">As mentioned earlier, async code is a specification of work to be done in another context which needs to be explicitly started.</span></span> <span data-ttu-id="b9178-125">Aqui estão duas maneiras principais de fazer isso:</span><span class="sxs-lookup"><span data-stu-id="b9178-125">Here are two primary ways to accomplish this:</span></span>

1. <span data-ttu-id="b9178-126">`Async.RunSynchronously` Inicie um fluxo de trabalho assíncrono em outro thread e await seu resultado.</span><span class="sxs-lookup"><span data-stu-id="b9178-126">`Async.RunSynchronously` will start an async workflow on another thread and await its result.</span></span>

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

2. <span data-ttu-id="b9178-127">`Async.Start` iniciará um fluxo de trabalho assíncrono em outro thread e serão **não** await seu resultado.</span><span class="sxs-lookup"><span data-stu-id="b9178-127">`Async.Start` will start an async workflow on another thread, and will **not** await its result.</span></span>

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

<span data-ttu-id="b9178-128">Há outras maneiras de iniciar um fluxo de trabalho assíncronos disponível para cenários mais específicos.</span><span class="sxs-lookup"><span data-stu-id="b9178-128">There are other ways to start an async workflow available for more specific scenarios.</span></span> <span data-ttu-id="b9178-129">Elas são detalhadas [na referência do Async](https://msdn.microsoft.com/library/ee370232.aspx).</span><span class="sxs-lookup"><span data-stu-id="b9178-129">They are detailed [in the Async reference](https://msdn.microsoft.com/library/ee370232.aspx).</span></span>

### <a name="a-note-on-threads"></a><span data-ttu-id="b9178-130">Uma observação sobre Threads</span><span class="sxs-lookup"><span data-stu-id="b9178-130">A Note on Threads</span></span>

<span data-ttu-id="b9178-131">A frase "em outro thread" é mencionada acima, mas é importante saber que **isso não significa que os fluxos de trabalho assíncronos são uma fachada para multithreading**.</span><span class="sxs-lookup"><span data-stu-id="b9178-131">The phrase "on another thread" is mentioned above, but it is important to know that **this does not mean that async workflows are a facade for multithreading**.</span></span> <span data-ttu-id="b9178-132">O fluxo de trabalho, na verdade, "salta" entre threads, emprestando-los para uma pequena quantidade de tempo para fazer trabalho útil.</span><span class="sxs-lookup"><span data-stu-id="b9178-132">The workflow actually "jumps" between threads, borrowing them for a small amount of time to do useful work.</span></span> <span data-ttu-id="b9178-133">Quando um fluxo de trabalho assíncrono está efetivamente "Aguardando" (por exemplo, aguardando uma chamada de rede retornar algo), qualquer thread que ele foi emprestando no momento é liberada até vá fazer o trabalho útil em algo mais.</span><span class="sxs-lookup"><span data-stu-id="b9178-133">When an async workflow is effectively "waiting" (for example, waiting for a network call to return something), any thread it was borrowing at the time is freed up to go do useful work on something else.</span></span> <span data-ttu-id="b9178-134">Isso permite que fluxos de trabalho assíncronos utilizar o sistema a em que serem executados com eficiência possível e os torna especialmente forte para cenários de e/s de alto volume.</span><span class="sxs-lookup"><span data-stu-id="b9178-134">This allows async workflows to utilize the system they run on as effectively as possible, and makes them especially strong for high-volume I/O scenarios.</span></span>

## <a name="how-to-add-parallelism-to-async-code"></a><span data-ttu-id="b9178-135">Como adicionar paralelismo em código assíncrono</span><span class="sxs-lookup"><span data-stu-id="b9178-135">How to Add Parallelism to Async Code</span></span>

<span data-ttu-id="b9178-136">Às vezes, você pode precisa para executar vários trabalhos assíncronos em paralelo, coletar seus resultados e interpretá-los de alguma forma.</span><span class="sxs-lookup"><span data-stu-id="b9178-136">Sometimes you may need to perform multiple asynchronous jobs in parallel, collect their results, and interpret them in some way.</span></span> <span data-ttu-id="b9178-137">`Async.Parallel` permite que você faça isso sem a necessidade de usar a biblioteca paralela de tarefas, que envolveria a necessidade de forçar `Task<'T>` e `Async<'T>` tipos.</span><span class="sxs-lookup"><span data-stu-id="b9178-137">`Async.Parallel` allows you to do this without needing to use the Task Parallel Library, which would involve needing to coerce `Task<'T>` and `Async<'T>` types.</span></span>

<span data-ttu-id="b9178-138">O exemplo a seguir usará `Async.Parallel` para baixar o HTML de quatro sites popular em paralelo, aguardar a conclusão dessas tarefas e, em seguida, imprima o HTML que foi baixado.</span><span class="sxs-lookup"><span data-stu-id="b9178-138">The following example will use `Async.Parallel` to download the HTML from four popular sites in parallel, wait for those tasks to complete, and then print the HTML which was downloaded.</span></span>

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

## <a name="important-info-and-advice"></a><span data-ttu-id="b9178-139">Conselhos e informações importantes</span><span class="sxs-lookup"><span data-stu-id="b9178-139">Important Info and Advice</span></span>

*   <span data-ttu-id="b9178-140">Acrescentar "Async" ao final de todas as funções que irá consumir</span><span class="sxs-lookup"><span data-stu-id="b9178-140">Append "Async" to the end of any functions you’ll consume</span></span>

 <span data-ttu-id="b9178-141">Embora essa seja apenas uma convenção de nomenclatura, ele facilitar as coisas, como a capacidade de descoberta de API.</span><span class="sxs-lookup"><span data-stu-id="b9178-141">Although this is just a naming convention, it does make things like API discoverability easier.</span></span> <span data-ttu-id="b9178-142">Especialmente se houver versões síncronas e assíncronas da mesma rotina, é aconselhável declarar explicitamente que é assíncrona por meio do nome.</span><span class="sxs-lookup"><span data-stu-id="b9178-142">Particularly if there are synchronous and asynchronous versions of the same routine, it’s a good idea to explicitly state which is asynchronous via the name.</span></span>

*   <span data-ttu-id="b9178-143">Ouça o compilador!</span><span class="sxs-lookup"><span data-stu-id="b9178-143">Listen to the compiler!</span></span>

 <span data-ttu-id="b9178-144">F#do compilador é muito estrito, tornando praticamente impossível fazer alguma coisa um problema, como executar código de "async" de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="b9178-144">F#’s compiler is very strict, making it nearly impossible to do something troubling like run "async" code synchronously.</span></span> <span data-ttu-id="b9178-145">Se você se deparar com um aviso, que é um sinal de que o código não será executado como você acha que ele será.</span><span class="sxs-lookup"><span data-stu-id="b9178-145">If you come across a warning, that’s a sign that the code won’t execute how you think it will.</span></span> <span data-ttu-id="b9178-146">Se você pode deixar o compilador feliz, seu código provavelmente será executado conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="b9178-146">If you can make the compiler happy, your code will most likely execute as expected.</span></span>

## <a name="for-the-cvb-programmer-looking-into-f"></a><span data-ttu-id="b9178-147">Para o C#programador /VB procurando em F\#</span><span class="sxs-lookup"><span data-stu-id="b9178-147">For the C#/VB Programmer Looking Into F\#</span></span>

<span data-ttu-id="b9178-148">Esta seção pressupõe que você esteja familiarizado com o modelo de async no C#/VB.</span><span class="sxs-lookup"><span data-stu-id="b9178-148">This section assumes you’re familiar with the async model in C#/VB.</span></span> <span data-ttu-id="b9178-149">Se não, [assíncrono de programação em C# ](../../../csharp/async.md) é um ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="b9178-149">If you are not, [Async Programming in C#](../../../csharp/async.md) is a starting point.</span></span>

<span data-ttu-id="b9178-150">Há uma diferença fundamental entre o C#modelo assíncrono /VB e o F# modelo assíncrono.</span><span class="sxs-lookup"><span data-stu-id="b9178-150">There is a fundamental difference between the C#/VB async model and the F# async model.</span></span>

<span data-ttu-id="b9178-151">Quando você chama uma função que retorna um `Task` ou `Task<'T>`, que o trabalho já tiver começado a execução.</span><span class="sxs-lookup"><span data-stu-id="b9178-151">When you call a function which returns a `Task` or `Task<'T>`, that job has already begun execution.</span></span> <span data-ttu-id="b9178-152">O identificador retornado representa um trabalho assíncrono do já em execução.</span><span class="sxs-lookup"><span data-stu-id="b9178-152">The handle returned represents an already-running asynchronous job.</span></span> <span data-ttu-id="b9178-153">Por outro lado, quando você chama uma função assíncrona F#, o `Async<'a>` retornada representa um trabalho que será **gerado** em algum momento.</span><span class="sxs-lookup"><span data-stu-id="b9178-153">In contrast, when you call an async function in F#, the `Async<'a>` returned represents a job which will be **generated** at some point.</span></span> <span data-ttu-id="b9178-154">Noções básicas sobre esse modelo é muito eficiente, porque permite trabalhos assíncronos no F# para ser encadeados juntos, executadas condicionalmente e ser iniciada com um detalhamento mais refinado de controle.</span><span class="sxs-lookup"><span data-stu-id="b9178-154">Understanding this model is powerful, because it allows for asynchronous jobs in F# to be chained together easier, performed conditionally, and be started with a finer grain of control.</span></span>

<span data-ttu-id="b9178-155">Há algumas semelhanças e diferenças que merecem atenção.</span><span class="sxs-lookup"><span data-stu-id="b9178-155">There are a few other similarities and differences worth noting.</span></span>

### <a name="similarities"></a><span data-ttu-id="b9178-156">Semelhanças</span><span class="sxs-lookup"><span data-stu-id="b9178-156">Similarities</span></span>

*   <span data-ttu-id="b9178-157">`let!`, `use!`, e `do!` são análogos aos `await` ao chamar um trabalho assíncrono de dentro um `async{ }` bloco.</span><span class="sxs-lookup"><span data-stu-id="b9178-157">`let!`, `use!`, and `do!` are analogous to `await` when calling an async job from within an `async{ }` block.</span></span>

 <span data-ttu-id="b9178-158">As três palavras-chave só podem ser usadas dentro de um `async { }` bloco, de forma semelhante a como `await` só pode ser chamada dentro de um `async` método.</span><span class="sxs-lookup"><span data-stu-id="b9178-158">The three keywords can only be used within an `async { }` block, similar to how `await` can only be invoked inside an `async` method.</span></span> <span data-ttu-id="b9178-159">Em resumo, `let!` destina-se quando você deseja capturar e usar um resultado `use!` é o mesmo, mas algo cujos recursos devem obter limpos depois que ele é usado, e `do!` é para quando você deseja esperar para um fluxo de trabalho assíncrono com nenhum valor de retorno para concluir antes de prosseguir.</span><span class="sxs-lookup"><span data-stu-id="b9178-159">In short, `let!` is for when you want to capture and use a result, `use!` is the same but for something whose resources should get cleaned after it’s used, and `do!` is for when you want to wait for an async workflow with no return value to finish before moving on.</span></span>

*   <span data-ttu-id="b9178-160">F#dá suporte a paralelismo de dados de maneira semelhante.</span><span class="sxs-lookup"><span data-stu-id="b9178-160">F# supports data-parallelism in a similar way.</span></span>

 <span data-ttu-id="b9178-161">Embora ele opera de forma muito diferente `Async.Parallel` corresponde ao `Task.WhenAll` para o cenário de que deseja os resultados de um conjunto de trabalhos assíncronos quando todos forem concluídos.</span><span class="sxs-lookup"><span data-stu-id="b9178-161">Although it operates very differently, `Async.Parallel` corresponds to `Task.WhenAll` for the scenario of wanting the results of a set of async jobs when they all complete.</span></span>

### <a name="differences"></a><span data-ttu-id="b9178-162">Diferenças</span><span class="sxs-lookup"><span data-stu-id="b9178-162">Differences</span></span>

*   <span data-ttu-id="b9178-163">Aninhado `let!` não é permitido, ao contrário de aninhados `await`</span><span class="sxs-lookup"><span data-stu-id="b9178-163">Nested `let!` is not allowed, unlike nested `await`</span></span>

 <span data-ttu-id="b9178-164">Diferentemente `await`, que podem ser aninhado indefinidamente `let!` não é possível e deve ter seu resultado associado antes de usá-lo dentro de outra `let!`, `do!`, ou `use!`.</span><span class="sxs-lookup"><span data-stu-id="b9178-164">Unlike `await`, which can be nested indefinitely, `let!` cannot and must have its result bound before using it inside of another `let!`, `do!`, or `use!`.</span></span>

*   <span data-ttu-id="b9178-165">Suporte ao cancelamento é mais simples no F# que no C#/VB.</span><span class="sxs-lookup"><span data-stu-id="b9178-165">Cancellation support is simpler in F# than in C#/VB.</span></span>

 <span data-ttu-id="b9178-166">Oferecer suporte ao cancelamento de midway uma tarefa por meio de sua execução no C#/VB requer verificação o `IsCancellationRequested` propriedade ou chamada `ThrowIfCancellationRequested()` em um `CancellationToken` objeto que é passado para o método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="b9178-166">Supporting cancellation of a task midway through its execution in C#/VB requires checking the `IsCancellationRequested` property or calling `ThrowIfCancellationRequested()` on a `CancellationToken` object that’s passed into the async method.</span></span>

<span data-ttu-id="b9178-167">Por outro lado, F# fluxos de trabalho assíncronos são mais naturalmente cancelável.</span><span class="sxs-lookup"><span data-stu-id="b9178-167">In contrast, F# async workflows are more naturally cancellable.</span></span> <span data-ttu-id="b9178-168">O cancelamento é um processo de três etapas simples.</span><span class="sxs-lookup"><span data-stu-id="b9178-168">Cancellation is a simple three-step process.</span></span>

1. <span data-ttu-id="b9178-169">Crie um novo `CancellationTokenSource`.</span><span class="sxs-lookup"><span data-stu-id="b9178-169">Create a new `CancellationTokenSource`.</span></span>
2. <span data-ttu-id="b9178-170">Passá-la para uma função inicial.</span><span class="sxs-lookup"><span data-stu-id="b9178-170">Pass it into a starting function.</span></span>
3. <span data-ttu-id="b9178-171">Chamar `Cancel` no token.</span><span class="sxs-lookup"><span data-stu-id="b9178-171">Call `Cancel` on the token.</span></span>

<span data-ttu-id="b9178-172">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b9178-172">Example:</span></span>

```fsharp
open System.Threading

// Create a workflow which will loop forever.
let workflow =
    async {
        while true do
            printfn "Working..."
            do! Async.Sleep 1000
    }
    
let tokenSource = new CancellationTokenSource()

// Start the workflow in the background
Async.Start (workflow, tokenSource.Token)

// Executing the next line will stop the workflow
tokenSource.Cancel()
```

<span data-ttu-id="b9178-173">E pronto!</span><span class="sxs-lookup"><span data-stu-id="b9178-173">And that’s it!</span></span>

## <a name="further-resources"></a><span data-ttu-id="b9178-174">Recursos adicionais:</span><span class="sxs-lookup"><span data-stu-id="b9178-174">Further resources:</span></span>

*   [<span data-ttu-id="b9178-175">Fluxos de trabalho assíncronos no MSDN</span><span class="sxs-lookup"><span data-stu-id="b9178-175">Async Workflows on MSDN</span></span>](https://msdn.microsoft.com/library/dd233250.aspx)
*   [<span data-ttu-id="b9178-176">Sequências assíncronas paraF#</span><span class="sxs-lookup"><span data-stu-id="b9178-176">Asynchronous Sequences for F#</span></span>](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [<span data-ttu-id="b9178-177">F#Utilitários de dados HTTP</span><span class="sxs-lookup"><span data-stu-id="b9178-177">F# Data HTTP Utilities</span></span>](https://fsharp.github.io/FSharp.Data/library/Http.html)