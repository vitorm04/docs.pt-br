---
title: Programação assincronia
description: Saiba como f# fornece suporte limpo para assincronia com base em um modelo de programação em nível de linguagem derivado de conceitos de programação funcional principais.
ms.date: 12/17/2018
ms.openlocfilehash: 0a7d400c9778e30d6b25798239f12b7b2b0e3d82
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021528"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="58832-103">Programação de assincronismo em F\#</span><span class="sxs-lookup"><span data-stu-id="58832-103">Async programming in F\#</span></span>

<span data-ttu-id="58832-104">A programação assíncrona é um mecanismo essencial para aplicações modernas por diversas razões.</span><span class="sxs-lookup"><span data-stu-id="58832-104">Asynchronous programming is a mechanism that is essential to modern applications for diverse reasons.</span></span> <span data-ttu-id="58832-105">Existem dois casos de uso primário que a maioria dos desenvolvedores encontrará:</span><span class="sxs-lookup"><span data-stu-id="58832-105">There are two primary use cases that most developers will encounter:</span></span>

- <span data-ttu-id="58832-106">Apresentar um processo de servidor que possa atender a um número significativo de solicitações simultâneas recebidas, minimizando os recursos do sistema ocupados enquanto o processamento de solicitação aguarda entradas de sistemas ou serviços externos a esse processo</span><span class="sxs-lookup"><span data-stu-id="58832-106">Presenting a server process that can service a significant number of concurrent incoming requests, while minimizing the system resources occupied while request processing awaits inputs from systems or services external to that process</span></span>
- <span data-ttu-id="58832-107">Mantendo uma ui responsiva ou um segmento principal enquanto simultaneamente progride o trabalho de fundo</span><span class="sxs-lookup"><span data-stu-id="58832-107">Maintaining a responsive UI or main thread while concurrently progressing background work</span></span>

<span data-ttu-id="58832-108">Embora o trabalho de fundo muitas vezes envolva a utilização de vários threads, é importante considerar os conceitos de assincronia e multi-threading separadamente.</span><span class="sxs-lookup"><span data-stu-id="58832-108">Although background work often does involve the utilization of multiple threads, it's important to consider the concepts of asynchrony and multi-threading separately.</span></span> <span data-ttu-id="58832-109">Na verdade, são preocupações separadas, e uma não implica a outra.</span><span class="sxs-lookup"><span data-stu-id="58832-109">In fact, they are separate concerns, and one does not imply the other.</span></span> <span data-ttu-id="58832-110">Este artigo descreve os conceitos separados com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="58832-110">This article describes the separate concepts in more detail.</span></span>

## <a name="asynchrony-defined"></a><span data-ttu-id="58832-111">Assincronia definida</span><span class="sxs-lookup"><span data-stu-id="58832-111">Asynchrony defined</span></span>

<span data-ttu-id="58832-112">O ponto anterior - que a assincronia é independente da utilização de vários segmentos - vale a pena explicar um pouco mais.</span><span class="sxs-lookup"><span data-stu-id="58832-112">The previous point - that asynchrony is independent of the utilization of multiple threads - is worth explaining a bit further.</span></span> <span data-ttu-id="58832-113">Há três conceitos que às vezes estão relacionados, mas estritamente independentes um do outro:</span><span class="sxs-lookup"><span data-stu-id="58832-113">There are three concepts that are sometimes related, but strictly independent of one another:</span></span>

- <span data-ttu-id="58832-114">Concorrência; quando vários cálculos são executados em períodos de tempo sobrepostos.</span><span class="sxs-lookup"><span data-stu-id="58832-114">Concurrency; when multiple computations execute in overlapping time periods.</span></span>
- <span data-ttu-id="58832-115">Paralelismo; quando vários cálculos ou várias partes de uma única computação são executados exatamente ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="58832-115">Parallelism; when multiple computations or several parts of a single computation run at exactly the same time.</span></span>
- <span data-ttu-id="58832-116">Assincronia; quando um ou mais cálculos podem ser executados separadamente do fluxo principal do programa.</span><span class="sxs-lookup"><span data-stu-id="58832-116">Asynchrony; when one or more computations can execute separately from the main program flow.</span></span>

<span data-ttu-id="58832-117">Todos os três são conceitos ortogonais, mas podem ser facilmente confundidos, especialmente quando são usados juntos.</span><span class="sxs-lookup"><span data-stu-id="58832-117">All three are orthogonal concepts, but can be easily conflated, especially when they are used together.</span></span> <span data-ttu-id="58832-118">Por exemplo, você pode precisar executar vários cálculos assíncronos em paralelo.</span><span class="sxs-lookup"><span data-stu-id="58832-118">For example, you may need to execute multiple asynchronous computations in parallel.</span></span> <span data-ttu-id="58832-119">Essa relação não significa que o paralelismo ou a assincronia implicam um ao outro.</span><span class="sxs-lookup"><span data-stu-id="58832-119">This relationship does not mean that parallelism or asynchrony imply one another.</span></span>

<span data-ttu-id="58832-120">Se você considerar a etimologia da palavra "assíncrona", há duas peças envolvidas:</span><span class="sxs-lookup"><span data-stu-id="58832-120">If you consider the etymology of the word "asynchronous", there are two pieces involved:</span></span>

- <span data-ttu-id="58832-121">"A", que significa "não".</span><span class="sxs-lookup"><span data-stu-id="58832-121">"a", meaning "not".</span></span>
- <span data-ttu-id="58832-122">"síncrono", que significa "ao mesmo tempo".</span><span class="sxs-lookup"><span data-stu-id="58832-122">"synchronous", meaning "at the same time".</span></span>

<span data-ttu-id="58832-123">Quando você colocar esses dois termos juntos, você verá que "assíncrono" significa "não ao mesmo tempo".</span><span class="sxs-lookup"><span data-stu-id="58832-123">When you put these two terms together, you'll see that "asynchronous" means "not at the same time".</span></span> <span data-ttu-id="58832-124">É isso!</span><span class="sxs-lookup"><span data-stu-id="58832-124">That's it!</span></span> <span data-ttu-id="58832-125">Não há implicação de simultismo ou paralelismo nesta definição.</span><span class="sxs-lookup"><span data-stu-id="58832-125">There is no implication of concurrency or parallelism in this definition.</span></span> <span data-ttu-id="58832-126">Isso também é verdade na prática.</span><span class="sxs-lookup"><span data-stu-id="58832-126">This is also true in practice.</span></span>

