---
title: "Expressões de computação (F#)"
description: "Saiba como criar uma sintaxe conveniente para escrever computações em F # que podem ser ordenadas e combinadas que usam construções de fluxo de controle e associações."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: acabbf5d-fbb8-479f-894c-7251bf16c8c3
ms.openlocfilehash: 15ba2e167efc1d295d81439dcf85bc7272e05265
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="computation-expressions"></a><span data-ttu-id="7901b-104">Expressões de computação</span><span class="sxs-lookup"><span data-stu-id="7901b-104">Computation Expressions</span></span>

<span data-ttu-id="7901b-105">Expressões de computação em F # fornecem uma sintaxe conveniente para criar cálculos que podem ser ordenados e combinadas que usam construções de fluxo de controle e associações.</span><span class="sxs-lookup"><span data-stu-id="7901b-105">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="7901b-106">Eles podem ser usados para fornecer uma sintaxe conveniente para *mônadas*, um recurso de programação funcional que pode ser usado para gerenciar dados, controle e efeitos colaterais em programas funcionais.</span><span class="sxs-lookup"><span data-stu-id="7901b-106">They can be used to provide a convenient syntax for *monads*, a functional programming feature that can be used to manage data, control, and side effects in functional programs.</span></span>


## <a name="built-in-workflows"></a><span data-ttu-id="7901b-107">Fluxos de trabalho internos</span><span class="sxs-lookup"><span data-stu-id="7901b-107">Built-in Workflows</span></span>
<span data-ttu-id="7901b-108">Expressões de sequência são um exemplo de uma expressão de computação, assim como fluxos de trabalho assíncronos e expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="7901b-108">Sequence expressions are an example of a computation expression, as are asynchronous workflows and query expressions.</span></span> <span data-ttu-id="7901b-109">Para obter mais informações, consulte [sequências](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md), e [expressões de consulta](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="7901b-109">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

<span data-ttu-id="7901b-110">Alguns recursos comuns a expressões de sequência e fluxos de trabalho assíncronos e ilustram a sintaxe básica de uma expressão de computação:</span><span class="sxs-lookup"><span data-stu-id="7901b-110">Certain features are common to both sequence expressions and asynchronous workflows and illustrate the basic syntax for a computation expression:</span></span>

```fsharp
builder-name { expression }
```

<span data-ttu-id="7901b-111">A sintaxe anterior Especifica a expressão especificada é uma expressão de computação de um tipo especificado pelo *nome do construtor*.</span><span class="sxs-lookup"><span data-stu-id="7901b-111">The previous syntax specifies that the given expression is a computation expression of a type specified by *builder-name*.</span></span> <span data-ttu-id="7901b-112">A expressão de cálculo pode ser um fluxo de trabalho interno, como `seq` ou `async`, ou pode ser algo que você definir.</span><span class="sxs-lookup"><span data-stu-id="7901b-112">The computation expression can be a built-in workflow, such as `seq` or `async`, or it can be something you define.</span></span> <span data-ttu-id="7901b-113">O *nome do construtor* é o identificador para uma instância de um tipo especial de conhecido como o *tipo de construtor*.</span><span class="sxs-lookup"><span data-stu-id="7901b-113">The *builder-name* is the identifier for an instance of a special type known as the *builder type*.</span></span> <span data-ttu-id="7901b-114">O tipo de construtor é um tipo de classe que define os métodos especiais que controlam a forma como os fragmentos da expressão de computação são combinados, ou seja, código que controla como a expressão é executada.</span><span class="sxs-lookup"><span data-stu-id="7901b-114">The builder type is a class type that defines special methods that govern the way the fragments of the computation expression are combined, that is, code that controls how the expression executes.</span></span> <span data-ttu-id="7901b-115">Outra maneira de descrever uma classe de construtor é dizer que ele permite que você personalize a operação de muitos F # construções, como loops e associações.</span><span class="sxs-lookup"><span data-stu-id="7901b-115">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

<span data-ttu-id="7901b-116">Em expressões de cálculo, duas formas estão disponíveis para algumas construções de linguagem comum.</span><span class="sxs-lookup"><span data-stu-id="7901b-116">In computation expressions, two forms are available for some common language constructs.</span></span> <span data-ttu-id="7901b-117">Você pode invocar as construções variantes usando um!</span><span class="sxs-lookup"><span data-stu-id="7901b-117">You can invoke the variant constructs by using a !</span></span> <span data-ttu-id="7901b-118">(pronto) sufixo em determinadas palavras-chave, como `let!`, `do!`e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="7901b-118">(bang) suffix on certain keywords, such as `let!`, `do!`, and so on.</span></span> <span data-ttu-id="7901b-119">Essas formas especiais causam determinadas funções definidas na classe de construtor para substituir o comportamento interno comum dessas operações.</span><span class="sxs-lookup"><span data-stu-id="7901b-119">These special forms cause certain functions defined in the builder class to replace the ordinary built-in behavior of these operations.</span></span> <span data-ttu-id="7901b-120">Esses formulários são semelhantes a `yield!` forma do `yield` palavra-chave que é usada em expressões de sequência.</span><span class="sxs-lookup"><span data-stu-id="7901b-120">These forms resemble the `yield!` form of the `yield` keyword that is used in sequence expressions.</span></span> <span data-ttu-id="7901b-121">Para obter mais informações, consulte [sequências](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="7901b-121">For more information, see [Sequences](sequences.md).</span></span>


## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="7901b-122">Criar um novo tipo de expressão de computação</span><span class="sxs-lookup"><span data-stu-id="7901b-122">Creating a New Type of Computation Expression</span></span>
<span data-ttu-id="7901b-123">Você pode definir as características de suas próprias expressões de computação, criando uma classe de construtor e definindo certos métodos especiais na classe.</span><span class="sxs-lookup"><span data-stu-id="7901b-123">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="7901b-124">A classe de construtor, opcionalmente, pode definir os métodos conforme listado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="7901b-124">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="7901b-125">A tabela a seguir descreve os métodos que podem ser usados em uma classe de construtor do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7901b-125">The following table describes methods that can be used in a workflow builder class.</span></span>


|<span data-ttu-id="7901b-126">**Método**</span><span class="sxs-lookup"><span data-stu-id="7901b-126">**Method**</span></span>|<span data-ttu-id="7901b-127">**Assinatura típica**</span><span class="sxs-lookup"><span data-stu-id="7901b-127">**Typical signature(s)**</span></span>|<span data-ttu-id="7901b-128">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="7901b-128">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="7901b-129">Chamado para `let!` e `do!` em expressões de cálculo.</span><span class="sxs-lookup"><span data-stu-id="7901b-129">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="7901b-130">Encapsula uma expressão de computação como uma função.</span><span class="sxs-lookup"><span data-stu-id="7901b-130">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="7901b-131">Chamado para `return` em expressões de cálculo.</span><span class="sxs-lookup"><span data-stu-id="7901b-131">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="7901b-132">Chamado para `return!` em expressões de cálculo.</span><span class="sxs-lookup"><span data-stu-id="7901b-132">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="7901b-133">`M<'T> -> M<'T>` ou</span><span class="sxs-lookup"><span data-stu-id="7901b-133">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="7901b-134">Executa uma expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="7901b-134">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="7901b-135">`M<'T> * M<'T> -> M<'T>` ou</span><span class="sxs-lookup"><span data-stu-id="7901b-135">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="7901b-136">Chamado para sequenciamento em expressões de cálculo.</span><span class="sxs-lookup"><span data-stu-id="7901b-136">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="7901b-137">`seq<'T> * ('T -> M<'U>) -> M<'U>` ou</span><span class="sxs-lookup"><span data-stu-id="7901b-137">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="7901b-138">Chamado para `for...do` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="7901b-138">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="7901b-139">Chamado para `try...finally` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="7901b-139">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="7901b-140">Chamado para `try...with` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="7901b-140">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="7901b-141">Chamado para `use` associações em expressões de cálculo.</span><span class="sxs-lookup"><span data-stu-id="7901b-141">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="7901b-142">Chamado para `while...do` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="7901b-142">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="7901b-143">Chamado para `yield` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="7901b-143">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="7901b-144">Chamado para `yield!` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="7901b-144">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="7901b-145">Chamado para vazio `else` ramificações de `if...then` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="7901b-145">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
<span data-ttu-id="7901b-146">Muitos dos métodos em uma classe de construtor usar e retornar um `M<'T>` construção, que é geralmente um tipo definido separadamente que caracteriza o tipo de cálculos que estão sendo combinados, por exemplo, `Async<'T>` para fluxos de trabalho assíncronos e `Seq<'T>` para fluxos de trabalho de sequência.</span><span class="sxs-lookup"><span data-stu-id="7901b-146">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="7901b-147">As assinaturas dos métodos a seguir permitem que sejam combinadas e aninhados entre si, para que o objeto de fluxo de trabalho retornado de uma construção pode ser passado para a próxima.</span><span class="sxs-lookup"><span data-stu-id="7901b-147">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="7901b-148">O compilador, quando ele analisa uma expressão de computação, converte a expressão em uma série de chamadas de função aninhada usando os métodos na tabela anterior e o código na expressão de cálculo.</span><span class="sxs-lookup"><span data-stu-id="7901b-148">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="7901b-149">A expressão aninhada é da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="7901b-149">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="7901b-150">No código acima, as chamadas para `Run` e `Delay` são omitidos se eles não estão definidos na classe do construtor de expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="7901b-150">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="7901b-151">O corpo da expressão de computação, aqui é denotado como `{| cexpr |}`, é convertida em chamadas envolvendo os métodos da classe de construtor, as conversões descritas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="7901b-151">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="7901b-152">A expressão de computação `{| cexpr |}` é definido recursivamente acordo com essas conversões onde `expr` é uma expressão do F # e `cexpr` é uma expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="7901b-152">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>



|<span data-ttu-id="7901b-153">Expressão</span><span class="sxs-lookup"><span data-stu-id="7901b-153">Expression</span></span>|<span data-ttu-id="7901b-154">Conversão</span><span class="sxs-lookup"><span data-stu-id="7901b-154">Translation</span></span>|
|----------|-----------|
|<code>{&#124; let binding in cexpr &#124;}</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{&#124; let! pattern = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; do! expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; yield expr &#124;}</code>|`builder.Yield(expr)`|
|<code>{&#124; yield! expr &#124;}</code>|`builder.YieldFrom(expr)`|
|<code>{&#124; return expr &#124;}<code>|`builder.Return(expr)`|
|<code>{&#124; return! expr &#124;}</code>|`builder.ReturnFrom(expr)`|
|<code>{&#124; use pattern = expr in cexpr &#124;}</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; use! value = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> {&#124; cexpr &#124;}))))</code>|
|<code>{&#124; if expr then cexpr0 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else binder.Zero()</code>|
|<code>{&#124; if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else {&#124; cexpr1 &#124;}</code>|
|<code>{&#124; match expr with &#124; pattern_i -> cexpr_i &#124;}</code>|<code>match expr with &#124; pattern_i -> {&#124; cexpr_i &#124;}</code>|
|<code>{&#124; for pattern in expr do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; for identifier = expr1 to expr2 do cexpr &#124;}<code>|<code>builder.For(enumeration, (fun identifier -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|
<span data-ttu-id="7901b-155">Na tabela anterior, `other-expr` descreve uma expressão que não esteja listada na tabela de outra forma.</span><span class="sxs-lookup"><span data-stu-id="7901b-155">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="7901b-156">Uma classe de construtor não é necessário implementar todos os métodos e dar suporte a todas as traduções listadas na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="7901b-156">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="7901b-157">As construções que não são implementadas não estão disponíveis em expressões de computação desse tipo.</span><span class="sxs-lookup"><span data-stu-id="7901b-157">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="7901b-158">Por exemplo, se você não deseja dar suporte a `use` palavra-chave em suas expressões de computação, você pode omitir a definição de `Use` em sua classe de construtor.</span><span class="sxs-lookup"><span data-stu-id="7901b-158">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="7901b-159">O exemplo de código a seguir mostra uma expressão de computação que encapsula uma computação de uma série de etapas que podem ser avaliados uma etapa por vez.</span><span class="sxs-lookup"><span data-stu-id="7901b-159">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="7901b-160">Um tipo de união de discriminada `OkOrException`, codifica o estado de erro da expressão, conforme avaliado até o momento.</span><span class="sxs-lookup"><span data-stu-id="7901b-160">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="7901b-161">Esse código demonstra vários padrões comuns que você pode usar em expressões de computação, como implementações clichê de alguns dos métodos de construtor.</span><span class="sxs-lookup"><span data-stu-id="7901b-161">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> NotYetDone (fun () -> func value)
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res -> 
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally 
            (whileLoop 
                (fun () -> ie.MoveNext()) 
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this 
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "NotYetDone <closure>"
comp |> step |> step |> step |> step |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step |> step |> step |> step |> step
```

<span data-ttu-id="7901b-162">Uma expressão de computação tem um tipo subjacente, a expressão retorna.</span><span class="sxs-lookup"><span data-stu-id="7901b-162">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="7901b-163">O tipo subjacente pode representar um resultado calculado ou uma computação atrasada que pode ser executada, ou pode fornecer uma maneira para iterar por meio de algum tipo de coleção.</span><span class="sxs-lookup"><span data-stu-id="7901b-163">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="7901b-164">No exemplo anterior, o tipo subjacente foi **eventualmente**.</span><span class="sxs-lookup"><span data-stu-id="7901b-164">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="7901b-165">Para uma expressão de sequência, o tipo subjacente é <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7901b-165">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7901b-166">Para uma expressão de consulta, o tipo subjacente é <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7901b-166">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7901b-167">Para um fluxo de trabalho assíncrona, o tipo subjacente é [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span><span class="sxs-lookup"><span data-stu-id="7901b-167">For an asychronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="7901b-168">O `Async` objeto representa o trabalho a ser executado para calcular o resultado.</span><span class="sxs-lookup"><span data-stu-id="7901b-168">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="7901b-169">Por exemplo, chamar [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) para executar uma computação e retorna o resultado.</span><span class="sxs-lookup"><span data-stu-id="7901b-169">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="7901b-170">Operações personalizadas</span><span class="sxs-lookup"><span data-stu-id="7901b-170">Custom Operations</span></span>
<span data-ttu-id="7901b-171">Você pode definir uma operação personalizada em uma expressão de computação e usar uma operação personalizada como um operador em uma expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="7901b-171">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="7901b-172">Por exemplo, você pode incluir um operador de consulta em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="7901b-172">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="7901b-173">Quando você define uma operação personalizada, você deve definir o rendimento e métodos na expressão de cálculo.</span><span class="sxs-lookup"><span data-stu-id="7901b-173">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="7901b-174">Para definir uma operação personalizada, colocá-lo em uma classe de construtor para a expressão de cálculo e, em seguida, aplicar o [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span><span class="sxs-lookup"><span data-stu-id="7901b-174">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="7901b-175">Este atributo tem uma cadeia de caracteres como um argumento, que é o nome a ser usado em uma operação personalizada.</span><span class="sxs-lookup"><span data-stu-id="7901b-175">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="7901b-176">Esse nome entra em escopo no início da chave de abertura da expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="7901b-176">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="7901b-177">Portanto, você não deve usar identificadores que têm o mesmo nome que uma operação personalizada neste bloco.</span><span class="sxs-lookup"><span data-stu-id="7901b-177">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="7901b-178">Por exemplo, evite o uso de identificadores como `all` ou `last` em expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="7901b-178">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

## <a name="see-also"></a><span data-ttu-id="7901b-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7901b-179">See Also</span></span>
[<span data-ttu-id="7901b-180">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="7901b-180">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="7901b-181">Fluxos de Trabalho Assíncronos</span><span class="sxs-lookup"><span data-stu-id="7901b-181">Asynchronous Workflows</span></span>](asynchronous-workflows.md)

[<span data-ttu-id="7901b-182">Sequências</span><span class="sxs-lookup"><span data-stu-id="7901b-182">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)

[<span data-ttu-id="7901b-183">Expressões de Consulta</span><span class="sxs-lookup"><span data-stu-id="7901b-183">Query Expressions</span></span>](query-expressions.md)
