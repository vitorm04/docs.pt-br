---
title: Padrões ativos (F#)
description: 'Saiba como usar padrões ativos para definir partições nomeadas que subdividem os dados de entrada a linguagem de programação F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 4fb7d3e2b9c7e6f1c1ed9d64a47728c7f40017c8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881870"
---
# <a name="active-patterns"></a>Padrões ativos

*Padrões ativos* permitem definir partições nomeadas que subdividem os dados de entrada, para que você possa usar esses nomes em um padrão de expressão de correspondência de exatamente como você faria para uma união discriminada. Você pode usar padrões ativos para decompor os dados de uma maneira personalizada para cada partição.

## <a name="syntax"></a>Sintaxe

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, os identificadores são os nomes de partições de dados de entrada que são representados pela *argumentos*, ou, em outras palavras, os nomes de subconjuntos do conjunto de todos os valores dos argumentos. Pode haver até sete partições em uma definição de padrão ativo. O *expressão* descreve o formulário no qual a decompor os dados. Você pode usar uma definição de padrão ativo para definir as regras para determinar quais partições nomeadas valores fornecidos como argumentos pertencem a. O (| e |) símbolos são denominados *pipe* e é chamada de função criado por este tipo de associação let um *reconhecedor active*.

Por exemplo, considere o seguinte padrão de Active Directory com um argumento.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Você pode usar o Active Directory padrão em um padrão de correspondência de expressão, como no exemplo a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

A saída desse programa é da seguinte maneira:

```
7 is odd
11 is odd
32 is even
```

Outro uso dos padrões ativos é decompor os tipos de dados de várias maneiras, como quando os mesmos dados subjacentes tem diversas representações possíveis. Por exemplo, um `Color` objeto pode ser decomposto em uma representação de RGB ou uma representação HSB.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

A saída do programa acima é da seguinte maneira:

```
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

Em combinação, essas duas maneiras de usar padrões ativos permitem a partição e decompõem os dados em um formulário apropriado em executam os cálculos apropriados nos dados apropriados na forma mais conveniente para a computação.

As expressões de correspondência de padrão resultante habilitar dados a serem gravados em uma maneira conveniente de ramificação potencialmente complexo muito legível, simplificando consideravelmente e o código de análise de dados.

## <a name="partial-active-patterns"></a>Padrões ativos parciais

Às vezes, você precisa apenas parte do espaço de entrada de partição. Nesse caso, você escrever um conjunto de parciais padrões que corresponder algumas entradas, mas não corresponde a outras entradas. Padrões ativos que não produzem um valor sempre são chamados *parciais padrões ativos*; eles têm um valor de retorno é um tipo de opção. Para definir um padrão ativo parcial, você pode usar um caractere curinga (\_) no final da lista de padrões de dentro do pipe. O código a seguir ilustra o uso de um padrão ativo parcial.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

A saída do exemplo anterior é da seguinte maneira:

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Ao usar padrões ativos parciais, às vezes, as opções individuais podem ser contíguos ou mutuamente exclusivos, mas eles não precisam ser. No exemplo a seguir, o quadrado do padrão e o padrão de cubo não são não contíguos, porque alguns números são quadrados e cubos, como 64. O programa a seguir imprime todos os inteiros até 1000000 quadrados e cubos.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

A saída é a seguinte:

```
1
64
729
4096
15625
46656
117649
262144
531441
1000000
```

## <a name="parameterized-active-patterns"></a>Padrões ativos com parâmetros

Padrões ativos sempre têm pelo menos um argumento para o item que está sendo correspondido, mas eles podem levar argumentos adicionais, bem, nesse caso, o nome *com parâmetros padrão ativo* se aplica. Argumentos adicionais permitem que um padrão geral ser especializados. Por exemplo, os padrões ativos que usam expressões regulares para analisar cadeias de caracteres geralmente incluem a expressão regular como um parâmetro extra, como no código a seguir, que também usa o padrão ativo parcial `Integer` definido no exemplo de código anterior. Neste exemplo, cadeias de caracteres que usam expressões regulares para vários formatos de data são fornecidas para personalizar o padrão do Active Directory de ParseRegex geral. O padrão do Active Directory de inteiro é usado para converter as cadeias de caracteres correspondentes em números inteiros que podem ser passados ao construtor DateTime.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

A saída do código anterior é da seguinte maneira:

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Padrões ativos não são restritos apenas a expressões de correspondência padrão, você também pode usá-los em associações permitem.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

A saída do código anterior é da seguinte maneira:

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Expressões Match](match-expressions.md)