<span data-ttu-id="58832-127">Em termos práticos, computações assíncronas em F# são programadas para executar independentemente do fluxo principal do programa.</span><span class="sxs-lookup"><span data-stu-id="58832-127">In practical terms, asynchronous computations in F# are scheduled to execute independently of the main program flow.</span></span> <span data-ttu-id="58832-128">Essa execução independente não implica simultuou-se ou paralelismo, nem implica que uma computação sempre acontece em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="58832-128">This independent execution doesn't imply concurrency or parallelism, nor does it imply that a computation always happens in the background.</span></span> <span data-ttu-id="58832-129">Na verdade, cálculos assíncronos podem até mesmo executar sincronicamente, dependendo da natureza da computação e do ambiente em que a computação está sendo executada.</span><span class="sxs-lookup"><span data-stu-id="58832-129">In fact, asynchronous computations can even execute synchronously, depending on the nature of the computation and the environment the computation is executing in.</span></span>

<span data-ttu-id="58832-130">A principal vantagem que você deve ter é que os cálculos assíncronos são independentes do fluxo principal do programa.</span><span class="sxs-lookup"><span data-stu-id="58832-130">The main takeaway you should have is that asynchronous computations are independent of the main program flow.</span></span> <span data-ttu-id="58832-131">Embora existam poucas garantias sobre quando ou como uma computação assíncrona é executada, existem algumas abordagens para orquestre-las e agendar.</span><span class="sxs-lookup"><span data-stu-id="58832-131">Although there are few guarantees about when or how an asynchronous computation executes, there are some approaches to orchestrating and scheduling them.</span></span> <span data-ttu-id="58832-132">O resto deste artigo explora conceitos centrais para a assincronia F# e como usar os tipos, funções e expressões incorporadas em F#.</span><span class="sxs-lookup"><span data-stu-id="58832-132">The rest of this article explores core concepts for F# asynchrony and how to use the types, functions, and expressions built into F#.</span></span>

## <a name="core-concepts"></a><span data-ttu-id="58832-133">Conceitos principais</span><span class="sxs-lookup"><span data-stu-id="58832-133">Core concepts</span></span>

<span data-ttu-id="58832-134">Em F#, a programação assíncrona é centrada em três conceitos principais:</span><span class="sxs-lookup"><span data-stu-id="58832-134">In F#, asynchronous programming is centered around three core concepts:</span></span>

- <span data-ttu-id="58832-135">O `Async<'T>` tipo, que representa uma composável computação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="58832-135">The `Async<'T>` type, which represents a composable asynchronous computation.</span></span>
- <span data-ttu-id="58832-136">As `Async` funções do módulo, que permitem programar trabalhos assíncronos, compõem cálculos assíncronos e transformam resultados assíncronos.</span><span class="sxs-lookup"><span data-stu-id="58832-136">The `Async` module functions, which let you schedule asynchronous work, compose asynchronous computations, and transform asynchronous results.</span></span>
- <span data-ttu-id="58832-137">A `async { }` [expressão computacional,](../../language-reference/computation-expressions.md)que fornece uma sintaxe conveniente para construir e controlar cálculos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="58832-137">The `async { }` [computation expression](../../language-reference/computation-expressions.md), which provides a convenient syntax for building and controlling asynchronous computations.</span></span>

<span data-ttu-id="58832-138">Você pode ver esses três conceitos no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="58832-138">You can see these three concepts in the following example:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

<span data-ttu-id="58832-139">No exemplo, `printTotalFileBytes` a função `string -> Async<unit>`é do tipo .</span><span class="sxs-lookup"><span data-stu-id="58832-139">In the example, the `printTotalFileBytes` function is of type `string -> Async<unit>`.</span></span> <span data-ttu-id="58832-140">Chamar a função não executa realmente a computação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="58832-140">Calling the function does not actually execute the asynchronous computation.</span></span> <span data-ttu-id="58832-141">Em vez disso, retorna um `Async<unit>` que age como uma *especificação* do trabalho que é executar assíncronamente.</span><span class="sxs-lookup"><span data-stu-id="58832-141">Instead, it returns an `Async<unit>` that acts as a *specification* of the work that is to execute asynchronously.</span></span> <span data-ttu-id="58832-142">Ele `Async.AwaitTask` chama em seu corpo, que <xref:System.IO.File.ReadAllBytesAsync%2A> converte o resultado de um tipo apropriado.</span><span class="sxs-lookup"><span data-stu-id="58832-142">It calls `Async.AwaitTask` in its body, which converts the result of <xref:System.IO.File.ReadAllBytesAsync%2A> to an appropriate type.</span></span>

<span data-ttu-id="58832-143">Outra linha importante é `Async.RunSynchronously`a chamada para .</span><span class="sxs-lookup"><span data-stu-id="58832-143">Another important line is the call to `Async.RunSynchronously`.</span></span> <span data-ttu-id="58832-144">Esta é uma das funções de partida do módulo Assync que você precisará chamar se quiser realmente executar uma computação assíncrona F#.</span><span class="sxs-lookup"><span data-stu-id="58832-144">This is one of the Async module starting functions that you'll need to call if you want to actually execute an F# asynchronous computation.</span></span>

<span data-ttu-id="58832-145">Esta é uma diferença fundamental com o `async` estilo C#/Visual Basic de programação.</span><span class="sxs-lookup"><span data-stu-id="58832-145">This is a fundamental difference with the C#/Visual Basic style of `async` programming.</span></span> <span data-ttu-id="58832-146">Em F#, cálculos assíncronos podem ser considerados como **tarefas frias.**</span><span class="sxs-lookup"><span data-stu-id="58832-146">In F#, asynchronous computations can be thought of as **Cold tasks**.</span></span> <span data-ttu-id="58832-147">Eles devem ser explicitamente iniciados para realmente executar.</span><span class="sxs-lookup"><span data-stu-id="58832-147">They must be explicitly started to actually execute.</span></span> <span data-ttu-id="58832-148">Isso tem algumas vantagens, pois permite combinar e sequenciar trabalhos assíncronos muito mais facilmente do que em C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="58832-148">This has some advantages, as it allows you to combine and sequence asynchronous work much more easily than in C# or Visual Basic.</span></span>

