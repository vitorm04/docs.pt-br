---
title: "Parâmetros e argumentos (F#)"
description: "Saiba mais sobre o suporte da linguagem F # para definir parâmetros e argumentos de passagem para funções, métodos e propriedades."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9b37a5c4-9263-4513-822a-fbb0d1004254
ms.openlocfilehash: 50f54bacd9ba7ec20a7151794734f93200df9f2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="parameters-and-arguments"></a>Parâmetros e argumentos

Este tópico descreve o suporte de idioma para definir parâmetros e argumentos de passagem para funções, métodos e propriedades. Ela inclui informações sobre como passar por referência e como definir e usar os métodos que podem levar a um número variável de argumentos.


## <a name="parameters-and-arguments"></a>Parâmetros e argumentos
O termo *parâmetro* é usado para descrever os nomes de valores que devem ser fornecidos. O termo *argumento* é usado para os valores fornecidos para cada parâmetro.

Parâmetros podem ser especificados na tupla ou um formulário na forma curried, ou em uma combinação dos dois. Você pode passar argumentos usando um nome de parâmetro explícito. Parâmetros de métodos podem ser especificados como opcionais e recebe um valor padrão.


## <a name="parameter-patterns"></a>Padrões de parâmetro
Em geral, os parâmetros fornecidos para funções e métodos são padrões separados por espaços. Isso significa que, a princípio, qualquer um dos padrões descritas em [correspondência expressões](match-expressions.md) pode ser usado em uma lista de parâmetro para uma função ou um membro.

Métodos geralmente usam o formato de tupla de argumentos de passagem. Gera um resultado mais claro da perspectiva de outras linguagens .NET porque a forma de tupla corresponde a maneira como os argumentos são passados em métodos do .NET.

O formulário na forma curried geralmente é usado com funções criadas usando `let` associações.

O pseudocódigo a seguir mostra exemplos de tupla e argumentos na forma curried.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Formulários combinados são possíveis quando alguns argumentos são em tuplas e outros não.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Outros padrões também podem ser usados em listas de parâmetros, mas se o padrão de parâmetro não corresponde a todas as entradas possíveis, pode haver uma correspondência incompleta em tempo de execução. A exceção `MatchFailureException` é gerado quando o valor de um argumento não coincide com os padrões especificados na lista de parâmetros. O compilador emite um aviso quando um padrão de parâmetro permite correspondências incompletas. Pelo menos um outro padrão é normalmente útil para listas de parâmetros e que é o padrão de curinga. Você pode usar o padrão de curinga em uma lista de parâmetros quando você deseja simplesmente ignorar quaisquer argumentos fornecidos. O código a seguir ilustra o uso do padrão de curinga em uma lista de argumentos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

O padrão de curinga pode ser útil sempre que você não precisa de argumentos passados, como o ponto de entrada principal para um programa, quando você não estiver interessado nos argumentos de linha de comando que normalmente são fornecidos como uma matriz de cadeia de caracteres, como no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Outros padrões que às vezes são usados nos argumentos são o `as` padrão e padrões de identificador associados uniões discriminadas e padrões ativos. Você pode usar o padrão de união discriminado único caso, da seguinte maneira.

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

Você pode usar o `as` padrão para armazenar um valor correspondente como um valor local, conforme é mostrado na seguinte linha de código.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Outro padrão que é usado ocasionalmente é uma função que deixa o último argumento sem nome, fornecendo, como o corpo da função, uma expressão lambda que executa uma correspondência de padrão imediatamente no argumento implícita. Um exemplo disso é a seguinte linha de código.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Esse código define uma função que usa uma lista genérica e retorna `true` se a lista estiver vazia, e `false` caso contrário. O uso dessas técnicas pode tornar o código mais difícil de ler.

Ocasionalmente, padrões que envolvem incompletas correspondências são úteis, por exemplo, se você souber que as listas em seu programa tem somente três elementos, você pode usar um padrão semelhante ao seguinte em uma lista de parâmetros.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

O uso de padrões de correspondência incompleta melhor é reservado para a rápida criação de protótipos e outros usos temporários. O compilador emite um aviso para esse tipo de código. Esses padrões não podem abranger o caso geral de todas as entradas de possíveis e, portanto, não são adequados para APIs de componente.

