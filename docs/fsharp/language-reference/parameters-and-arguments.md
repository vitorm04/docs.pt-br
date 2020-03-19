---
title: Parâmetros e argumentos
description: Aprenda sobre o suporte à linguagem F# para definir parâmetros e passar argumentos para funções, métodos e propriedades.
ms.date: 12/04/2019
ms.openlocfilehash: b234ef939128e7cf09d35f9580d4d5010d7dc639
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400193"
---
# <a name="parameters-and-arguments"></a>Parâmetros e argumentos

Este tópico descreve o suporte à linguagem para definir parâmetros e passar argumentos para funções, métodos e propriedades. Ele inclui informações sobre como passar por referência, e como definir e usar métodos que podem levar um número variável de argumentos.

## <a name="parameters-and-arguments"></a>Parâmetros e argumentos

O *parâmetro* de termo é usado para descrever os nomes para valores que devem ser fornecidos. O termo *argumento* é usado para os valores previstos para cada parâmetro.

Os parâmetros podem ser especificados em tuple ou curried forma, ou em alguma combinação dos dois. Você pode passar argumentos usando um nome de parâmetro explícito. Os parâmetros dos métodos podem ser especificados como opcionais e dado um valor padrão.

## <a name="parameter-patterns"></a>Padrões de parâmetros

Os parâmetros fornecidos às funções e métodos são, em geral, padrões separados por espaços. Isso significa que, em princípio, qualquer um dos padrões descritos em [Match Expressions](match-expressions.md) pode ser usado em uma lista de parâmetros para uma função ou membro.

Os métodos geralmente usam a forma tuplo de argumentos de passagem. Isso alcança um resultado mais claro da perspectiva de outras línguas .NET porque a forma tupla corresponde à maneira como os argumentos são passados nos métodos .NET.

A forma curried é mais frequentemente usada `let` com funções criadas usando amarras.

O pseudocódigo a seguir mostra exemplos de argumentos tuplos e curried.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Formas combinadas são possíveis quando alguns argumentos estão em tuplas e alguns não.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Outros padrões também podem ser usados em listas de parâmetros, mas se o padrão de parâmetro não corresponder a todas as entradas possíveis, pode haver uma correspondência incompleta no tempo de execução. A `MatchFailureException` exceção é gerada quando o valor de um argumento não corresponde aos padrões especificados na lista de parâmetros. O compilador emite um aviso quando um padrão de parâmetro permite correspondências incompletas. Pelo menos um outro padrão é comumente útil para listas de parâmetros, e esse é o padrão curinga. Você usa o padrão curinga em uma lista de parâmetros quando você simplesmente quer ignorar quaisquer argumentos que são fornecidos. O código a seguir ilustra o uso do padrão curinga em uma lista de argumentos.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

O padrão curinga pode ser útil sempre que você não precisar dos argumentos passados, como no ponto de entrada principal de um programa, quando você não está interessado nos argumentos de linha de comando que normalmente são fornecidos como uma matriz de strings, como no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Outros padrões que às vezes `as` são usados em argumentos são o padrão, e padrões identificadores associados a sindicatos discriminados e padrões ativos. Você pode usar o padrão sindical discriminado em caso único da seguinte forma.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

A saída é a seguinte.

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Padrões ativos podem ser úteis como parâmetros, por exemplo, ao transformar um argumento em um formato desejado, como no exemplo a seguir:

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

Você pode `as` usar o padrão para armazenar um valor compatível como um valor local, como é mostrado na seguinte linha de código.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Outro padrão que é usado ocasionalmente é uma função que deixa o último argumento sem nome, fornecendo, como o corpo da função, uma expressão lambda que imediatamente executa uma correspondência padrão no argumento implícito. Um exemplo disso é a seguinte linha de código.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Este código define uma função que pega `true` uma lista genérica `false` e retorna se a lista estiver vazia, e de outra forma. O uso de tais técnicas pode tornar o código mais difícil de ler.

Ocasionalmente, padrões que envolvem correspondências incompletas são úteis, por exemplo, se você sabe que as listas em seu programa têm apenas três elementos, você pode usar um padrão como o seguinte em uma lista de parâmetros.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

O uso de padrões que têm correspondências incompletas é melhor reservado para prototipagem rápida e outros usos temporários. O compilador emitirá um aviso para tal código. Tais padrões não podem cobrir o caso geral de todas as entradas possíveis e, portanto, não são adequados para APIs componentes.

## <a name="named-arguments"></a>Argumentos nomeados

Os argumentos para métodos podem ser especificados por posição em uma lista de argumentos separada por comma, ou podem ser passados para um método explicitamente fornecendo o nome, seguido de um sinal igual e o valor a ser passado. Se especificado fornecendo o nome, eles podem aparecer em uma ordem diferente da usada na declaração.

