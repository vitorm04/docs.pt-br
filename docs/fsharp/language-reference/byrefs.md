---
title: 'Zkratka (F #)'
description: 'Saiba mais sobre byref e byref tipos em F #, que são usados para programação de nível baixo.'
ms.date: 09/02/2018
ms.openlocfilehash: 6131104e4325f77da84368c337f998c6b2b5309b
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030808"
---
# <a name="byrefs"></a>Zkratka

O F # tem duas principais áreas de recurso que lidam no espaço de programação de nível baixo:

* O `byref` / `inref` / `outref` tipos, que são um ponteiros gerenciados. Eles têm restrições no uso, de modo que você não pode compilar um programa que é inválido em tempo de execução.
* Um `byref`-como struct, que é um [estrutura](structures.md) que tem semântica semelhante e as mesmas restrições de tempo de compilação que `byref<'T>`. Um exemplo é <xref:System.Span%601>.

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
* `outref<'T>`, um ponteiro gerenciado para gravar o valor subjacente.
* `byref<'T>`, um ponteiro gerenciado para ler e gravar o valor subjacente.

Um `byref<'T>` pode ser passado em que um `inref<'T>` é esperado. Da mesma forma, uma `byref<'T>` pode ser passado em que um `outref<'T>` é esperado.

## <a name="using-byrefs"></a>Usando zkratka

Para usar um `inref<'T>`, você precisa obter um valor de ponteiro com `&`:

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let dt = DateTime.Now
f &dt // Pass a pointer to 'dt'
```

Para gravar o ponteiro, usando um `outref<'T>` ou `byref<'T>`, você também deve verificar o valor que você Pegue um ponteiro para `mutable`.

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

Se você estiver apenas escrevendo o ponteiro em vez de lê-lo, considere o uso `outref<'T>` em vez de `byref<'T>`.

### <a name="inref-semantics"></a>Semântica de Inref

Considere o código a seguir:

```fsharp
let f (x: inref<SomeStruct>) = s.SomeField
```

Semanticamente, isso significa que o seguinte:

* O proprietário do `x` ponteiro só pode usá-lo para ler o valor.
* Adquiridos, qualquer ponteiro para `struct` campos aninhados `SomeStruct` recebem o tipo `inref<_>`.

O seguinte também é verdadeiro:

* Não há nenhuma implicação que outros threads ou aliases não tem acesso de gravação ao `x`.
* Não há nenhuma implicação que `SomeStruct` é imutável em virtude da `x` sendo um `inref`.

No entanto, para F # tipos de valores que **estão** imutável, o `this` ponteiro é inferido para ser um `inref`.

Todas essas regras juntas significam que o proprietário de um `inref` ponteiro não pode modificar o conteúdo imediato da memória que está sendo apontado.

### <a name="outref-semantics"></a>Semântica de Outref

A finalidade de `outref<'T>` é para indicar que o ponteiro só deve ser lidos do. Inesperadamente, `outref<'T>` permite ler subjacente valor apesar do nome. Isso é para fins de compatibilidade. Semanticamente, `outref<'T>` não é diferente de `byref<'T>`.

### <a name="interop-with-c"></a>Interoperabilidade com c# #

C# é compatível com o `in ref` e `out ref` palavras-chave, além de `ref` retorna. A tabela a seguir mostra como F # interpreta o que c# emite:

|Construção de linguagem c#|F # infere|
|------------|---------|
|`ref` Valor de retorno|`outref<'T>`|
|`ref readonly` Valor de retorno|`inref<'T>`|
|Parâmetro `in ref`|`inref<'T>`|
|Parâmetro `out ref`|`outref<'T>`|

A tabela a seguir mostra o que F # emite:

|Construção F #|Construção emitida|
|------------|-----------------|
|`inref<'T>` argumento|`[In]` atributo no argumento|
|`inref<'T>` Retornar|`modreq` atributo de valor|
|`inref<'T>` no slot abstrata ou na implementação|`modreq` no argumento ou retorno|
|`outref<'T>` argumento|`[Out]` atributo no argumento|

### <a name="type-inference-and-overloading-rules"></a>Inferência de tipo e a sobrecarga de regras

Um `inref<'T>` tipo é inferido pelo compilador do F # nos seguintes casos:

1. Um tipo de parâmetro ou retornado de .NET que tem um `IsReadOnly` atributo.
2. O `this` ponteiro em um tipo de struct que não tem nenhum campo mutável.
3. O endereço de um local de memória é derivado de outro `inref<_>` ponteiro.

Quando um endereço implícito de um `inref` estiver sendo feito, uma sobrecarga com um argumento do tipo `SomeType` é preferencial para uma sobrecarga com um argumento do tipo `inref<SomeType>`. Por exemplo:

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

Em ambos os casos, as sobrecargas `System.DateTime` são resolvidos em vez de sobrecargas `inref<System.DateTime>`.

## <a name="byref-like-structs"></a>Estruturas do tipo ByRef

Além de `byref` / `inref` / `outref` trio, você pode definir seus próprios structs que podem aderir a `byref`-como semântica. Isso é feito com o <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> atributo:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` não implica `Struct`. Ambos devem estar presentes no tipo.

Um "`byref`-como" struct em F # é um tipo de valor de limite de pilha. Ele nunca é alocado no heap gerenciado. Um `byref`-como o struct é útil para programação de alto desempenho, como ela é imposta com o conjunto de verificações forte sobre tempo de vida e não captura. As regras são:

* Eles podem ser usados como parâmetros de função, os parâmetros de método, variáveis locais, método retorna.
* Eles não podem ser estáticos ou membros de uma classe ou struct normal da instância.
* Eles não podem ser capturados por qualquer construção de fechamento (`async` métodos ou expressões lambda).
* Eles não podem ser usados como um parâmetro genérico.

Esse último ponto é crucial para F # programação no estilo do pipeline, como `|>` é uma função genérica que parametriza seus tipos de entrada. Essa restrição pode ser reduzida a `|>` no futuro, conforme ele é embutido e não faz todas as chamadas para funções genéricas não embutida em seu corpo.

Embora essas regras altamente restringem o uso, eles fazem isso para cumprir a promessa de computação de alto desempenho de maneira segura.

## <a name="byref-returns"></a>Retornos de ByRef

Retornos de ByRef do functions em F # ou os membros podem ser gerados e consumidos. Ao consumir um `byref`-método de retorno, o valor é deferência implícita. Por exemplo:

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

Para evitar a desreferência implícita, como passar uma referência por meio de várias chamadas encadeadas, use `&x` (onde `x` é o valor).

Você pode também atribuir diretamente a um retorno `byref`. Considere o seguinte programa (altamente obrigatório):

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override __.ToString() = String.Join(' ', nums)

    member __.FindLargestSmallerThan(target: int) =
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

## <a name="scoping-for-byrefs"></a>Escopo para zkratka

Um `let`-valor associado não pode ter sua referência excedam o escopo no qual ele foi definido. Por exemplo, o seguinte não é permitido:

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

Isso impede que você obter resultados diferentes dependendo se você compilar com otimizações ativada ou desativada.