## <a name="combine-asynchronous-computations"></a><span data-ttu-id="58832-149">Combine cálculos assíncronos</span><span class="sxs-lookup"><span data-stu-id="58832-149">Combine asynchronous computations</span></span>

<span data-ttu-id="58832-150">Aqui está um exemplo que se baseia no anterior combinando cálculos:</span><span class="sxs-lookup"><span data-stu-id="58832-150">Here is an example that builds upon the previous one by combining computations:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

<span data-ttu-id="58832-151">Como você pode `main` ver, a função tem mais algumas chamadas feitas.</span><span class="sxs-lookup"><span data-stu-id="58832-151">As you can see, the `main` function has quite a few more calls made.</span></span> <span data-ttu-id="58832-152">Conceitualmente, ele faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="58832-152">Conceptually, it does the following:</span></span>

1. <span data-ttu-id="58832-153">Transforme os argumentos `Async<unit>` da linha `Array.map`de comando em cálculos com .</span><span class="sxs-lookup"><span data-stu-id="58832-153">Transform the command-line arguments into `Async<unit>` computations with `Array.map`.</span></span>
2. <span data-ttu-id="58832-154">Crie `Async<'T[]>` um que programe `printTotalFileBytes` e execute os cálculos em paralelo quando for executado.</span><span class="sxs-lookup"><span data-stu-id="58832-154">Create an `Async<'T[]>` that schedules and runs the `printTotalFileBytes` computations in parallel when it runs.</span></span>
3. <span data-ttu-id="58832-155">Crie `Async<unit>` um que execute a computação paralela e ignore seu resultado.</span><span class="sxs-lookup"><span data-stu-id="58832-155">Create an `Async<unit>` that will run the parallel computation and ignore its result.</span></span>
4. <span data-ttu-id="58832-156">Execute explicitamente a última `Async.RunSynchronously` computação com e bloqueie até que seja concluída.</span><span class="sxs-lookup"><span data-stu-id="58832-156">Explicitly run the last computation with `Async.RunSynchronously` and block until it completes.</span></span>

<span data-ttu-id="58832-157">Quando este programa `printTotalFileBytes` é executado, é executado em paralelo para cada argumento de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="58832-157">When this program runs, `printTotalFileBytes` runs in parallel for each command-line argument.</span></span> <span data-ttu-id="58832-158">Como os cálculos assíncronos são executados independentemente do fluxo do programa, não há ordem na qual imprimam suas informações e terminem a execução.</span><span class="sxs-lookup"><span data-stu-id="58832-158">Because asynchronous computations execute independently of program flow, there is no order in which they print their information and finish executing.</span></span> <span data-ttu-id="58832-159">Os cálculos serão agendados em paralelo, mas sua ordem de execução não é garantida.</span><span class="sxs-lookup"><span data-stu-id="58832-159">The computations will be scheduled in parallel, but their order of execution is not guaranteed.</span></span>

## <a name="sequence-asynchronous-computations"></a><span data-ttu-id="58832-160">Cálculos assíncronos de seqüência</span><span class="sxs-lookup"><span data-stu-id="58832-160">Sequence asynchronous computations</span></span>

<span data-ttu-id="58832-161">Por `Async<'T>` ser uma especificação do trabalho em vez de uma tarefa já em execução, você pode realizar transformações mais complexas facilmente.</span><span class="sxs-lookup"><span data-stu-id="58832-161">Because `Async<'T>` is a specification of work rather than an already-running task, you can perform more intricate transformations easily.</span></span> <span data-ttu-id="58832-162">Aqui está um exemplo que sequencia um conjunto de cálculos Do Sync para que eles executem um após o outro.</span><span class="sxs-lookup"><span data-stu-id="58832-162">Here is an example that sequences a set of Async computations so they execute one after another.</span></span>

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

<span data-ttu-id="58832-163">Isso será `printTotalFileBytes` agendado para executar na `argv` ordem dos elementos de vez em programá-los em paralelo.</span><span class="sxs-lookup"><span data-stu-id="58832-163">This will schedule `printTotalFileBytes` to execute in the order of the elements of `argv` rather than scheduling them in parallel.</span></span> <span data-ttu-id="58832-164">Como o próximo item não será agendado até que a última computação tenha sido executada, os cálculos são sequenciados de tal forma que não haja sobreposição em sua execução.</span><span class="sxs-lookup"><span data-stu-id="58832-164">Because the next item will not be scheduled until after the last computation has finished executing, the computations are sequenced such that there is no overlap in their execution.</span></span>

## <a name="important-async-module-functions"></a><span data-ttu-id="58832-165">Funções importantes do módulo Async</span><span class="sxs-lookup"><span data-stu-id="58832-165">Important Async module functions</span></span>

<span data-ttu-id="58832-166">Quando você escreve código assincrono em F#, você geralmente interage com uma estrutura que lida com o agendamento de cálculos para você.</span><span class="sxs-lookup"><span data-stu-id="58832-166">When you write async code in F#, you'll usually interact with a framework that handles scheduling of computations for you.</span></span> <span data-ttu-id="58832-167">No entanto, nem sempre é assim, por isso é bom aprender as várias funções iniciais para agendar trabalhos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="58832-167">However, this is not always the case, so it is good to learn the various starting functions to schedule asynchronous work.</span></span>

<span data-ttu-id="58832-168">Como os cálculos assíncronos F# são uma _especificação_ do trabalho em vez de uma representação de trabalho que já está sendo executado, eles devem ser explicitamente iniciados com uma função inicial.</span><span class="sxs-lookup"><span data-stu-id="58832-168">Because F# asynchronous computations are a _specification_ of work rather than a representation of work that is already executing, they must be explicitly started with a starting function.</span></span> <span data-ttu-id="58832-169">Existem muitas [funções iniciais do Assync](https://msdn.microsoft.com/library/ee370232.aspx) que são úteis em diferentes contextos.</span><span class="sxs-lookup"><span data-stu-id="58832-169">There are many [Async starting functions](https://msdn.microsoft.com/library/ee370232.aspx) that are helpful in different contexts.</span></span> <span data-ttu-id="58832-170">A seção a seguir descreve algumas das funções de partida mais comuns.</span><span class="sxs-lookup"><span data-stu-id="58832-170">The following section describes some of the more common starting functions.</span></span>