## <a name="named-arguments"></a>Argumentos nomeados
Argumentos de métodos que podem ser especificados por posição em uma lista de argumentos separados por vírgulas ou podem ser passados para um método explicitamente fornecendo o nome, seguido por um sinal de igual e o valor a ser passado. Se especificado, fornecendo o nome, eles podem aparecer em uma ordem diferente daquele usado na declaração.

Argumentos nomeados podem tornar o código mais legível e mais adaptável para determinados tipos de alterações na API, como uma reorganização de parâmetros de método.

Argumentos nomeados são permitidos apenas para métodos, não para `let`-associados a funções, valores de função ou expressões lambda.

O exemplo de código a seguir demonstra o uso de argumentos nomeados.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

Em uma chamada para um construtor de classe, você pode definir os valores das propriedades da classe usando uma sintaxe semelhante de argumentos nomeados. O exemplo a seguir mostra essa sintaxe.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Para obter mais informações, consulte [construtores (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>Parâmetros opcionais
Você pode especificar um parâmetro opcional para um método usando um ponto de interrogação na frente do nome de parâmetro. Parâmetros opcionais são interpretados como o tipo de opção F #, para que você possa consultá-los da maneira normal que tipos de opção são consultados, usando um `match` expressão com `Some` e `None`. Parâmetros opcionais são permitidos somente em membros, não em funções criados usando `let` associações.

Você também pode usar uma função `defaultArg`, que define um valor padrão de um argumento opcional. O `defaultArg` função usa o parâmetro opcional, como o primeiro argumento e o valor padrão como o segundo.

O exemplo a seguir ilustra o uso de parâmetros opcionais.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

A saída é a seguinte.

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a>Passagem por referência
F # suporta o `byref` palavra-chave, que especifica se um parâmetro é passado por referência. Isso significa que as alterações para o valor são mantidas após a execução da função. Os valores fornecidos para um `byref` parâmetro deve ser mutável. Como alternativa, você pode passar as células de referência do tipo apropriado.

Passagem por referência em linguagens .NET evoluído como uma maneira de retornar mais de um valor de uma função. Em F #, você pode retornar uma coleção de itens para essa finalidade, ou usar uma célula de referência mutável como um parâmetro. O `byref` parâmetro for fornecido principalmente para interoperabilidade com bibliotecas .NET.

Os exemplos a seguir ilustram o uso do `byref` palavra-chave. Observe que quando você usa uma célula de referência como um parâmetro, você deve criar uma célula de referência como um valor nomeado e usá-lo como o parâmetro, não basta adicionar o `ref` operador conforme mostrado na primeira chamada para `Increment` no código a seguir. Como criar uma célula de referência cria uma cópia do valor subjacente, a primeira chamada incrementa apenas um valor temporário.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

Você pode usar uma tupla como um valor de retorno para armazenar as `out` parâmetros em métodos de biblioteca do .NET. Como alternativa, você pode tratar o `out` parâmetro como um `byref` parâmetro. O exemplo de código a seguir ilustra duas formas.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Matrizes de parâmetros
Ocasionalmente, é necessário definir uma função que recebe um número arbitrário de parâmetros de tipo heterogêneo. Não ser prático criar todos os métodos sobrecarregados possíveis para a conta para todos os tipos que podem ser usados. As implementações de .NET oferecem suporte para esses métodos por meio do recurso de matriz de parâmetro. Um método que usa uma matriz de parâmetros na sua assinatura pode ser fornecido com um número arbitrário de parâmetros. Os parâmetros são colocados em uma matriz. O tipo dos elementos da matriz determina os tipos de parâmetro que podem ser passados para a função. Se você definir a matriz de parâmetros com `System.Object` como o tipo de elemento, em seguida, o código do cliente pode passar valores de qualquer tipo.

Em F #, matrizes de parâmetros só podem ser definidas em métodos. Eles não podem ser usados em autônomo ou funções que são definidas em módulos.

Você define uma matriz de parâmetros usando o `ParamArray` atributo. O `ParamArray` atributo só pode ser aplicado ao último parâmetro.

O código a seguir ilustra os dois chamando um método de .NET que usa uma matriz de parâmetros e a definição de um tipo em F # que tem um método que usa uma matriz de parâmetros.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Quando executado em um projeto, a saída do código anterior é da seguinte maneira:

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>Consulte também
[Membros](members/index.md)