Argumentos nomeados podem tornar o código mais legível e mais adaptável a certos tipos de alterações na API, como uma reordenação de parâmetros de método.

Argumentos nomeados são permitidos apenas `let`para métodos, não para funções vinculadas, valores de função ou expressões lambda.

O exemplo de código a seguir demonstra o uso de argumentos nomeados.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

Em uma chamada para um construtor de classe, você pode definir os valores das propriedades da classe usando uma sintaxe semelhante à dos argumentos nomeados. O exemplo a seguir mostra essa sintaxe.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Para obter mais informações, consulte [Construtores (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>Parâmetros opcionais

Você pode especificar um parâmetro opcional para um método usando um ponto de interrogação na frente do nome do parâmetro. Os parâmetros opcionais são interpretados como o tipo de opção F#, para que você `match` possa `Some` consultá-los da maneira regular que os tipos de opção são consultados, usando uma expressão com e `None`. Os parâmetros opcionais são permitidos apenas em `let` membros, não em funções criadas usando vinculações.

Você pode passar valores opcionais existentes para `?arg=None` o `?arg=Some(3)` `?arg=arg`método por nome de parâmetro, como ou ou . Isso pode ser útil ao construir um método que passe argumentos opcionais para outro método.

Você também pode `defaultArg`usar uma função , que define um valor padrão de um argumento opcional. A `defaultArg` função toma o parâmetro opcional como o primeiro argumento e o valor padrão como o segundo.

O exemplo a seguir ilustra o uso de parâmetros opcionais.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

A saída é a seguinte.

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

Para os fins de C# e Visual Basic `[<Optional; DefaultParameterValue<(...)>]` interop você pode usar os atributos em F#, para que os chamadores vejam um argumento como opcional. Isso equivale a definir o argumento como `MyMethod(int i = 3)`opcional em C# como em .

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

Você também pode especificar um novo objeto como um valor de parâmetro padrão. Por exemplo, `Foo` o membro `CancellationToken` poderia ter uma entrada opcional em vez disso:

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

O valor dado `DefaultParameterValue` como argumento deve corresponder ao tipo do parâmetro. Por exemplo, o seguinte não é permitido:

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

Neste caso, o compilador gera um aviso e ignorará ambos os atributos completamente. Observe que o `null` valor padrão precisa ser anotado por tipo, pois caso contrário, o compilador `[<Optional; DefaultParameterValue(null:obj)>] o:obj`infere o tipo errado, ou seja.

## <a name="passing-by-reference"></a>Passando por Referência

Passar um valor F# por referência envolve [byrefs](byrefs.md), que são tipos de ponteiro gerenciados. A orientação para qual tipo de uso é a seguinte:

- Use `inref<'T>` se você só precisa ler o ponteiro.
- Use `outref<'T>` se você só precisa escrever para o ponteiro.
- Use `byref<'T>` se você precisar ler e escrever para o ponteiro.

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

Como o parâmetro é um ponteiro e o valor é mutável, quaisquer alterações no valor são retidas após a execução da função.

Você pode usar uma tupla como `out` um valor de retorno para armazenar quaisquer parâmetros nos métodos de biblioteca .NET. Alternativamente, você pode `out` tratar o `byref` parâmetro como um parâmetro. O exemplo de código a seguir ilustra os dois sentidos.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Matrizes de parâmetros

Ocasionalmente, é necessário definir uma função que leva um número arbitrário de parâmetros do tipo heterogêneo. Não seria prático criar todos os métodos sobreponderados possíveis para explicar todos os tipos que poderiam ser usados. As implementações .NET fornecem suporte para esses métodos através do recurso de matriz de parâmetros. Um método que leva uma matriz de parâmetros em sua assinatura pode ser fornecido com um número arbitrário de parâmetros. Os parâmetros são colocados em uma matriz. O tipo de elementos da matriz determina os tipos de parâmetros que podem ser passados para a função. Se você definir a `System.Object` matriz de parâmetros com como o tipo de elemento, então o código do cliente pode passar valores de qualquer tipo.

Em F#, matrizes de parâmetros só podem ser definidas em métodos. Eles não podem ser usados em funções ou funções autônomas definidas em módulos.

Você define uma matriz de `ParamArray` parâmetros usando o atributo. O `ParamArray` atributo só pode ser aplicado ao último parâmetro.

O código a seguir ilustra tanto a chamada de um método .NET que leva uma matriz de parâmetros quanto a definição de um tipo em F# que tem um método que leva uma matriz de parâmetros.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Quando executado em um projeto, a saída do código anterior é a seguinte:

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>Confira também

- [Membros](./members/index.md)