### <a name="asyncstartchild"></a><span data-ttu-id="58832-171">Async.StartChild</span><span class="sxs-lookup"><span data-stu-id="58832-171">Async.StartChild</span></span>

<span data-ttu-id="58832-172">Inicia uma computação infantil dentro de uma computação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="58832-172">Starts a child computation within an asynchronous computation.</span></span> <span data-ttu-id="58832-173">Isso permite que vários cálculos assíncronos sejam executados simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="58832-173">This allows multiple asynchronous computations to be executed concurrently.</span></span> <span data-ttu-id="58832-174">A computação infantil compartilha um token de cancelamento com a computação dos pais.</span><span class="sxs-lookup"><span data-stu-id="58832-174">The child computation shares a cancellation token with the parent computation.</span></span> <span data-ttu-id="58832-175">Se a computação dos pais for cancelada, a computação filho também será cancelada.</span><span class="sxs-lookup"><span data-stu-id="58832-175">If the parent computation is canceled, the child computation is also canceled.</span></span>

<span data-ttu-id="58832-176">Assinatura:</span><span class="sxs-lookup"><span data-stu-id="58832-176">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

<span data-ttu-id="58832-177">Quando usar:</span><span class="sxs-lookup"><span data-stu-id="58832-177">When to use:</span></span>

- <span data-ttu-id="58832-178">Quando você deseja executar vários cálculos assíncronos simultaneamente em vez de um de cada vez, mas não tê-los agendados em paralelo.</span><span class="sxs-lookup"><span data-stu-id="58832-178">When you want to execute multiple asynchronous computations concurrently rather than one at a time, but not have them scheduled in parallel.</span></span>
- <span data-ttu-id="58832-179">Quando você deseja vincular a vida útil de um cálculo infantil à de um cálculo pai.</span><span class="sxs-lookup"><span data-stu-id="58832-179">When you wish to tie the lifetime of a child computation to that of a parent computation.</span></span>

<span data-ttu-id="58832-180">O que tomar cuidado:</span><span class="sxs-lookup"><span data-stu-id="58832-180">What to watch out for:</span></span>

- <span data-ttu-id="58832-181">Iniciar vários cálculos `Async.StartChild` com não é o mesmo que agendar em paralelo.</span><span class="sxs-lookup"><span data-stu-id="58832-181">Starting multiple computations with `Async.StartChild` isn't the same as scheduling them in parallel.</span></span> <span data-ttu-id="58832-182">Se você deseja agendar cálculos `Async.Parallel`em paralelo, use .</span><span class="sxs-lookup"><span data-stu-id="58832-182">If you wish to schedule computations in parallel, use `Async.Parallel`.</span></span>
- <span data-ttu-id="58832-183">O cancelamento de um cálculo dos pais provocará o cancelamento de todos os cálculos de crianças iniciados.</span><span class="sxs-lookup"><span data-stu-id="58832-183">Canceling a parent computation will trigger cancellation of all child computations it started.</span></span>

### <a name="asyncstartimmediate"></a><span data-ttu-id="58832-184">Async.StartImmediate</span><span class="sxs-lookup"><span data-stu-id="58832-184">Async.StartImmediate</span></span>

<span data-ttu-id="58832-185">Executa uma computação assíncrona, iniciando imediatamente no segmento atual do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="58832-185">Runs an asynchronous computation, starting immediately on the current operating system thread.</span></span> <span data-ttu-id="58832-186">Isso é útil se você precisar atualizar algo no segmento de chamada durante a computação.</span><span class="sxs-lookup"><span data-stu-id="58832-186">This is helpful if you need to update something on the calling thread during the computation.</span></span> <span data-ttu-id="58832-187">Por exemplo, se uma computação assíncrona deve atualizar uma ui (como atualizar uma barra de progresso), então `Async.StartImmediate` deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="58832-187">For example, if an asynchronous computation must update a UI (such as updating a progress bar), then `Async.StartImmediate` should be used.</span></span>

<span data-ttu-id="58832-188">Assinatura:</span><span class="sxs-lookup"><span data-stu-id="58832-188">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="58832-189">Quando usar:</span><span class="sxs-lookup"><span data-stu-id="58832-189">When to use:</span></span>

- <span data-ttu-id="58832-190">Quando você precisa atualizar algo no segmento de chamada no meio de uma computação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="58832-190">When you need to update something on the calling thread in the middle of an asynchronous computation.</span></span>

<span data-ttu-id="58832-191">O que tomar cuidado:</span><span class="sxs-lookup"><span data-stu-id="58832-191">What to watch out for:</span></span>

- <span data-ttu-id="58832-192">O código na computação assíncrona será executado em qualquer segmento que esteja programado.</span><span class="sxs-lookup"><span data-stu-id="58832-192">Code in the asynchronous computation will run on whatever thread one happens to be scheduled on.</span></span> <span data-ttu-id="58832-193">Isso pode ser problemático se esse segmento for de alguma forma sensível, como um segmento de UI.</span><span class="sxs-lookup"><span data-stu-id="58832-193">This can be problematic if that thread is in some way sensitive, such as a UI thread.</span></span> <span data-ttu-id="58832-194">Nesses casos, `Async.StartImmediate` é provável que seja inapropriado usar.</span><span class="sxs-lookup"><span data-stu-id="58832-194">In such cases, `Async.StartImmediate` is likely inappropriate to use.</span></span>

### <a name="asyncstartastask"></a><span data-ttu-id="58832-195">Async.StartAsTask</span><span class="sxs-lookup"><span data-stu-id="58832-195">Async.StartAsTask</span></span>

<span data-ttu-id="58832-196">Executa um cálculo no pool de segmentos.</span><span class="sxs-lookup"><span data-stu-id="58832-196">Executes a computation in the thread pool.</span></span> <span data-ttu-id="58832-197">Retorna <xref:System.Threading.Tasks.Task%601> um que será concluído no estado correspondente assim que o cálculo terminar (produz o resultado, lança exceção ou é cancelado).</span><span class="sxs-lookup"><span data-stu-id="58832-197">Returns a <xref:System.Threading.Tasks.Task%601> that will be completed on the corresponding state once the computation terminates (produces the result, throws exception, or gets canceled).</span></span> <span data-ttu-id="58832-198">Se nenhum token de cancelamento for fornecido, o token de cancelamento padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="58832-198">If no cancellation token is provided, then the default cancellation token is used.</span></span>

