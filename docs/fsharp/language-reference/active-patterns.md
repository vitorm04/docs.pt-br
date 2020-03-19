---
title: Padrões ativos
description: Aprenda a usar padrões ativos para definir partições nomeadas que subdividem dados de entrada na linguagem de programação F#.
ms.date: 05/16/2016
ms.openlocfilehash: 898ef201369683bfd49d53e863e86f919f5837fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187068"
---
# <a name="active-patterns"></a>Padrões ativos

*Padrões ativos* permitem definir partições nomeadas que subdividem dados de entrada, para que você possa usar esses nomes em uma expressão de correspondência de padrões, assim como você faria para uma união discriminada. Você pode usar padrões ativos para decompor os dados de uma maneira personalizada para cada partição.

## <a name="syntax"></a>Sintaxe

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, os identificadores são nomes para partições dos dados de entrada que são representados por argumentos , ou, em *outras*palavras, nomes para subconjuntos do conjunto de todos os valores dos argumentos. Pode haver até sete partições em uma definição de padrão ativo. A *expressão* descreve a forma em que decompor os dados. Você pode usar uma definição de padrão ativo para definir as regras para determinar quais das partições nomeadas os valores dados como argumentos pertencem. Os símbolos (| e |) são chamados de *clipes* de banana e a função criada por esse tipo de vinculação de let é chamada de *reconhecedor ativo.*

Como exemplo, considere o seguinte padrão ativo com um argumento.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Você pode usar o padrão ativo em uma expressão de correspondência de padrão, como no exemplo a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

A saída deste programa é a seguinte:

```console
7 is odd
11 is odd
32 is even
```

Outro uso de padrões ativos é decompor tipos de dados de várias maneiras, como quando os mesmos dados subjacentes têm várias representações possíveis. Por exemplo, `Color` um objeto pode ser decomposto em uma representação RGB ou uma representação HSB.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

A saída do programa acima é a seguinte:

```console
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

Em combinação, essas duas maneiras de usar padrões ativos permitem que você particione e decomponha dados na forma apropriada e realize os cálculos apropriados sobre os dados apropriados na forma mais conveniente para a computação.

As expressões de correspondência de padrões resultantes permitem que os dados sejam escritos de forma conveniente, simplificando consideravelmente o código de ramificação e análise de dados potencialmente complexos.

## <a name="partial-active-patterns"></a>Padrões ativos parciais

Às vezes, você precisa particionar apenas parte do espaço de entrada. Nesse caso, você escreve um conjunto de padrões parciais que correspondem a algumas entradas, mas não correspondem a outras entradas. Padrões ativos que nem sempre produzem um valor são chamados *de padrões ativos parciais;* eles têm um valor de retorno que é um tipo de opção. Para definir um padrão ativo parcial, você\_usa um caractere curinga ( ) no final da lista de padrões dentro dos clipes de banana. O código a seguir ilustra o uso de um padrão ativo parcial.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

A saída do exemplo anterior é a seguinte:

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Ao usar padrões ativos parciais, às vezes as escolhas individuais podem ser desarticuladas ou mutuamente exclusivas, mas não precisam ser. No exemplo a seguir, o padrão Quadrado e o padrão Cubo não são desarticulados, pois alguns números são quadrados e cubos, como 64. O programa a seguir usa o padrão E para combinar os padrões Quadrado e Cubo. Ele imprime todos os inteiros até 1000 que são quadrados e cubos, bem como aqueles que são apenas cubos.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

A saída é da seguinte maneira:

```console
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a>Padrões ativos parametrizados

Padrões ativos sempre levam pelo menos um argumento para que o item seja correspondido, mas eles podem ter argumentos adicionais também, nesse caso o *padrão ativo parametrizado* do nome se aplica. Argumentos adicionais permitem que um padrão geral seja especializado. Por exemplo, padrões ativos que usam expressões regulares para analisar as cordas geralmente incluem a expressão regular como `Integer` um parâmetro extra, como no código a seguir, que também usa o padrão ativo parcial definido no exemplo de código anterior. Neste exemplo, as strings que usam expressões regulares para vários formatos de data são dadas para personalizar o padrão ativo geral Do ParseRegex. O padrão ativo Integer é usado para converter as strings combinadas em inteiros que podem ser passados para o construtor DateTime.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

A saída do código anterior é a seguinte:

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Os padrões ativos não estão restritos apenas às expressões de correspondência de padrões, você também pode usá-los em let-bindings.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

A saída do código anterior é a seguinte:

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Confira também

- [Referência de idioma F#](index.md)
- [Expressões de correspondência](match-expressions.md)
