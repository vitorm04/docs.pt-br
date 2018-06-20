---
title: Expressões de computação (F#)
description: 'Saiba como criar uma sintaxe conveniente para escrever computações em F # que podem ser ordenadas e combinadas que usam construções de fluxo de controle e associações.'
ms.date: 05/16/2016
ms.openlocfilehash: 4995efc757d99a575ee9fad3abf0465a32398c44
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207427"
---
# <a name="computation-expressions"></a>Expressões de computação

Expressões de computação em F # fornecem uma sintaxe conveniente para criar cálculos que podem ser ordenados e combinadas que usam construções de fluxo de controle e associações. Eles podem ser usados para fornecer uma sintaxe conveniente para *mônadas*, um recurso de programação funcional que pode ser usado para gerenciar dados, controle e efeitos colaterais em programas funcionais.


## <a name="built-in-workflows"></a>Fluxos de trabalho internos

Expressões de sequência são um exemplo de uma expressão de computação, assim como fluxos de trabalho assíncronos e expressões de consulta. Para obter mais informações, consulte [sequências](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md), e [expressões de consulta](query-expressions.md).

Alguns recursos comuns a expressões de sequência e fluxos de trabalho assíncronos e ilustram a sintaxe básica de uma expressão de computação:

```fsharp
builder-name { expression }
```

A sintaxe anterior Especifica a expressão especificada é uma expressão de computação de um tipo especificado pelo *nome do construtor*. A expressão de cálculo pode ser um fluxo de trabalho interno, como `seq` ou `async`, ou pode ser algo que você definir. O *nome do construtor* é o identificador para uma instância de um tipo especial de conhecido como o *tipo de construtor*. O tipo de construtor é um tipo de classe que define os métodos especiais que controlam a forma como os fragmentos da expressão de computação são combinados, ou seja, código que controla como a expressão é executada. Outra maneira de descrever uma classe de construtor é dizer que ele permite que você personalize a operação de muitos F # construções, como loops e associações.

Em expressões de cálculo, duas formas estão disponíveis para algumas construções de linguagem comum. Você pode invocar as construções variantes usando um! (pronto) sufixo em determinadas palavras-chave, como `let!`, `do!`e assim por diante. Essas formas especiais causam determinadas funções definidas na classe de construtor para substituir o comportamento interno comum dessas operações. Esses formulários são semelhantes a `yield!` forma do `yield` palavra-chave que é usada em expressões de sequência. Para obter mais informações, consulte [sequências](sequences.md).


## <a name="creating-a-new-type-of-computation-expression"></a>Criar um novo tipo de expressão de computação
Você pode definir as características de suas próprias expressões de computação, criando uma classe de construtor e definindo certos métodos especiais na classe. A classe de construtor, opcionalmente, pode definir os métodos conforme listado na tabela a seguir.

A tabela a seguir descreve os métodos que podem ser usados em uma classe de construtor do fluxo de trabalho.


|**Método**|**Assinatura típica**|**Descrição**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Chamado para `let!` e `do!` em expressões de cálculo.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Encapsula uma expressão de computação como uma função.|
|`Return`|`'T -> M<'T>`|Chamado para `return` em expressões de cálculo.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Chamado para `return!` em expressões de cálculo.|
|`Run`|`M<'T> -> M<'T>` ou<br /><br />`M<'T> -> 'T`|Executa uma expressão de computação.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` ou<br /><br />`M<unit> * M<'T> -> M<'T>`|Chamado para sequenciamento em expressões de cálculo.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` ou<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Chamado para `for...do` expressões em expressões de computação.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Chamado para `try...finally` expressões em expressões de computação.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Chamado para `try...with` expressões em expressões de computação.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|Chamado para `use` associações em expressões de cálculo.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Chamado para `while...do` expressões em expressões de computação.|
|`Yield`|`'T -> M<'T>`|Chamado para `yield` expressões em expressões de computação.|
|`YieldFrom`|`M<'T> -> M<'T>`|Chamado para `yield!` expressões em expressões de computação.|
|`Zero`|`unit -> M<'T>`|Chamado para vazio `else` ramificações de `if...then` expressões em expressões de computação.|
Muitos dos métodos em uma classe de construtor usar e retornar um `M<'T>` construção, que é geralmente um tipo definido separadamente que caracteriza o tipo de cálculos que estão sendo combinados, por exemplo, `Async<'T>` para fluxos de trabalho assíncronos e `Seq<'T>` para fluxos de trabalho de sequência. As assinaturas dos métodos a seguir permitem que sejam combinadas e aninhados entre si, para que o objeto de fluxo de trabalho retornado de uma construção pode ser passado para a próxima. O compilador, quando ele analisa uma expressão de computação, converte a expressão em uma série de chamadas de função aninhada usando os métodos na tabela anterior e o código na expressão de cálculo.

A expressão aninhada é da seguinte forma:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

No código acima, as chamadas para `Run` e `Delay` são omitidos se eles não estão definidos na classe do construtor de expressão de computação. O corpo da expressão de computação, aqui é denotado como `{| cexpr |}`, é convertida em chamadas envolvendo os métodos da classe de construtor, as conversões descritas na tabela a seguir. A expressão de computação `{| cexpr |}` é definido recursivamente acordo com essas conversões onde `expr` é uma expressão do F # e `cexpr` é uma expressão de computação.



|Expressão|Conversão|
|----------|-----------|
|<code>{&#124; let binding in cexpr &#124;}</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{&#124; let! pattern = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; do! expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; yield expr &#124;}</code>|`builder.Yield(expr)`|
|<code>{&#124; yield! expr &#124;}</code>|`builder.YieldFrom(expr)`|
|<code>{&#124; return expr &#124;}</code>|`builder.Return(expr)`|
|<code>{&#124; return! expr &#124;}</code>|`builder.ReturnFrom(expr)`|
|<code>{&#124; use pattern = expr in cexpr &#124;}</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; use! value = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> {&#124; cexpr &#124;}))))</code>|
|<code>{&#124; if expr then cexpr0 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else binder.Zero()</code>|
|<code>{&#124; if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else {&#124; cexpr1 &#124;}</code>|
|<code>{&#124; match expr with &#124; pattern_i -> cexpr_i &#124;}</code>|<code>match expr with &#124; pattern_i -> {&#124; cexpr_i &#124;}</code>|
|<code>{&#124; for pattern in expr do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; for identifier = expr1 to expr2 do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun identifier -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|
Na tabela anterior, `other-expr` descreve uma expressão que não esteja listada na tabela de outra forma. Uma classe de construtor não é necessário implementar todos os métodos e dar suporte a todas as traduções listadas na tabela anterior. As construções que não são implementadas não estão disponíveis em expressões de computação desse tipo. Por exemplo, se você não deseja dar suporte a `use` palavra-chave em suas expressões de computação, você pode omitir a definição de `Use` em sua classe de construtor.

O exemplo de código a seguir mostra uma expressão de computação que encapsula uma computação de uma série de etapas que podem ser avaliados uma etapa por vez. Um tipo de união de discriminada `OkOrException`, codifica o estado de erro da expressão, conforme avaliado até o momento. Esse código demonstra vários padrões comuns que você pode usar em expressões de computação, como implementações clichê de alguns dos métodos de construtor.

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

Uma expressão de computação tem um tipo subjacente, a expressão retorna. O tipo subjacente pode representar um resultado calculado ou uma computação atrasada que pode ser executada, ou pode fornecer uma maneira para iterar por meio de algum tipo de coleção. No exemplo anterior, o tipo subjacente foi **eventualmente**. Para uma expressão de sequência, o tipo subjacente é <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Para uma expressão de consulta, o tipo subjacente é <xref:System.Linq.IQueryable?displayProperty=nameWithType>. Para um fluxo de trabalho assíncrona, o tipo subjacente é [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7). O `Async` objeto representa o trabalho a ser executado para calcular o resultado. Por exemplo, chamar [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) para executar uma computação e retorna o resultado.

## <a name="custom-operations"></a>Operações personalizadas
Você pode definir uma operação personalizada em uma expressão de computação e usar uma operação personalizada como um operador em uma expressão de computação. Por exemplo, você pode incluir um operador de consulta em uma expressão de consulta. Quando você define uma operação personalizada, você deve definir o rendimento e métodos na expressão de cálculo. Para definir uma operação personalizada, colocá-lo em uma classe de construtor para a expressão de cálculo e, em seguida, aplicar o [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19). Este atributo tem uma cadeia de caracteres como um argumento, que é o nome a ser usado em uma operação personalizada. Esse nome entra em escopo no início da chave de abertura da expressão de computação. Portanto, você não deve usar identificadores que têm o mesmo nome que uma operação personalizada neste bloco. Por exemplo, evite o uso de identificadores como `all` ou `last` em expressões de consulta.

## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)

[Sequências](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)

[Expressões de Consulta](query-expressions.md)
