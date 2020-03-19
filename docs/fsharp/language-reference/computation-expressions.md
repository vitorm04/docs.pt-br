---
title: Expressões de computação
description: Aprenda a criar sintaxe conveniente para escrever cálculos em F# que podem ser seqüenciados e combinados usando construções de fluxo de controle e vinculações.
ms.date: 11/04/2019
ms.openlocfilehash: 55406cc12d9e6e890fe69d712f79486d23b84452
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400228"
---
# <a name="computation-expressions"></a>Expressões de computação

As expressões de computação em F# fornecem uma sintaxe conveniente para escrever cálculos que podem ser seqüenciados e combinados usando construções de fluxo de controle e vinculações. Dependendo do tipo de expressão computacional, eles podem ser pensados como uma maneira de expressar mônades, monóides, transformadores mônades e functores aplicados. No entanto, ao contrário de outras línguas (como *a notação* em Haskell), elas não estão ligadas a uma única abstração, e não dependem de macros ou outras formas de metaprogramação para realizar uma sintaxe conveniente e sensível ao contexto.

## <a name="overview"></a>Visão geral

Computações podem assumir muitas formas. A forma mais comum de computação é a execução de um segmento único, que é fácil de entender e modificar. No entanto, nem todas as formas de computação são tão simples quanto a execução de um único segmento. Alguns exemplos incluem:

- Cálculos não determinísticos
- Cálculos assíncronos
- Cálculos eficazes
- Computação generativa

Em geral, existem cálculos sensíveis ao *contexto* que você deve executar em certas partes de um aplicativo. Escrever código susceptino de um código sensível ao contexto pode ser desafiador, pois é fácil "vazar" cálculos fora de um determinado contexto sem abstrações para impedi-lo de fazê-lo. Essas abstrações são muitas vezes desafiadoras para escrever por si mesmo, e é por isso que F# tem uma maneira generalizada de fazer as chamadas **expressões computacionais.**

As expressões computacionais oferecem um modelo uniforme de sintaxe e abstração para codificação de computação sensível ao contexto.

