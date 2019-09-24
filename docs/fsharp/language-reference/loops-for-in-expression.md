---
title: 'Loops: expressão for...in'
description: Veja como o F# para... no constructo de loop de expressão é usado para iterar sobre as correspondências de um padrão em uma coleção enumerável.
ms.date: 05/16/2016
ms.openlocfilehash: 5a2ca59ca4199ece5d78010ff780e86ae2b25181
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216452"
---
# <a name="loops-forin-expression"></a>Loops: expressão for...in

Esse constructo de loop é usado para iterar sobre as correspondências de um padrão em uma coleção enumerável, como uma expressão de intervalo, sequência, lista, matriz ou outro constructo que dá suporte à enumeração.

## <a name="syntax"></a>Sintaxe

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>Comentários

A `for...in` expressão pode ser `for each` comparada à instrução em outras linguagens .net porque é usada para executar um loop sobre os valores em uma coleção enumerável. No entanto, `for...in` o também dá suporte à correspondência de padrões na coleção, em vez de apenas iteração em toda a coleção.

A expressão enumerável pode ser especificada como uma coleção enumerável ou, usando `..` o operador, como um intervalo em um tipo integral. As coleções enumeráveis incluem listas, sequências, matrizes, conjuntos, mapas e assim por diante. Qualquer tipo que implemente `System.Collections.IEnumerable` possa ser usado.

Ao expressar um intervalo usando o `..` operador, você pode usar a sintaxe a seguir.

*Iniciar* .. *finish*

Você também pode usar uma versão que inclui um incremento chamado *Skip*, como no código a seguir.

*Iniciar* .. *ignorar* .. *finish*

Quando você usa intervalos integrais e uma variável de contador simples como um padrão, o comportamento típico é incrementar a variável de contador em 1 em cada iteração, mas se o intervalo incluir um valor de ignorar, o contador será incrementado pelo valor de salto em vez disso.

Os valores correspondidos no padrão também podem ser usados na expressão Body.

Os exemplos de código a seguir ilustram o `for...in` uso da expressão.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

A saída é a seguinte.

```console
1
5
100
450
788
```

O exemplo a seguir mostra como executar um loop em uma sequência e como usar um padrão de tupla em vez de uma variável simples.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

A saída é a seguinte.

```console
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

O exemplo a seguir mostra como executar um loop em um intervalo de inteiros simples.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

A saída de function1 é a seguinte:

```console
1 2 3 4 5 6 7 8 9 10
```

O exemplo a seguir mostra como executar um loop em um intervalo com um Skip de 2, que inclui todos os outros elementos do intervalo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

A saída de `function2` é a seguinte:

```console
1 3 5 7 9
```

O exemplo a seguir mostra como usar um intervalo de caracteres.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

A saída de `function3` é a seguinte:

```console
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

O exemplo a seguir mostra como usar um valor de omissão negativo para uma iteração inversa.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

A saída de `function4` é a seguinte:

```console
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

O início e o final do intervalo também podem ser expressões, como funções, como no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

A saída de `function5` com essa entrada é a seguinte.

```console
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

O exemplo a seguir mostra o uso de um caractere curinga\_() quando o elemento não é necessário no loop.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

A saída é a seguinte.

```console
Number of elements in list1: 5
```

`Note`Você pode usar `for...in` em expressões de sequência e outras expressões de computação, caso em que uma versão personalizada `for...in` da expressão é usada. Para obter mais informações, consulte [Sequências](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md)e [expressões de computação](computation-expressions.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Loops `for...to`Expressão](loops-for-to-expression.md)
- [Loops `while...do`Expressão](loops-while-do-expression.md)