<span data-ttu-id="58832-199">Assinatura:</span><span class="sxs-lookup"><span data-stu-id="58832-199">Signature:</span></span>

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

<span data-ttu-id="58832-200">Quando usar:</span><span class="sxs-lookup"><span data-stu-id="58832-200">When to use:</span></span>

- <span data-ttu-id="58832-201">Quando você precisa chamar uma API .NET que espera que a represente <xref:System.Threading.Tasks.Task%601> o resultado de uma computação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="58832-201">When you need to call into a .NET API that expects a <xref:System.Threading.Tasks.Task%601> to represent the result of an asynchronous computation.</span></span>

<span data-ttu-id="58832-202">O que tomar cuidado:</span><span class="sxs-lookup"><span data-stu-id="58832-202">What to watch out for:</span></span>

- <span data-ttu-id="58832-203">Esta chamada alocará um objeto adicional, `Task` que pode aumentar a sobrecarga se for usada com frequência.</span><span class="sxs-lookup"><span data-stu-id="58832-203">This call will allocate an additional `Task` object, which can increase overhead if it is used often.</span></span>

### <a name="asyncparallel"></a><span data-ttu-id="58832-204">Assync.Parallel</span><span class="sxs-lookup"><span data-stu-id="58832-204">Async.Parallel</span></span>

<span data-ttu-id="58832-205">Agenda uma seqüência de cálculos assíncronos a serem executados em paralelo.</span><span class="sxs-lookup"><span data-stu-id="58832-205">Schedules a sequence of asynchronous computations to be executed in parallel.</span></span> <span data-ttu-id="58832-206">O grau de paralelismo pode ser opcionalmente `maxDegreesOfParallelism` ajustado/estrangulado especificando o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="58832-206">The degree of parallelism can be optionally tuned/throttled by specifying the `maxDegreesOfParallelism` parameter.</span></span>

<span data-ttu-id="58832-207">Assinatura:</span><span class="sxs-lookup"><span data-stu-id="58832-207">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> * ?maxDegreesOfParallelism: int -> Async<'T[]>
```

<span data-ttu-id="58832-208">Quando usar:</span><span class="sxs-lookup"><span data-stu-id="58832-208">When to use it:</span></span>

- <span data-ttu-id="58832-209">Se você precisar executar um conjunto de cálculos ao mesmo tempo e não confiar em sua ordem de execução.</span><span class="sxs-lookup"><span data-stu-id="58832-209">If you need to run a set of computations at the same time and have no reliance on their order of execution.</span></span>
- <span data-ttu-id="58832-210">Se você não precisar de resultados de cálculos agendados em paralelo até que todos tenham sido concluídos.</span><span class="sxs-lookup"><span data-stu-id="58832-210">If you don't require results from computations scheduled in parallel until they have all completed.</span></span>

<span data-ttu-id="58832-211">O que tomar cuidado:</span><span class="sxs-lookup"><span data-stu-id="58832-211">What to watch out for:</span></span>

- <span data-ttu-id="58832-212">Você só pode acessar a matriz de valores resultante uma vez que todos os cálculos tenham terminado.</span><span class="sxs-lookup"><span data-stu-id="58832-212">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="58832-213">Os cálculos serão executados sempre que forem agendados.</span><span class="sxs-lookup"><span data-stu-id="58832-213">Computations will be run whenever they end up getting scheduled.</span></span> <span data-ttu-id="58832-214">Este comportamento significa que você não pode confiar na ordem deles de sua execução.</span><span class="sxs-lookup"><span data-stu-id="58832-214">This behavior means you cannot rely on their order of their execution.</span></span>

### <a name="asyncsequential"></a><span data-ttu-id="58832-215">Async.Seqüencial</span><span class="sxs-lookup"><span data-stu-id="58832-215">Async.Sequential</span></span>

<span data-ttu-id="58832-216">Agenda uma seqüência de cálculos assíncronos a serem executados na ordem em que são passados.</span><span class="sxs-lookup"><span data-stu-id="58832-216">Schedules a sequence of asynchronous computations to be executed in the order that they are passed.</span></span> <span data-ttu-id="58832-217">O primeiro cálculo será executado, depois o próximo, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="58832-217">The first computation will be executed, then the next, and so on.</span></span> <span data-ttu-id="58832-218">Nenhum cálculo será executado em paralelo.</span><span class="sxs-lookup"><span data-stu-id="58832-218">No computations will be executed in parallel.</span></span>

<span data-ttu-id="58832-219">Assinatura:</span><span class="sxs-lookup"><span data-stu-id="58832-219">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

<span data-ttu-id="58832-220">Quando usar:</span><span class="sxs-lookup"><span data-stu-id="58832-220">When to use it:</span></span>

- <span data-ttu-id="58832-221">Se você precisar executar vários cálculos em ordem.</span><span class="sxs-lookup"><span data-stu-id="58832-221">If you need to execute multiple computations in order.</span></span>

<span data-ttu-id="58832-222">O que tomar cuidado:</span><span class="sxs-lookup"><span data-stu-id="58832-222">What to watch out for:</span></span>

- <span data-ttu-id="58832-223">Você só pode acessar a matriz de valores resultante uma vez que todos os cálculos tenham terminado.</span><span class="sxs-lookup"><span data-stu-id="58832-223">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="58832-224">Os cálculos serão executados na ordem em que são passados para esta função, o que pode significar que mais tempo se passará antes que os resultados sejam devolvidos.</span><span class="sxs-lookup"><span data-stu-id="58832-224">Computations will be run in the order that they are passed to this function, which can mean that more time will elapse before the results are returned.</span></span>

### <a name="asyncawaittask"></a><span data-ttu-id="58832-225">Async.AwaitTask</span><span class="sxs-lookup"><span data-stu-id="58832-225">Async.AwaitTask</span></span>

<span data-ttu-id="58832-226">Retorna uma computação assíncrona que <xref:System.Threading.Tasks.Task%601> espera que o dado complete e retorna seu resultado como um`Async<'T>`</span><span class="sxs-lookup"><span data-stu-id="58832-226">Returns an asynchronous computation that waits for the given <xref:System.Threading.Tasks.Task%601> to complete and returns its result as an `Async<'T>`</span></span>

<span data-ttu-id="58832-227">Assinatura:</span><span class="sxs-lookup"><span data-stu-id="58832-227">Signature:</span></span>

```fsharp
task: Task<'T> -> Async<'T>
```

<span data-ttu-id="58832-228">Quando usar:</span><span class="sxs-lookup"><span data-stu-id="58832-228">When to use:</span></span>

- <span data-ttu-id="58832-229">Quando você está consumindo uma API <xref:System.Threading.Tasks.Task%601> .NET que retorna a dentro de uma computação assíncrona F#.</span><span class="sxs-lookup"><span data-stu-id="58832-229">When you are consuming a .NET API that returns a <xref:System.Threading.Tasks.Task%601> within an F# asynchronous computation.</span></span>

<span data-ttu-id="58832-230">O que tomar cuidado:</span><span class="sxs-lookup"><span data-stu-id="58832-230">What to watch out for:</span></span>

- <span data-ttu-id="58832-231">As exceções <xref:System.AggregateException> são embrulhadas seguindo a convenção da Biblioteca Paralela de Tarefas, e esse comportamento é diferente de como o f# assync geralmente aparece exceções.</span><span class="sxs-lookup"><span data-stu-id="58832-231">Exceptions are wrapped in <xref:System.AggregateException> following the convention of the Task Parallel Library, and this behavior is different from how F# async generally surfaces exceptions.</span></span>

### <a name="asynccatch"></a><span data-ttu-id="58832-232">Async.Catch</span><span class="sxs-lookup"><span data-stu-id="58832-232">Async.Catch</span></span>

<span data-ttu-id="58832-233">Cria uma computação assíncrona `Async<'T>`que executa `Async<Choice<'T, exn>>`um dado, retornando um .</span><span class="sxs-lookup"><span data-stu-id="58832-233">Creates an asynchronous computation that executes a given `Async<'T>`, returning an `Async<Choice<'T, exn>>`.</span></span> <span data-ttu-id="58832-234">Se o `Async<'T>` dado for `Choice1Of2` concluído com sucesso, então um é devolvido com o valor resultante.</span><span class="sxs-lookup"><span data-stu-id="58832-234">If the given `Async<'T>` completes successfully, then a `Choice1Of2` is returned with the resultant value.</span></span> <span data-ttu-id="58832-235">Se uma exceção for lançada antes `Choice2of2` de ser concluída, então um é devolvido com a exceção levantada.</span><span class="sxs-lookup"><span data-stu-id="58832-235">If an exception is thrown before it completes, then a `Choice2of2` is returned with the raised exception.</span></span> <span data-ttu-id="58832-236">Se for usado em uma computação assíncrona que é composta por muitos cálculos, e um desses cálculos abre uma exceção, a computação abrangente será totalmente interrompida.</span><span class="sxs-lookup"><span data-stu-id="58832-236">If it is used on an asynchronous computation that is itself composed of many computations, and one of those computations throws an exception, the encompassing computation will be stopped entirely.</span></span>

<span data-ttu-id="58832-237">Assinatura:</span><span class="sxs-lookup"><span data-stu-id="58832-237">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

<span data-ttu-id="58832-238">Quando usar:</span><span class="sxs-lookup"><span data-stu-id="58832-238">When to use:</span></span>

- <span data-ttu-id="58832-239">Quando você está realizando um trabalho assíncrono que pode falhar com uma exceção e você deseja lidar com essa exceção no chamador.</span><span class="sxs-lookup"><span data-stu-id="58832-239">When you are performing asynchronous work that may fail with an exception and you want to handle that exception in the caller.</span></span>

<span data-ttu-id="58832-240">O que tomar cuidado:</span><span class="sxs-lookup"><span data-stu-id="58832-240">What to watch out for:</span></span>

- <span data-ttu-id="58832-241">Ao usar cálculos assíncronos combinados ou seqüenciados, a computação abrangente irá parar totalmente se uma de suas computação "internas" lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="58832-241">When using combined or sequenced asynchronous computations, the encompassing computation will fully stop if one of its "internal" computations throws an exception.</span></span>

### <a name="asyncignore"></a><span data-ttu-id="58832-242">Assync.Ignore</span><span class="sxs-lookup"><span data-stu-id="58832-242">Async.Ignore</span></span>

<span data-ttu-id="58832-243">Cria uma computação assíncrona que executa a dada computação e ignora seu resultado.</span><span class="sxs-lookup"><span data-stu-id="58832-243">Creates an asynchronous computation that runs the given computation and ignores its result.</span></span>

<span data-ttu-id="58832-244">Assinatura:</span><span class="sxs-lookup"><span data-stu-id="58832-244">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<unit>
```

