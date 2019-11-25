---
title: Byrefs
description: Saiba mais sobre tipos ByRef e ByRef no F#, que são usados para programação de baixo nível.
ms.date: 11/04/2019
ms.openlocfilehash: 2c46cea2329b6817dd753e67c6702fb163ce2193
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976822"
---
# <a name="byrefs"></a>Byrefs

F#o tem duas áreas principais de recursos que lidam com o espaço de programação de baixo nível:

* Os `byref`/`inref`/tipos de `outref`, que são ponteiros gerenciados. Eles têm restrições de uso para que você não possa compilar um programa inválido em tempo de execução.
* Um struct `byref`como, que é uma [estrutura](structures.md) que tem semântica semelhante e as mesmas restrições de tempo de compilação que `byref<'T>`. Um exemplo é <xref:System.Span%601>.

## <a name="syntax"></a>Sintaxe

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a>ByRef, inref e outref

Há três formas de `byref`:

* `inref<'T>`, um ponteiro gerenciado para ler o valor subjacente.
* `outref<'T>`, um ponteiro gerenciado para gravar no valor subjacente.
* `byref<'T>`, um ponteiro gerenciado para ler e gravar o valor subjacente.

Um `byref<'T>` pode ser passado onde um `inref<'T>` é esperado. Da mesma forma, um `byref<'T>` pode ser passado onde um `outref<'T>` é esperado.

## <a name="using-byrefs"></a>Usando byrefs

Para usar um `inref<'T>`, você precisa obter um valor de ponteiro com `&`:

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

Para gravar no ponteiro usando um `outref<'T>` ou `byref<'T>`, você também deve fazer com que o valor para o qual você obtém um ponteiro `mutable`.

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

Se você estiver apenas escrevendo o ponteiro em vez de lê-lo, considere o uso de `outref<'T>` em vez de `byref<'T>`.

### <a name="inref-semantics"></a>Semântica Inref

Considere o código a seguir:

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

Semanticamente, isso significa o seguinte:

* O detentor do ponteiro de `x` só pode usá-lo para ler o valor.
* Qualquer ponteiro adquirido para `struct` campos aninhados em `SomeStruct` recebe `inref<_>`de tipo.

O seguinte também é verdadeiro:

* Não há implicação de que outros threads ou aliases não tenham acesso de gravação para `x`.
* Não há implicação de que `SomeStruct` seja imutável em virtude de `x` ser uma `inref`.

No entanto F# , para tipos de valor que **são** imutáveis, o ponteiro de `this` é inferido para ser um `inref`.

Todas essas regras em conjunto significam que o detentor de um ponteiro de `inref` pode não modificar o conteúdo imediato da memória que está sendo apontada.

### <a name="outref-semantics"></a>Semântica Outref

A finalidade de `outref<'T>` é indicar que o ponteiro só deve ser lido de. Inesperadamente, `outref<'T>` permite ler o valor subjacente, apesar do seu nome. Isso é para fins de compatibilidade. Semanticamente, `outref<'T>` não é diferente de `byref<'T>`.

### <a name="interop-with-c"></a>Interoperabilidade com C\#

C#dá suporte às palavras-chave `in ref` e `out ref`, além de `ref` retorna. A tabela a seguir mostra F# como o interpreta C# o que emite:

|C#construir|F#infere|
|------------|---------|
|`ref` valor de retorno|`outref<'T>`|
|`ref readonly` valor de retorno|`inref<'T>`|
|Parâmetro `in ref`|`inref<'T>`|
|Parâmetro `out ref`|`outref<'T>`|

A tabela a seguir mostra F# o que são emitidos:

|F#construir|Construção emitida|
|------------|-----------------|
|`inref<'T>` argumento|atributo de `[In]` no argumento|
|`inref<'T>` retornar|`modreq` atributo no valor|
|`inref<'T>` no slot abstrato ou na implementação|`modreq` no argumento ou retorno|
|`outref<'T>` argumento|atributo de `[Out]` no argumento|

### <a name="type-inference-and-overloading-rules"></a>Inferência de tipos e regras de sobrecarga

Um tipo de `inref<'T>` é inferido pelo F# compilador nos seguintes casos:

1. Um parâmetro .NET ou tipo de retorno que tem um atributo `IsReadOnly`.
2. O ponteiro de `this` em um tipo de struct que não tem campos mutáveis.
3. O endereço de um local de memória derivado de outro ponteiro de `inref<_>`.

Quando um endereço implícito de um `inref` está sendo obtido, uma sobrecarga com um argumento do tipo `SomeType` é preferida para uma sobrecarga com um argumento do tipo `inref<SomeType>`. Por exemplo:

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

Em ambos os casos, as sobrecargas que levam `System.DateTime` são resolvidas em vez das sobrecargas que levam `inref<System.DateTime>`.

## <a name="byref-like-structs"></a>Estruturas do tipo ByRef

Além do `byref`/`inref`/`outref` trio, você pode definir suas próprias estruturas que podem aderir à semântica do tipo `byref`. Isso é feito com o atributo <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` não implica `Struct`. Ambos devem estar presentes no tipo.

Um struct "`byref`como" no F# é um tipo de valor vinculado à pilha. Ele nunca é alocado no heap gerenciado. Uma estrutura semelhante a `byref`é útil para programação de alto desempenho, pois é imposta com o conjunto de verificações fortes sobre o tempo de vida e a não captura. As regras são:

* Eles podem ser usados como parâmetros de função, parâmetros de método, variáveis locais, método retorna.
* Eles não podem ser membros estáticos ou de instância de uma classe ou estrutura normal.
* Eles não podem ser capturados por nenhuma construção de fechamento (`async` métodos ou expressões lambda).
* Eles não podem ser usados como um parâmetro genérico.

Esse último ponto é crucial para F# a programação em estilo de pipeline, pois `|>` é uma função genérica que parametriza seus tipos de entrada. Essa restrição pode ser reduzida para `|>` no futuro, pois ela está embutida e não faz nenhuma chamada para funções genéricas não embutidas em seu corpo.

Embora essas regras restrinjam muito o uso, elas fazem isso para atender à promessa de computação de alto desempenho de maneira segura.

## <a name="byref-returns"></a>Retornos de ByRef

O ByRef retorna F# de funções ou membros pode ser produzido e consumido. Ao consumir um método de retorno de `byref`, o valor é implicitamente desreferenciado. Por exemplo:

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

Para evitar a desreferência implícita, como passar uma referência por meio de várias chamadas encadeadas, use `&x` (em que `x` é o valor).

Você também pode atribuir diretamente a um `byref`de retorno. Considere o seguinte programa (altamente imperativo):

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override _.ToString() = String.Join(' ', nums)

    member _.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn "Original sequence: %s" (c.ToString())

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn "New sequence:      %s" (c.ToString())

    0 // return an integer exit code
```

Esta é a saída:

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a>Escopo para byrefs

Um valor associado a `let`não pode ter sua referência exceder o escopo no qual ele foi definido. Por exemplo, o seguinte não é permitido:

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

Isso impede que você obtenha resultados diferentes dependendo de se você compilar com otimizações ativadas ou desativadas.
