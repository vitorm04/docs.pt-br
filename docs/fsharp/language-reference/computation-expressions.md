---
title: Expressões de computação (F#)
description: 'Saiba como criar uma sintaxe conveniente para criar cálculos em F # que podem ser sequenciados e combinados usando construções de fluxo de controle e associações.'
ms.date: 07/27/2018
ms.openlocfilehash: 4995efc757d99a575ee9fad3abf0465a32398c44
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/08/2018
ms.locfileid: "36207427"
---
# <a name="computation-expressions"></a>Expressões de computação

Expressões de computação no F # fornecem uma sintaxe conveniente para criar cálculos que podem ser sequenciados e combinados usando construções de fluxo de controle e associações. Dependendo do tipo de expressão de computação, elas podem ser consideradas como uma maneira de expressar monads, monoids, transformadores monad e functors applicative. No entanto, ao contrário de outras linguagens (como *notação* em Haskell), eles não estão vinculados a uma única abstração e não dependem de macros ou outras formas de metaprogramação para realizar uma sintaxe conveniente e sensível ao contexto.

## <a name="overview"></a>Visão geral

Computações podem assumir várias formas. A forma mais comum de computação é execução single-threaded, que é fácil de entender e modificar. No entanto, nem todos os formulários de computação são tão simples como execução single-threaded. Eis alguns exemplos:

* Cálculos não determinísticas
* Computações assíncronas
* Computações effectful
* Computações produtivas

De modo geral, há *contextual* cálculos que você deve executar em determinadas partes de um aplicativo. Escrever o código sensível ao contexto pode ser um desafio, pois é fácil de computações "vaze" fora de um determinado contexto sem abstrações para impedir que você fazer isso. Essas abstrações geralmente são um desafio para escrever por conta própria, por isso, o F # tem uma maneira generalizada fazer chamados **expressões de computação**.

Expressões de computação oferecem um modelo uniforme de sintaxe e abstração para codificação de cálculos sensíveis ao contexto.

Cada expressão de computação é apoiado por um *construtor* tipo. O tipo de construtor define as operações que estão disponíveis para a expressão de computação. Ver [criando uma nova expressão de tipo de computação](computation-expressions.md#creating-a-new-type-of-computation-expression), que mostra como criar uma expressão de cálculo personalizado.

### <a name="syntax-overview"></a>Visão geral da sintaxe

Todas as expressões de computação têm o seguinte formato:

```
builder-expr { cexper }
```

em que `builder-expr` é o nome de um tipo de construtor que define a expressão de computação, e `cexper` é o corpo de expressão da expressão de computação. Por exemplo, `async` código de expressão de cálculo pode ter esta aparência:

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

Há uma sintaxe especial, adicional disponível dentro de uma expressão de computação, conforme mostrado no exemplo anterior. Os formulários de expressão a seguir são possíveis com expressões de computação:

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

Cada uma dessas palavras-chave e outros F # palavras-chave padrão só estão disponíveis em uma expressão de computação se eles tiverem sido definidos no tipo de construtor de backup. É a única exceção a isso `match!`, que é a própria açúcar sintático para o uso de `let!` seguido por uma correspondência de padrões no resultado.

O tipo de construtor é um objeto que define os métodos especiais que regem a forma como os fragmentos da expressão de computação são combinados; ou seja, a seus métodos controlam o comportamento da expressão de computação. Outra maneira de descrever uma classe de construtor é dizer que ele permite que você personalize a operação de várias construções no F #, como loops e associações.

### `let!`

O `let!` palavra-chave associa o resultado de uma chamada para outra expressão de computação para um nome:

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

Se você associar a chamada para uma expressão de computação com `let`, você não obterá o resultado da expressão de computação. Em vez disso, você será tiver associado o valor de *não realizado* chamada para essa expressão de computação. Use `let!` para associar ao resultado.

`let!` é definido pelo `Bind(x, f)` membro no tipo de construtor.

### `do!`

O `do!` palavra-chave é para chamar uma expressão de cálculo que retorna um `unit`-como o tipo (definido pelo `Zero` membro no construtor de):

```fsharp
let doThingsAsync data url =
    async {
        do! sumbitData data url
        ...
    }
```

Para o [fluxo de trabalho assíncrono](asynchronous-workflows.md), esse tipo é `Async<unit>`. Para outras expressões de cálculo, o tipo é provavelmente será `CExpType<unit>`.

`do!` é definido pela `Bind(x, f)` membro no tipo de construtor, onde `f` produz um `unit`.

### `yield`

O `yield` palavra-chave é para retornar um valor de expressão de computação para que ele possa ser consumido como um <xref:System.Collections.Generic.IEnumerable%601>:

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

Assim como acontece com o [palavra-chave na linguagem c# yield](../../csharp/language-reference/keywords/yield.md), cada elemento na expressão de cálculo é rendido de volta como ele é iterado.

`yield` é definido pela `Yield(x)` membro no tipo de construtor, onde `x` é o item para gerar novamente.

### `yield!`

O `yield!` palavra-chave é para mesclar uma coleção de valores de uma expressão de cálculo:

```fsharp
let squares =
    seq {
        for i in 1..3 -> i * i
    }

let cubes =
    seq {
        for i in 1..3 -> i * i * i
    }

let squaresAndCubes =
    seq {
        yield! squares
        yield! cubes
    }

printfn "%A" squaresAndCubes // Prints - 1; 4; 9; 1; 8; 27
```

Quando avaliada, a expressão de computação chamado pelo `yield!` serão seus itens produziram back---individualmente, simplificar o resultado.

`yield!` é definido pela `YieldFrom(x)` membro no tipo de construtor, onde `x` é uma coleção de valores.

### `return`

O `return` palavra-chave encapsula um valor no tipo correspondente à expressão de cálculo. Além das expressões de computação usando `yield`, ele é usado para "complete" uma expressão de computação:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return` é definido pela `Return(x)` membro no tipo de construtor, onde `x` é o item a ser encapsulado.

### `return!`

O `return!` palavra-chave percebe que o valor de uma expressão de computação e encapsula o resultado no tipo correspondente à expressão de cálculo:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!` é definido pela `ReturnFrom(x)` membro no tipo de construtor, onde `x` é outra expressão de computação.

### `match!`

Começando com o F # 4.5, o `match!` palavra-chave permite que você embutir uma chamada para outra correspondência de expressão e o padrão de computação em seu resultado:

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

Ao chamar uma expressão de computação com `match!`, ele obterá o resultado da chamada, como `let!`. Isso geralmente é usado ao chamar uma expressão de computação em que o resultado é um [opcional](options.md).

## <a name="built-in-computation-expressions"></a>Expressões de computação interna

A biblioteca principal F # define três expressões de computação interna: [expressões de sequência](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md), e [expressões de consulta](query-expressions.md).

## <a name="creating-a-new-type-of-computation-expression"></a>Criar um novo tipo de expressão de computação

Você pode definir as características de suas próprias expressões de cálculo, criando uma classe de construtor e definindo determinados métodos especiais na classe. A classe de construtor, opcionalmente, pode definir os métodos, conforme listado na tabela a seguir.

A tabela a seguir descreve os métodos que podem ser usados em uma classe de construtor do fluxo de trabalho.

|**Método**|**Típica assinatura (s)**|**Descrição**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Chamado para `let!` e `do!` em expressões de computação.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Encapsula uma expressão de computação como uma função.|
|`Return`|`'T -> M<'T>`|Chamado para `return` em expressões de computação.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Chamado para `return!` em expressões de computação.|
|`Run`|`M<'T> -> M<'T>` ou<br /><br />`M<'T> -> 'T`|Executa uma expressão de computação.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` ou<br /><br />`M<unit> * M<'T> -> M<'T>`|Chamado para o sequenciamento em expressões de computação.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` ou<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Chamado para `for...do` expressões em expressões de computação.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Chamado para `try...finally` expressões em expressões de computação.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Chamado para `try...with` expressões em expressões de computação.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|Chamado para `use` ligações em expressões de computação.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Chamado para `while...do` expressões em expressões de computação.|
|`Yield`|`'T -> M<'T>`|Chamado para `yield` expressões em expressões de computação.|
|`YieldFrom`|`M<'T> -> M<'T>`|Chamado para `yield!` expressões em expressões de computação.|
|`Zero`|`unit -> M<'T>`|Chamado para vazio `else` ramificações de `if...then` expressões em expressões de computação.|

Muitos dos métodos em uma classe de construtor usam e retornam um `M<'T>` constructo, que geralmente é um tipo definido separadamente que caracteriza o tipo de computações sendo combinados, por exemplo, `Async<'T>` para fluxos de trabalho assíncronos e `Seq<'T>` para fluxos de trabalho da sequência. As assinaturas desses métodos habilitá-los a serem combinados e aninhados uns com os outros, para que o objeto de fluxo de trabalho retornado por uma construção que pode ser passado para o próximo. O compilador, quando ele analisa uma expressão de computação, converte a expressão em uma série de chamadas de função aninhada usando os métodos na tabela anterior e o código na expressão de cálculo.

A expressão aninhada é da seguinte forma:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

No código acima, as chamadas para `Run` e `Delay` são omitidos se eles não estão definidos na classe de construtor de expressão de computação. O corpo da expressão de computação, aqui é denotado como `{| cexpr |}`, é convertida em chamadas envolvendo os métodos da classe de construtor pelas conversões descritas na tabela a seguir. A expressão de cálculo `{| cexpr |}` é definido recursivamente acordo com essas traduções em que `expr` é uma expressão F # e `cexpr` é uma expressão de computação.



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
Na tabela anterior, `other-expr` descreve uma expressão que não esteja listada na tabela de caso contrário. Uma classe de construtor não precisa implementar todos os métodos e dar suporte a todas as conversões listadas na tabela anterior. Essas construções que não são implementadas não estão disponíveis em expressões de computação desse tipo. Por exemplo, se você não deseja oferecer suporte a `use` palavra-chave em suas expressões de computação, você pode omitir a definição de `Use` em sua classe de construtor.

O exemplo de código a seguir mostra uma expressão de computação que encapsula uma computação de uma série de etapas que podem ser avaliadas uma etapa por vez. Um tipo de união de discriminada `OkOrException`, codifica o estado de erro da expressão, conforme avaliado até o momento. Esse código demonstra vários padrões típicos que você pode usar em suas expressões de computação, como as implementações de texto clichê de alguns dos métodos de construtor.

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

Uma expressão de computação tem um tipo subjacente, que retorna a expressão. O tipo subjacente pode representar um resultado calculado ou uma computação atrasada que pode ser executada ou ela pode fornecer uma maneira para iterar por meio de algum tipo de coleção. No exemplo anterior, o tipo subjacente foi **eventualmente**. Uma expressão de sequência, o tipo subjacente é <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Uma expressão de consulta, o tipo subjacente é <xref:System.Linq.IQueryable?displayProperty=nameWithType>. Para um fluxo de trabalho assíncrono, o tipo subjacente é [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7). O `Async` objeto representa o trabalho seja realizado para calcular o resultado. Por exemplo, você chama [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) para executar um cálculo e retornar o resultado.

## <a name="custom-operations"></a>Operações personalizadas
Você pode definir uma operação personalizada em uma expressão de computação e usar uma operação personalizada como um operador em uma expressão de computação. Por exemplo, você pode incluir um operador de consulta em uma expressão de consulta. Quando você define uma operação personalizada, você deve definir o rendimento e métodos na expressão de cálculo. Para definir uma operação personalizada, coloque-o em uma classe de construtor para a expressão de cálculo e, em seguida, aplicar a [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19). Esse atributo usa uma cadeia de caracteres como um argumento, que é o nome a ser usado em uma operação personalizada. Esse nome entra em escopo no início da chave de abertura da expressão de computação. Portanto, você não deve usar identificadores que têm o mesmo nome que uma operação personalizada neste bloco. Por exemplo, evite o uso de identificadores como `all` ou `last` em expressões de consulta.

### <a name="extending-existing-builders-with-new-custom-operations"></a>Estendendo construtores existentes com novas operações personalizadas
Se você já tiver uma classe de construtor, suas operações personalizadas podem ser estendidas de fora dessa classe de construtor. As extensões devem ser declaradas em módulos. Namespaces não podem conter membros de extensão, exceto no mesmo arquivo e o mesmo grupo de declaração de namespace no qual o tipo é definido.

O exemplo a seguir mostra a extensão da existente `Microsoft.FSharp.Linq.QueryBuilder` classe.

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)

[Sequências](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)

[Expressões de Consulta](query-expressions.md)
