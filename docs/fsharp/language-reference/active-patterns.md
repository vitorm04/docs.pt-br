---
title: Padrões ativos (F#)
description: 'Saiba como usar padrões ativos para definir partições nomeadas subdividir os dados de entrada em F # linguagem de programação.'
ms.date: 05/16/2016
ms.openlocfilehash: b8c3270b1efbeb3495ac69bf1217fddf8a5a73e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564440"
---
# <a name="active-patterns"></a>Padrões ativos

*Padrões ativos* permitem definir partições nomeadas subdividir os dados de entrada, para que você pode usar esses nomes em um padrão de expressão de correspondência, exatamente como você faria para uma união discriminada. Você pode usar padrões ativos para decompor os dados de uma maneira personalizada para cada partição.


## <a name="syntax"></a>Sintaxe

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a>Comentários
Na sintaxe anterior, os identificadores são os nomes de partições de dados de entrada que são representados por *argumentos*, ou, em outras palavras, os nomes de subconjuntos do conjunto de todos os valores dos argumentos. Pode haver até sete partições em uma definição padrão ativo. O *expressão* descreve o formulário no qual decompor os dados. Você pode usar uma definição padrão ativo para definir as regras para determinar quais partições nomeadas os valores fornecidos como argumentos pertencem ao. A (| e |) símbolos são chamados de *clipes banana* e a função criada por este tipo de associação let é chamada uma *reorganizador ativo*.

Por exemplo, considere o seguinte padrão ativo com um argumento.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Você pode usar o padrão ativo em um padrão de correspondência de expressão, como no exemplo a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

A saída do programa é da seguinte maneira:

```
7 is odd
11 is odd
32 is even
```

Outro uso de padrões ativos é decompor os tipos de dados de várias maneiras, como quando os mesmos dados subjacentes tem diversas representações possíveis. Por exemplo, um `Color` objeto pode ser decomposto em uma representação de RGB ou uma representação HSB.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

A saída do programa acima é o seguinte:

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

Em combinação, essas duas maneiras de usar padrões ativos permitem a partição e decompõem dados em formato apropriado em executam os cálculos apropriados nos dados apropriados na forma mais conveniente para a computação.

As expressões de correspondência de padrão resultante permitem que os dados sejam gravados em um modo conveniente de ramificação potencialmente complexa muito legível, simplificando bastante e código de análise de dados.


## <a name="partial-active-patterns"></a>Padrões ativos parciais
Às vezes, você precisa apenas parte do espaço da entrada de partição. Nesse caso, você gravar um conjunto parcial padrões que correspondem a algumas entradas, mas não corresponde a outras entradas. Padrões ativos que não produzem um valor sempre são chamados *padrões ativos parciais*; eles têm um valor de retorno é um tipo de opção. Para definir um padrão ativo parcial, você pode usar um caractere curinga (_) ao final da lista de padrões dentro dos clipes banana. O código a seguir ilustra o uso de um padrão ativo parcial.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

A saída do exemplo anterior é da seguinte maneira:

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Ao usar padrões ativos parciais, às vezes, as opções individuais podem ser contíguos ou mutuamente exclusivos, mas não precisa ser. No exemplo a seguir, o quadrado padrão e o cubo padrão não são não contíguas, porque alguns números são quadrados e cubos, como 64. O programa a seguir imprime todos os números inteiros até 1000000 quadrados e cubos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

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
Padrões ativos sempre têm pelo menos um argumento para o item que está sendo correspondido, mas podem se tornar argumentos adicionais, caso em que o nome *com parâmetros padrão ativo* se aplica. Argumentos adicionais permitem que um padrão geral a ser especializado. Por exemplo, os padrões ativos que usam expressões regulares para analisar cadeias de caracteres geralmente incluem a expressão regular como um parâmetro adicional, como no código a seguir, que também usa o padrão ativo parcial `Integer` definida no exemplo de código anterior. Neste exemplo, cadeias de caracteres que usam expressões regulares para vários formatos de data são fornecidas para personalizar o padrão ativo ParseRegex geral. O padrão de ativo de inteiro é usado para converter as cadeias de caracteres correspondentes em números inteiros que podem ser passados para o construtor DateTime.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

A saída do código anterior é da seguinte maneira:

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Padrões ativos não são restritos apenas a expressões de correspondência de padrões, também pode usá-las em associações let.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

A saída do código anterior é da seguinte maneira:

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Expressões Match](match-expressions.md)