<span data-ttu-id="58832-245">Quando usar:</span><span class="sxs-lookup"><span data-stu-id="58832-245">When to use:</span></span>

- <span data-ttu-id="58832-246">Quando você tem uma computação assíncrona cujo resultado não é necessário.</span><span class="sxs-lookup"><span data-stu-id="58832-246">When you have an asynchronous computation whose result is not needed.</span></span> <span data-ttu-id="58832-247">Isso é análogo `ignore` ao código para código não assíncrono.</span><span class="sxs-lookup"><span data-stu-id="58832-247">This is analogous to the `ignore` code for non-asynchronous code.</span></span>

<span data-ttu-id="58832-248">O que tomar cuidado:</span><span class="sxs-lookup"><span data-stu-id="58832-248">What to watch out for:</span></span>

- <span data-ttu-id="58832-249">Se você `Async.Ignore` deve usar porque `Async.Start` deseja usar `Async<unit>`ou outra função que exija, considere se descartar o resultado está bem.</span><span class="sxs-lookup"><span data-stu-id="58832-249">If you must use `Async.Ignore` because you wish to use `Async.Start` or another function that requires `Async<unit>`, consider if discarding the result is okay.</span></span> <span data-ttu-id="58832-250">Evite descartar resultados apenas para se encaixar em uma assinatura do tipo.</span><span class="sxs-lookup"><span data-stu-id="58832-250">Avoid discarding results just to fit a type signature.</span></span>

### <a name="asyncrunsynchronously"></a><span data-ttu-id="58832-251">Async.RunSynchronously</span><span class="sxs-lookup"><span data-stu-id="58832-251">Async.RunSynchronously</span></span>