Cada expressão de computação é apoiada por um tipo *de construtor.* O tipo de construtor define as operações disponíveis para a expressão de computação. Consulte [Criando um novo tipo de expressão de computação,](computation-expressions.md#creating-a-new-type-of-computation-expression)que mostra como criar uma expressão de computação personalizada.

### <a name="syntax-overview"></a>Visão geral da sintaxe

Todas as expressões de computação têm a seguinte forma:

```fsharp
builder-expr { cexper }
```

onde `builder-expr` está o nome de um tipo de construtor `cexper` que define a expressão de computação, e é o corpo de expressão da expressão computacional. Por exemplo, `async` o código de expressão de computação pode ser assim:

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

Há uma sintaxe adicional especial disponível dentro de uma expressão de computação, como mostrado no exemplo anterior. As seguintes formas de expressão são possíveis com expressões de computação:

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

Cada uma dessas palavras-chave e outras palavras-chave Padrão F# só estão disponíveis em uma expressão de computação se tiverem sido definidas no tipo de construtor de backup. A única exceção `match!`a isso é, que é `let!` o próprio açúcar sintático para o uso seguido de um padrão compatível com o resultado.

O tipo de construtor é um objeto que define métodos especiais que regem a forma como os fragmentos da expressão computacional são combinados; ou seja, seus métodos controlam como a expressão computacional se comporta. Outra maneira de descrever uma classe de construtores é dizer que ele permite personalizar a operação de muitas construções F#, como loops e vinculações.

### `let!`

A `let!` palavra-chave liga o resultado de uma chamada a outra expressão de computação a um nome:

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

Se você vincular a chamada a `let`uma expressão de computação com , você não obterá o resultado da expressão de computação. Em vez disso, você terá vinculado o valor da chamada *não realizada* a essa expressão de computação. Use `let!` para se ligar ao resultado.

`let!`é definido `Bind(x, f)` pelo membro no tipo de construtor.

### `do!`

A `do!` palavra-chave é para chamar uma `unit`expressão de computação `Zero` que retorna um tipo semelhante (definido pelo membro no construtor):

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

Para o fluxo de trabalho `Async<unit>` [assíncrono,](asynchronous-workflows.md)este tipo é . Para outras expressões de computação, `CExpType<unit>`é provável que o tipo seja .

`do!`é definido `Bind(x, f)` pelo membro sobre o `f` tipo `unit`de construtor, onde produz um .

### `yield`

A `yield` palavra-chave é para devolver um valor da expressão computacional <xref:System.Collections.Generic.IEnumerable%601>para que ele possa ser consumido como um :

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

Na maioria dos casos, pode ser omitido por chamadores. A maneira mais comum `yield` de `->` omitir é com o operador:

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

Para expressões mais complexas que podem render muitos valores diferentes, e talvez condicionalmente, simplesmente omitir a palavra-chave pode fazer:

```fsharp
let weekdays includeWeekend =
    seq {
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    }
```

Como com a [palavra-chave de rendimento em C#](../../csharp/language-reference/keywords/yield.md), cada elemento na expressão de computação é rendido de volta como é iterado.

`yield`é definido `Yield(x)` pelo membro no tipo `x` de construtor, onde está o item a render de volta.

### `yield!`

A `yield!` palavra-chave é para achatar uma coleção de valores de uma expressão computacional:

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

Quando avaliada, a expressão de `yield!` computação chamada terá seus itens recolhidos um a um, achatando o resultado.

`yield!`é definido `YieldFrom(x)` pelo membro sobre o `x` tipo de construtor, onde está uma coleção de valores.

Ao `yield` `yield!` contrário, deve ser explicitamente especificado. Seu comportamento não está implícito nas expressões computacionais.

### `return`

A `return` palavra-chave envolve um valor no tipo correspondente à expressão de computação. Além das expressões `yield`computacionais usando, é usado para "completar" uma expressão de computação:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return`é definido `Return(x)` pelo membro no tipo `x` de construtor, onde está o item para embrulhar.

### `return!`

A `return!` palavra-chave percebe o valor de uma expressão de computação e envoltórios que resultam no tipo correspondente à expressão de computação:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!`é definido `ReturnFrom(x)` pelo membro sobre o `x` tipo de construtor, onde está outra expressão de computação.

### `match!`

A `match!` palavra-chave permite que você inforre uma chamada para outra expressão de computação e correspondência de padrão em seu resultado:

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

Ao chamar uma expressão `match!`de computação com , `let!`ele vai perceber o resultado da chamada como . Isso é frequentemente usado ao chamar uma expressão de computação onde o resultado é [opcional](options.md).

## <a name="built-in-computation-expressions"></a>Expressões de computação incorporadas

A biblioteca principal F# define três expressões de computação incorporadas: Expressões de [seqüência,](sequences.md) [fluxos de trabalho assíncronos](asynchronous-workflows.md)e [expressões de consulta](query-expressions.md).

## <a name="creating-a-new-type-of-computation-expression"></a>Criando um novo tipo de expressão de computação

Você pode definir as características de suas próprias expressões de computação criando uma classe de construtor e definindo certos métodos especiais na classe. A classe construtora pode definir opcionalmente os métodos listados na tabela a seguir.

A tabela a seguir descreve métodos que podem ser usados em uma classe de construtor de fluxo de trabalho.

|**Método**|**Assinatura típica**|**Descrição**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Chamado `let!` e `do!` em expressões computacionais.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Envolve uma expressão de computação como função.|
|`Return`|`'T -> M<'T>`|Chamado `return` em expressões computacionais.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Chamado `return!` em expressões computacionais.|
|`Run`|`M<'T> -> M<'T>` ou<br /><br />`M<'T> -> 'T`|Executa uma expressão de computação.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` ou<br /><br />`M<unit> * M<'T> -> M<'T>`|Pediu sequenciamento em expressões computacionais.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` ou<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Pediu `for...do` expressões em expressões computacionais.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Pediu `try...finally` expressões em expressões computacionais.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Pediu `try...with` expressões em expressões computacionais.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|Pediu `use` vinculações nas expressões de computação.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Pediu `while...do` expressões em expressões computacionais.|
|`Yield`|`'T -> M<'T>`|Pediu `yield` expressões em expressões computacionais.|
|`YieldFrom`|`M<'T> -> M<'T>`|Pediu `yield!` expressões em expressões computacionais.|
|`Zero`|`unit -> M<'T>`|Pediu ramos `else` vazios de `if...then` expressões em expressões computacionais.|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|Indica que a expressão de `Run` computação é passada ao membro como uma citação. Traduz todas as instâncias de um cálculo em uma citação.|

Muitos dos métodos em uma classe `M<'T>` de construtor usam e retornam um construto, que é tipicamente um tipo `Async<'T>` definido separadamente que caracteriza `Seq<'T>` o tipo de computação sendo combinada, por exemplo, para fluxos de trabalho assíncronos e para fluxos de trabalho seqüenciais. As assinaturas desses métodos permitem que eles sejam combinados e aninhados entre si, de modo que o objeto de fluxo de trabalho retornado de uma construção possa ser passado para o próximo. O compilador, quando analisa uma expressão de computação, converte a expressão em uma série de chamadas de função aninhadas usando os métodos na tabela anterior e o código na expressão de computação.

A expressão aninhada é da seguinte forma:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

No código acima, as `Run` `Delay` chamadas são omitidas se não forem definidas na classe de construtor de expressão de computação. O corpo da expressão computacional, `{| cexpr |}`aqui denotado como , é traduzido em chamadas envolvendo os métodos da classe construtora pelas traduções descritas na tabela a seguir. A expressão `{| cexpr |}` de computação é definida recursivamente `expr` de acordo com `cexpr` essas traduções onde é uma expressão F# e é uma expressão computacional.

|Expression|Tradução|
|----------|-----------|
|<code>{ let binding in cexpr }</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{ let! pattern = expr in cexpr }</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ do! expr in cexpr }</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{ yield expr }</code>|`builder.Yield(expr)`|
|<code>{ yield! expr }</code>|`builder.YieldFrom(expr)`|
|<code>{ return expr }</code>|`builder.Return(expr)`|
|<code>{ return! expr }</code>|`builder.ReturnFrom(expr)`|
|<code>{ use pattern = expr in cexpr }</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ use! value = expr in cexpr }</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> { cexpr }))))</code>|
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else builder.Zero()</code>|
|<code>{ if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then { cexpr0 } else { cexpr1 }</code>|
|<code>{ match expr with &#124; pattern_i -> cexpr_i }</code>|<code>match expr with &#124; pattern_i -> { cexpr_i }</code>|
|<code>{ for pattern in expr do cexpr }</code>|<code>builder.For(enumeration, (fun pattern -> { cexpr }))</code>|
|<code>{ for identifier = expr1 to expr2 do cexpr }</code>|<code>builder.For(enumeration, (fun identifier -> { cexpr }))</code>|
|<code>{ while expr do cexpr }</code>|<code>builder.While(fun () -> expr, builder.Delay({ cexpr }))</code>|
|<code>{ try cexpr with &#124; pattern_i -> expr_i }</code>|<code>builder.TryWith(builder.Delay({ cexpr }), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{ try cexpr finally expr }</code>|<code>builder.TryFinally(builder.Delay( { cexpr }), (fun () -> expr))</code>|
|<code>{ cexpr1; cexpr2 }</code>|<code>builder.Combine({ cexpr1 }, { cexpr2 })</code>|
|<code>{ other-expr; cexpr }</code>|<code>expr; { cexpr }</code>|
|<code>{ other-expr }</code>|`expr; builder.Zero()`|

Na tabela anterior, `other-expr` descreve uma expressão que não está listada de outra forma na tabela. Uma classe de construtor não precisa implementar todos os métodos e suportar todas as traduções listadas na tabela anterior. Aqueles construtos que não são implementados não estão disponíveis em expressões computacionais desse tipo. Por exemplo, se você não `use` quiser apoiar a palavra-chave em suas expressões `Use` de computação, você pode omitir a definição de em sua classe de construtor.

O exemplo de código a seguir mostra uma expressão de computação que encapsula uma computação como uma série de etapas que podem ser avaliadas um passo de cada vez. Um tipo de `OkOrException`união discriminada, codifica o estado de erro da expressão como avaliado até agora. Este código demonstra vários padrões típicos que você pode usar em suas expressões de computação, como implementações de caldeiras de alguns dos métodos de construtor.

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
        | Done value -> func value
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
// returns "Done 7"
comp |> step |> step |> step |> step
```

Uma expressão de computação tem um tipo subjacente, que a expressão retorna. O tipo subjacente pode representar um resultado computado ou um cálculo atrasado que pode ser realizado, ou pode fornecer uma maneira de iterar através de algum tipo de coleta. No exemplo anterior, o tipo subjacente era **Eventualmente**. Para uma expressão de seqüência, o tipo subjacente é <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Para uma expressão de consulta, <xref:System.Linq.IQueryable?displayProperty=nameWithType>o tipo subjacente é . Para um fluxo de trabalho assíncrono, o tipo subjacente é [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7). O `Async` objeto representa o trabalho a ser realizado para calcular o resultado. Por exemplo, [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) você chama para executar um cálculo e retornar o resultado.

## <a name="custom-operations"></a>Operações personalizadas

Você pode definir uma operação personalizada em uma expressão de computação e usar uma operação personalizada como operador em uma expressão de computação. Por exemplo, você pode incluir um operador de consulta em uma expressão de consulta. Quando você define uma operação personalizada, você deve definir os métodos Rendimento e Para na expressão de computação. Para definir uma operação personalizada, coloque-a em uma classe de [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)construtor para a expressão de computação e, em seguida, aplique o . Este atributo tem uma seqüência como argumento, que é o nome a ser usado em uma operação personalizada. Este nome entra em escopo no início da cinta encaracolada de abertura da expressão de computação. Portanto, você não deve usar identificadores que tenham o mesmo nome de uma operação personalizada neste bloco. Por exemplo, evite o uso de `all` `last` identificadores como ou em expressões de consulta.

### <a name="extending-existing-builders-with-new-custom-operations"></a>Ampliação de construtores existentes com novas operações personalizadas

Se você já tem uma classe de construtor, suas operações personalizadas podem ser estendidas de fora desta classe de construtores. As extensões devem ser declaradas em módulos. Os namespaces não podem conter membros de extensão, exceto no mesmo arquivo e no mesmo grupo de declaração de namespace onde o tipo é definido.

O exemplo a seguir mostra `Microsoft.FSharp.Linq.QueryBuilder` a extensão da classe existente.

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>Confira também

- [Referência de idioma F#](index.md)
- [Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)
- [Sequências](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [Expressões de consulta](query-expressions.md)
