---
title: Parâmetros e argumentos (F#)
description: 'Saiba mais sobre o suporte de linguagem F # para definir parâmetros e passar argumentos para funções, métodos e propriedades.'
ms.date: 05/16/2016
ms.openlocfilehash: a1e2a70ca560bbb09d2cd10f47485cbe5c5e029d
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46288177"
---
# <a name="parameters-and-arguments"></a>Parâmetros e argumentos

Este tópico descreve o suporte de linguagem para definir parâmetros e passar argumentos para funções, métodos e propriedades. Ele inclui informações sobre como passar por referência e como definir e usar os métodos que podem aproveitar um número variável de argumentos.

## <a name="parameters-and-arguments"></a>Parâmetros e argumentos

O termo *parâmetro* é usado para descrever os nomes para os valores que devem ser fornecidos. O termo *argumento* é usado para os valores fornecidos para cada parâmetro.

Parâmetros podem ser especificados na tupla ou formulário na forma curried ou em alguma combinação dos dois. Você pode passar argumentos usando um nome de parâmetro explícito. Parâmetros de métodos podem ser especificados como opcionais e recebe um valor padrão.

## <a name="parameter-patterns"></a>Padrões de parâmetro

Parâmetros fornecidos para funções e métodos são, em geral, padrões, separados por espaços. Isso significa que, em princípio, qualquer um dos padrões descritos em [expressões de correspondência](match-expressions.md) pode ser usado em uma lista de parâmetros para uma função ou um membro.

Métodos geralmente usam o formulário de tupla de passagem de argumentos. Isso proporciona um resultado mais claro da perspectiva de outras linguagens .NET como o formulário de tupla corresponde a maneira como os argumentos são passados em métodos do .NET.

O formulário na forma curried geralmente é usado com funções criadas com `let` associações.

O pseudocódigo a seguir mostra exemplos de tupla e os argumentos na forma curried.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Formulários combinados são possíveis quando alguns argumentos estão na tuplas e outros não.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Outros padrões também podem ser usados em listas de parâmetros, mas se o padrão de parâmetro não corresponder a todas as entradas possíveis, pode haver uma correspondência incompleta em tempo de execução. A exceção `MatchFailureException` é gerado quando o valor de um argumento não coincide com os padrões especificados na lista de parâmetros. O compilador emite um aviso quando um padrão de parâmetro permite correspondências incompleta. Pelo menos um outro padrão que é geralmente útil para listas de parâmetros e que é o padrão de curinga. Você pode usar o padrão de curinga em uma lista de parâmetros quando você simplesmente deseja ignorar os argumentos que são fornecidos. O código a seguir ilustra o uso do padrão de curinga em uma lista de argumentos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

O padrão de curinga pode ser útil sempre que você não precisa argumentos passados, como o ponto de entrada principal para um programa, quando você não estiver interessado nos argumentos de linha de comando que normalmente são fornecidos como uma matriz de cadeia de caracteres, o código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Outros padrões que às vezes são usados nos argumentos são o `as` padrão e padrões de identificador associadas com as uniões discriminadas e padrões ativos. Você pode usar o padrão de união discriminado caso único da seguinte maneira.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

A saída é a seguinte.

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Padrões ativos podem ser útil como parâmetros, por exemplo, ao transformar um argumento em um formato desejado, como no exemplo a seguir:

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

Você pode usar o `as` padrão para armazenar um valor correspondente como um valor local, conforme mostrado na seguinte linha de código.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Outro padrão que é usado ocasionalmente é uma função que deixa o último argumento sem nome, fornecendo, como o corpo da função, uma expressão lambda que executa imediatamente uma correspondência de padrões no argumento implícito. Um exemplo disso é a seguinte linha de código.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Esse código define uma função que usa uma lista genérica e retorna `true` se a lista estiver vazia, e `false` caso contrário. O uso dessas técnicas pode tornar o código mais difícil de ler.

Ocasionalmente, padrões que envolvem incompletas correspondências são úteis, por exemplo, se você souber que as listas em seu programa tem apenas três elementos, você pode usar um padrão semelhante ao seguinte em uma lista de parâmetros.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

O uso de padrões que têm uma correspondência incompleta melhor é reservado para prototipagem rápida e outros usos temporários. O compilador emitirá um aviso para esse tipo de código. Esses padrões não podem abranger o caso geral de todas as entradas possíveis e, portanto, não são adequados para as APIs do componente.

## <a name="named-arguments"></a>Argumentos nomeados

Argumentos para métodos que podem ser especificados por posição em uma lista de argumentos separados por vírgulas, ou eles poderão ser passados para um método explicitamente fornecendo o nome, seguido por um sinal de igual e o valor a ser passado em. Se especificado, fornecendo o nome, eles podem aparecer em uma ordem diferente daquele usado na declaração.

Argumentos nomeados podem tornar código mais legível e mais adaptável a determinados tipos de alterações na API, como um reordenação de parâmetros de método.

Argumentos nomeados são permitidos apenas para métodos, não para `let`-associados a funções, valores de função ou expressões lambda.

O exemplo de código a seguir demonstra o uso de argumentos nomeados.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

Em uma chamada para um construtor de classe, você pode definir os valores das propriedades da classe usando uma sintaxe semelhante de argumentos nomeados. O exemplo a seguir mostra essa sintaxe.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Para obter mais informações, consulte [construtores (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>Parâmetros opcionais

Você pode especificar um parâmetro opcional para um método por meio de um ponto de interrogação na frente do nome do parâmetro. Parâmetros opcionais são interpretados como o tipo de opção F #, portanto, você pode consultá-los da maneira normal, tipos de opção são consultados, usando um `match` expressão com `Some` e `None`. Parâmetros opcionais são permitidos apenas em membros, não em funções criadas com `let` associações.

Você também pode usar uma função `defaultArg`, que define um valor padrão de um argumento opcional. O `defaultArg` função usa o parâmetro opcional como o primeiro argumento e o valor padrão como o segundo.

O exemplo a seguir ilustra o uso de parâmetros opcionais.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

A saída é a seguinte.

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a>Passagem por referência

Um valor de F # a passagem por referência envolve [byrefs](byrefs.md), que são tipos de ponteiro gerenciado. Diretrizes para qual tipo usar é o seguinte:

* Use `inref<'T>` se você precisar ler o ponteiro.
* Use `outref<'T>` se você só precisa escrever para o ponteiro.
* Use `byref<'T>` se você precisar de ler e gravar para o ponteiro.

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

// No need to make it mutable, since it's read-only
let x = 1
example1 &x

// Needs to be mutable, since we write to it
let mutable y = 2
example2 &y
example3 &y // Now 'y' is 3
```

Como o parâmetro é um ponteiro e o valor é mutável, quaisquer alterações no valor são mantidas após a execução da função.

Você pode usar uma tupla como um valor de retorno para armazenar as `out` parâmetros em métodos de biblioteca do .NET. Como alternativa, você pode tratar a `out` parâmetro como um `byref` parâmetro. O exemplo de código a seguir ilustra as duas maneiras.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Matrizes de parâmetros

Ocasionalmente, é necessário definir uma função que usa um número arbitrário de parâmetros de tipo heterogêneo. Não seria prático criar todos os métodos sobrecarregados possíveis para levar em conta todos os tipos que podem ser usados. As implementações do .NET oferecem suporte para esses métodos por meio do recurso de matriz de parâmetro. Um método que usa uma matriz de parâmetros na sua assinatura pode ser fornecido com um número arbitrário de parâmetros. Os parâmetros são colocados em uma matriz. O tipo dos elementos da matriz determina os tipos de parâmetro que podem ser passados para a função. Se você definir a matriz de parâmetros com `System.Object` como o tipo de elemento, em seguida, código do cliente pode passar valores de qualquer tipo.

No F #, matrizes de parâmetros só podem ser definidas nos métodos. Eles não podem ser usados em funções autônomas ou funções que são definidas em módulos.

Você define uma matriz de parâmetros usando o `ParamArray` atributo. O `ParamArray` atributo só pode ser aplicado ao último parâmetro.

O código a seguir ilustra as duas chamando um método do .NET que usa uma matriz de parâmetros e a definição de um tipo em F # que tem um método que usa uma matriz de parâmetros.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Quando executado em um projeto, a saída do código anterior é da seguinte maneira:

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>Consulte também

- [Membros](members/index.md)