<span data-ttu-id="58832-252">Executa uma computação assíncrona e aguarda seu resultado no segmento de chamada.</span><span class="sxs-lookup"><span data-stu-id="58832-252">Runs an asynchronous computation and awaits its result on the calling thread.</span></span> <span data-ttu-id="58832-253">Esta chamada está bloqueando.</span><span class="sxs-lookup"><span data-stu-id="58832-253">This call is blocking.</span></span>

<span data-ttu-id="58832-254">Assinatura:</span><span class="sxs-lookup"><span data-stu-id="58832-254">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

<span data-ttu-id="58832-255">Quando usar:</span><span class="sxs-lookup"><span data-stu-id="58832-255">When to use it:</span></span>

- <span data-ttu-id="58832-256">Se você precisar, use-o apenas uma vez em um aplicativo - no ponto de entrada para um executável.</span><span class="sxs-lookup"><span data-stu-id="58832-256">If you need it, use it only once in an application - at the entry point for an executable.</span></span>
- <span data-ttu-id="58832-257">Quando você não se importa com o desempenho e quer executar um conjunto de outras operações assíncronas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="58832-257">When you don't care about performance and want to execute a set of other asynchronous operations at once.</span></span>

<span data-ttu-id="58832-258">O que tomar cuidado:</span><span class="sxs-lookup"><span data-stu-id="58832-258">What to watch out for:</span></span>

- <span data-ttu-id="58832-259">A `Async.RunSynchronously` chamada bloqueia o segmento de chamada até que a execução seja concluída.</span><span class="sxs-lookup"><span data-stu-id="58832-259">Calling `Async.RunSynchronously` blocks the calling thread until the execution completes.</span></span>

### <a name="asyncstart"></a><span data-ttu-id="58832-260">Async.Start</span><span class="sxs-lookup"><span data-stu-id="58832-260">Async.Start</span></span>

<span data-ttu-id="58832-261">Inicia uma computação assíncrona no `unit`pool de segmentos que retorna .</span><span class="sxs-lookup"><span data-stu-id="58832-261">Starts an asynchronous computation in the thread pool that returns `unit`.</span></span> <span data-ttu-id="58832-262">Não espera pelo resultado.</span><span class="sxs-lookup"><span data-stu-id="58832-262">Doesn't wait for its result.</span></span> <span data-ttu-id="58832-263">Os cálculos aninhados iniciados `Async.Start` são iniciados independentemente da computação parental que os chamou.</span><span class="sxs-lookup"><span data-stu-id="58832-263">Nested computations started with `Async.Start` are started independently of the parent computation that called them.</span></span> <span data-ttu-id="58832-264">Sua vida não está ligada a nenhum cálculo dos pais.</span><span class="sxs-lookup"><span data-stu-id="58832-264">Their lifetime is not tied to any parent computation.</span></span> <span data-ttu-id="58832-265">Se a computação dos pais for cancelada, nenhum cálculo de filho será cancelado.</span><span class="sxs-lookup"><span data-stu-id="58832-265">If the parent computation is canceled, no child computations are canceled.</span></span>

<span data-ttu-id="58832-266">Assinatura:</span><span class="sxs-lookup"><span data-stu-id="58832-266">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="58832-267">Use somente quando:</span><span class="sxs-lookup"><span data-stu-id="58832-267">Use only when:</span></span>

- <span data-ttu-id="58832-268">Você tem uma computação assíncrona que não produz um resultado e/ou requer processamento de um.</span><span class="sxs-lookup"><span data-stu-id="58832-268">You have an asynchronous computation that doesn't yield a result and/or require processing of one.</span></span>
- <span data-ttu-id="58832-269">Você não precisa saber quando uma computação assíncrona é concluída.</span><span class="sxs-lookup"><span data-stu-id="58832-269">You don't need to know when an asynchronous computation completes.</span></span>
- <span data-ttu-id="58832-270">Você não se importa em qual segmento uma computação assíncrona é executada.</span><span class="sxs-lookup"><span data-stu-id="58832-270">You don't care which thread an asynchronous computation runs on.</span></span>
- <span data-ttu-id="58832-271">Você não precisa estar ciente ou relatar exceções resultantes da tarefa.</span><span class="sxs-lookup"><span data-stu-id="58832-271">You don't have any need to be aware of or report exceptions resulting from the task.</span></span>

<span data-ttu-id="58832-272">O que tomar cuidado:</span><span class="sxs-lookup"><span data-stu-id="58832-272">What to watch out for:</span></span>

- <span data-ttu-id="58832-273">Exceções levantadas por cálculos `Async.Start` iniciados não são propagadas para o chamador.</span><span class="sxs-lookup"><span data-stu-id="58832-273">Exceptions raised by computations started with `Async.Start` aren't propagated to the caller.</span></span> <span data-ttu-id="58832-274">A pilha de chamadas será completamente desenrolada.</span><span class="sxs-lookup"><span data-stu-id="58832-274">The call stack will be completely unwound.</span></span>
- <span data-ttu-id="58832-275">Qualquer trabalho (como `printfn`chamada) `Async.Start` iniciado não fará com que o efeito aconteça no segmento principal da execução de um programa.</span><span class="sxs-lookup"><span data-stu-id="58832-275">Any work (such as calling `printfn`) started with `Async.Start` won't cause the effect to happen on the main thread of a program's execution.</span></span>

## <a name="interoperate-with-net"></a><span data-ttu-id="58832-276">Interoperar com .NET</span><span class="sxs-lookup"><span data-stu-id="58832-276">Interoperate with .NET</span></span>

<span data-ttu-id="58832-277">Você pode estar trabalhando com uma biblioteca .NET ou c# codebase que usa programação assíncrona de estilo assíncrono de estilo assíncrono. [async/await](../../../standard/async.md)</span><span class="sxs-lookup"><span data-stu-id="58832-277">You may be working with a .NET library or C# codebase that uses [async/await](../../../standard/async.md)-style asynchronous programming.</span></span> <span data-ttu-id="58832-278">Como c# e a maioria das <xref:System.Threading.Tasks.Task%601> bibliotecas .NET usam os <xref:System.Threading.Tasks.Task> e `Async<'T>`tipos como suas abstrações principais em vez de , você deve cruzar um limite entre essas duas abordagens para a assincronia.</span><span class="sxs-lookup"><span data-stu-id="58832-278">Because C# and the majority of .NET libraries use the <xref:System.Threading.Tasks.Task%601> and <xref:System.Threading.Tasks.Task> types as their core abstractions rather than `Async<'T>`, you must cross a boundary between these two approaches to asynchrony.</span></span>

