---
title: Byrefs
description: Saiba mais sobre os tipos byref e byref em F#, que são usados para programação de baixo nível.
ms.date: 11/04/2019
ms.openlocfilehash: 527f465ee87fe153a2deae1306b6730531dc4123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187046"
---
# <a name="byrefs"></a>Byrefs

F# tem duas principais áreas de destaque que lidam com o espaço de programação de baixo nível:

* `byref` / Os `inref` / tipos, que são ponteiros gerenciados. `outref` Eles têm restrições de uso para que você não possa compilar um programa que seja inválido no tempo de execução.
* Uma `byref`estrutura semelhante, que é uma [estrutura](structures.md) que tem semântica semelhante `byref<'T>`e as mesmas restrições de tempo de compilação que . Um exemplo <xref:System.Span%601>é .

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

## <a name="byref-inref-and-outref"></a>Byref, inref e outref

Existem três `byref`formas de:

* `inref<'T>`, um ponteiro gerenciado para ler o valor subjacente.
* `outref<'T>`, um ponteiro gerenciado para escrever para o valor subjacente.
* `byref<'T>`, um ponteiro gerenciado para ler e escrever o valor subjacente.

Pode `byref<'T>` ser passado `inref<'T>` onde um é esperado. Da mesma `byref<'T>` forma, pode-se passar onde se espera um. `outref<'T>`

## <a name="using-byrefs"></a>Usando byrefs

Para usar `inref<'T>`um , você precisa `&`obter um valor de ponteiro com :

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

Para escrever no ponteiro `outref<'T>` usando `byref<'T>`um ou , você também deve `mutable`fazer o valor que você pegar um ponteiro para .

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

Se você estiver apenas escrevendo o ponteiro `outref<'T>` em `byref<'T>`vez de lê-lo, considere usar em vez de .

### <a name="inref-semantics"></a>Semântica inref

Considere o código a seguir:

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

Semanticamente, isso significa o seguinte:

* O suporte `x` do ponteiro só pode usá-lo para ler o valor.
* Qualquer ponteiro adquirido `struct` para campos `SomeStruct` aninhados dentro é dado tipo `inref<_>`.

O seguinte também é verdadeiro:

* Não há implicação de que outros segmentos ou `x`codinomes não tenham acesso à gravação .
* Não há implicação que `SomeStruct` seja imutável em virtude de `x` ser um `inref`.

No entanto, para **are** os tipos de valor `this` F# que são `inref`imutáveis, o ponteiro é inferido como um .

Todas essas regras juntas significam que `inref` o titular de um ponteiro não pode modificar o conteúdo imediato da memória que está sendo apontada.

### <a name="outref-semantics"></a>Semântica outref

O objetivo `outref<'T>` é indicar que o ponteiro só deve ser escrito para. Inesperadamente, `outref<'T>` permite ler o valor subjacente apesar de seu nome. Isto é para fins de compatibilidade. Semanticamente, `outref<'T>` não é `byref<'T>`diferente de .

### <a name="interop-with-c"></a>Interop com C\#

C# suporta `in ref` as `out ref` palavras-chave, `ref` além de retornos. A tabela a seguir mostra como F# interpreta o que C# emite:

|C# construir|F# infere|
|------------|---------|
|`ref`valor de retorno|`outref<'T>`|
|`ref readonly`valor de retorno|`inref<'T>`|
|Parâmetro `in ref`|`inref<'T>`|
|Parâmetro `out ref`|`outref<'T>`|

A tabela a seguir mostra o que F# emite:

|F# construir|Construção emitida|
|------------|-----------------|
|Argumento `inref<'T>`|`[In]`atributo sobre o argumento|
|`inref<'T>`Retorno|`modreq`atributo sobre o valor|
|`inref<'T>`em slot abstrato ou implementação|`modreq`em argumento ou retorno|
|Argumento `outref<'T>`|`[Out]`atributo sobre o argumento|

### <a name="type-inference-and-overloading-rules"></a>Digite regras de inferência e sobrecarga

Um `inref<'T>` tipo é inferido pelo compilador F# nos seguintes casos:

1. Um parâmetro .NET ou um `IsReadOnly` tipo de retorno que tenha um atributo.
2. O `this` ponteiro em um tipo de estrutura que não tem campos mutáveis.
3. O endereço de um local `inref<_>` de memória derivado de outro ponteiro.

Quando um endereço `inref` implícito de um está sendo `SomeType` tomado, uma sobrecarga com um `inref<SomeType>`argumento de tipo é preferível a uma sobrecarga com um argumento de tipo . Por exemplo: 

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

Em ambos os casos, `System.DateTime` as sobrecargas tomadas `inref<System.DateTime>`são resolvidas em vez das sobrecargas tomadas .

## <a name="byref-like-structs"></a>Estruturas semelhantes a byref

`byref` / `inref` / Além do `outref` trio, você pode definir suas próprias estruturas `byref`que podem aderir à semântica. Isso é feito <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> com o atributo:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike`não implica `Struct`. Ambos devem estar presentes no tipo.

Uma`byref`estrutura " -like" em F# é um tipo de valor vinculado à pilha. Ele nunca é alocado no monte gerenciado. Uma `byref`estrutura semelhante é útil para programação de alto desempenho, pois é aplicada com um conjunto de verificações fortes sobre a vida útil e a não captura. As regras são:

* Eles podem ser usados como parâmetros de função, parâmetros de método, variáveis locais, retornos do método.
* Eles não podem ser membros estáticos ou de instância de uma classe ou estrutura normal.
* Eles não podem ser capturados`async` por qualquer construção de fechamento (métodos ou expressões lambda).
* Eles não podem ser usados como parâmetro genérico.

Este último ponto é crucial para a programação `|>` no estilo de pipeline F#, assim como uma função genérica que parametriza seus tipos de entrada. Essa restrição pode `|>` ser relaxada no futuro, pois é inline e não faz nenhuma chamada para funções genéricas não-inlineadas em seu corpo.

Embora essas regras restrinjam fortemente o uso, eles o fazem para cumprir a promessa de computação de alto desempenho de forma segura.

## <a name="byref-returns"></a>Byref retorna

Byref retorna de funções F# ou membros podem ser produzidos e consumidos. Ao consumir `byref`um método de retorno, o valor é implicitamente desreferenciado. Por exemplo: 

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

Para devolver um byref de valor, a variável que contém o valor deve viver mais do que o escopo atual.
Além disso, para retornar `&value` byref, use (onde o valor é uma variável que vive mais do que o escopo atual).

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

Para evitar a dereferência implícita, como passar uma referência `&x` através `x` de várias chamadas acorrentadas, use (onde está o valor).

Você também pode atribuir diretamente `byref`a um retorno . Considere o seguinte programa (altamente imperativo):

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

Um `let`valor vinculado não pode ter sua referência excedendo o escopo em que foi definido. Por exemplo, o seguinte é proibido:

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

Isso evita que você tenha resultados diferentes dependendo se você compila com otimizações ou não.
