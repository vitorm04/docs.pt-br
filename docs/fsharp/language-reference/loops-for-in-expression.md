---
title: 'Loops: expressão for...in (F#)'
description: 'Veja como o F # loop for... na expressão de construção de loop é usado para iterar sobre a correspondência de um padrão de uma coleção enumerável.'
ms.date: 05/16/2016
ms.openlocfilehash: 926f0a9940021b3dc0deefc12ea158c35975e949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="loops-forin-expression"></a>Loops: expressão for...in

Esta construção de loop é usada para iterar sobre a correspondência de um padrão de uma coleção enumerável como uma expressão de intervalo, sequência, lista, matriz ou outra construção que oferece suporte à enumeração.


## <a name="syntax"></a>Sintaxe

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>Comentários
O `for...in` expressão pode ser comparada com o `for each` instrução em outras linguagens .NET porque ele é usado para executar um loop sobre os valores em uma coleção enumerável. No entanto, `for...in` também oferece suporte a padrões correspondentes na coleção em vez de apenas iteração pela coleção inteira.

A expressão enumerável pode ser especificada como uma coleção enumerável ou, usando o `..` operador, como um intervalo de um tipo integral. Coleções enumeráveis incluem listas, as sequências, matrizes, conjuntos, mapas e assim por diante. Qualquer tipo que implementa `System.Collections.IEnumerable` pode ser usado.

Quando você expressar um intervalo usando os `..` operador, você pode usar a sintaxe a seguir.

*Iniciar* ... *Concluir*

Você também pode usar uma versão que inclui um incremento chamado o *ignorar*, conforme mostrado no código a seguir.

*Iniciar* ... *Ignorar* ... *Concluir*

Quando você usa intervalos integrais e uma variável de contador simples como padrão, o comportamento típico é para incrementar a variável de contador em 1 em cada iteração, mas se o intervalo inclui um valor skip, o contador é incrementado pelo valor skip em vez disso.

Valores que correspondam ao padrão também podem ser usados na expressão de corpo.

Os exemplos de código a seguir ilustram o uso do `for...in` expressão.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

A saída é a seguinte.

```
1
5
100
450
788
```

O exemplo a seguir mostra como criar um loop em uma sequência e como usar um padrão de tupla em vez de uma variável simple.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

A saída é a seguinte.

```
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

O exemplo a seguir mostra como criar um loop em um intervalo de inteiros simples.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

A saída de function1 é da seguinte maneira.

```
1 2 3 4 5 6 7 8 9 10
```

O exemplo a seguir mostra como criar um loop em um intervalo com um salto de 2, que inclui todos os outros elementos do intervalo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

A saída de `function2` é da seguinte maneira.

```
1 3 5 7 9
```

O exemplo a seguir mostra como usar um intervalo de caracteres.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

A saída de `function3` é da seguinte maneira.

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

O exemplo a seguir mostra como usar um valor negativo skip para uma iteração inversa.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

A saída de `function4` é da seguinte maneira.

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

O início e fim do intervalo também podem ser expressões, como funções, como no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

A saída de `function5` com essa entrada é o seguinte.

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

O exemplo a seguir mostra o uso de um caractere curinga (_) quando o elemento não é necessária no loop.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

A saída é a seguinte.

```
Number of elements in list1: 5
```

`Note` Você pode usar `for...in` em expressões de sequência e outras expressões de cálculo, caso em que uma versão personalizada do `for...in` expressão é usada. Para obter mais informações, consulte [sequências](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md), e [expressões de computação](computation-expressions.md).


## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Loops: `for...to` expressão](loops-for-to-expression.md)

[Loops: `while...do` expressão](loops-while-do-expression.md)