### <a name="how-to-work-with-net-async-and-taskt"></a><span data-ttu-id="58832-279">Como trabalhar com .NET async e`Task<T>`</span><span class="sxs-lookup"><span data-stu-id="58832-279">How to work with .NET async and `Task<T>`</span></span>

<span data-ttu-id="58832-280">Trabalhar com bibliotecas assincronias <xref:System.Threading.Tasks.Task%601> .NET e bases de código que usam (ou seja, asincronizar computações que têm valores de retorno) é simples e tem suporte interno com F#.</span><span class="sxs-lookup"><span data-stu-id="58832-280">Working with .NET async libraries and codebases that use <xref:System.Threading.Tasks.Task%601> (that is, async computations that have return values) is straightforward and has built-in support with F#.</span></span>

<span data-ttu-id="58832-281">Você pode `Async.AwaitTask` usar a função para aguardar uma computação assíncrona .NET:</span><span class="sxs-lookup"><span data-stu-id="58832-281">You can use the `Async.AwaitTask` function to await a .NET asynchronous computation:</span></span>

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

<span data-ttu-id="58832-282">Você pode `Async.StartAsTask` usar a função para passar uma computação assíncrona para um chamador .NET:</span><span class="sxs-lookup"><span data-stu-id="58832-282">You can use the `Async.StartAsTask` function to pass an asynchronous computation to a .NET caller:</span></span>

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a><span data-ttu-id="58832-283">Como trabalhar com .NET async e`Task`</span><span class="sxs-lookup"><span data-stu-id="58832-283">How to work with .NET async and `Task`</span></span>

<span data-ttu-id="58832-284">Para trabalhar com APIs que usam <xref:System.Threading.Tasks.Task> (ou seja, computação sincronia .NET que não retorna `Async<'T>` um <xref:System.Threading.Tasks.Task>valor), talvez seja necessário adicionar uma função adicional que converterá um para:</span><span class="sxs-lookup"><span data-stu-id="58832-284">To work with APIs that use <xref:System.Threading.Tasks.Task> (that is, .NET async computations that do not return a value), you may need to add an additional function that will convert an `Async<'T>` to a <xref:System.Threading.Tasks.Task>:</span></span>

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<span data-ttu-id="58832-285">Já existe `Async.AwaitTask` um que <xref:System.Threading.Tasks.Task> aceita uma entrada.</span><span class="sxs-lookup"><span data-stu-id="58832-285">There is already an `Async.AwaitTask` that accepts a <xref:System.Threading.Tasks.Task> as input.</span></span> <span data-ttu-id="58832-286">Com isso e a `startTaskFromAsyncUnit` função previamente definida, você pode iniciar e esperar <xref:System.Threading.Tasks.Task> tipos a partir de uma computação assíncrona F#.</span><span class="sxs-lookup"><span data-stu-id="58832-286">With this and the previously defined `startTaskFromAsyncUnit` function, you can start and await <xref:System.Threading.Tasks.Task> types from an F# async computation.</span></span>

## <a name="relationship-to-multi-threading"></a><span data-ttu-id="58832-287">Relação com multi-threading</span><span class="sxs-lookup"><span data-stu-id="58832-287">Relationship to multi-threading</span></span>

<span data-ttu-id="58832-288">Embora o threading seja mencionado ao longo deste artigo, há duas coisas importantes a serem lembradas:</span><span class="sxs-lookup"><span data-stu-id="58832-288">Although threading is mentioned throughout this article, there are two important things to remember:</span></span>

1. <span data-ttu-id="58832-289">Não há afinidade entre uma computação assíncrona e um segmento, a menos que explicitamente iniciado no segmento atual.</span><span class="sxs-lookup"><span data-stu-id="58832-289">There is no affinity between an asynchronous computation and a thread, unless explicitly started on the current thread.</span></span>
1. <span data-ttu-id="58832-290">Programação assíncrona em F# não é uma abstração para multi-threading.</span><span class="sxs-lookup"><span data-stu-id="58832-290">Asynchronous programming in F# is not an abstraction for multi-threading.</span></span>

<span data-ttu-id="58832-291">Por exemplo, uma computação pode realmente ser executada no segmento de chamada, dependendo da natureza do trabalho.</span><span class="sxs-lookup"><span data-stu-id="58832-291">For example, a computation may actually run on its caller's thread, depending on the nature of the work.</span></span> <span data-ttu-id="58832-292">Uma computação também poderia "saltar" entre os segmentos, emprestando-os por um pequeno período de tempo para fazer um trabalho útil entre períodos de "espera" (como quando uma chamada de rede está em trânsito).</span><span class="sxs-lookup"><span data-stu-id="58832-292">A computation could also "jump" between threads, borrowing them for a small amount of time to do useful work in between periods of "waiting" (such as when a network call is in transit).</span></span>

<span data-ttu-id="58832-293">Embora f# forneça algumas habilidades para iniciar uma computação assíncrona no segmento atual (ou explicitamente não no segmento atual), a assincronia geralmente não está associada a uma estratégia de rosca específica.</span><span class="sxs-lookup"><span data-stu-id="58832-293">Although F# provides some abilities to start an asynchronous computation on the current thread (or explicitly not on the current thread), asynchrony generally is not associated with a particular threading strategy.</span></span>

## <a name="see-also"></a><span data-ttu-id="58832-294">Confira também</span><span class="sxs-lookup"><span data-stu-id="58832-294">See also</span></span>

- [<span data-ttu-id="58832-295">O Modelo de Programação Assíncrona F#</span><span class="sxs-lookup"><span data-stu-id="58832-295">The F# Asynchronous Programming Model</span></span>](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [<span data-ttu-id="58832-296">Guia De Async F# da Jet.com</span><span class="sxs-lookup"><span data-stu-id="58832-296">Jet.com's F# Async Guide</span></span>](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [<span data-ttu-id="58832-297">F# para diversão e lucro guia de Programação Assíncrona</span><span class="sxs-lookup"><span data-stu-id="58832-297">F# for fun and profit's Asynchronous Programming guide</span></span>](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [<span data-ttu-id="58832-298">Assync em C# e F#: Gotchas assíncronas em C #</span><span class="sxs-lookup"><span data-stu-id="58832-298">Async in C# and F#: Asynchronous gotchas in C#</span></span>](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
