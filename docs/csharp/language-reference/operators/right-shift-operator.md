---
title: '>> Operador - referência do C#'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 809cd2cab29d3378892ea224cf846e9d0909b073
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219718"
---
# <a name="-operator-c-reference"></a>Operador >> (Referência de C#)

O operador de deslocamento para a direita `>>` desloca o primeiro operando à direita pelo número de bits definido pelo seu segundo operando. Todos os tipos de inteiros dão suporte ao operador `>>`. No entanto, o tipo do segundo operando deve ser [int](../keywords/int.md) ou um tipo que tem uma [conversão numérica implícita predefinida](../keywords/implicit-numeric-conversions-table.md) para `int`.

A operação de deslocamento à direita descarta os bits de ordem inferior. As posições vazias de bit de ordem superior são definidas com base no tipo do primeiro operando da seguinte maneira:

- Se o primeiro operando for do tipo [int](../keywords/int.md) ou [long](../keywords/long.md), o operador de deslocamento à direita executará um deslocamento **aritmético**: o valor do bit mais significativo (o bit de sinal) do primeiro operando é propagado para as posições vazias de bits de ordem superior. Ou seja, as posições vazias de bit de ordem superior são definidas como zero se o primeiro operando for positivo e definidas como um se ele for negativo.

- Se o primeiro operando for do tipo [uint](../keywords/uint.md) ou [ulong](../keywords/ulong.md), o operador de deslocamento à direita executará um deslocamento **lógico**: as posições vazias de bit de ordem superior são sempre definidas como zero.

O exemplo a seguir demonstra esse comportamento:

[!code-csharp-interactive[right shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShift)]

## <a name="shift-count"></a>Contagem de deslocamentos

Para a expressão `x >> count`, a contagem real de deslocamento depende do tipo de `x` da seguinte maneira:

- Se o tipo de `x` for [int](../keywords/int.md) ou [uint](../keywords/uint.md), a contagem de deslocamentos será determinada pelos *cinco* bits de ordem inferior do segundo operando. Ou seja, a contagem de deslocamentos é calculada a partir de `count & 0x1F` (ou `count & 0b_1_1111`).

- Se o tipo de `x` for [long](../keywords/long.md) ou [ulong](../keywords/ulong.md), a contagem de deslocamentos será determinada pelos *seis* bits de ordem inferior do segundo operando. Ou seja, a contagem de deslocamentos é calculada a partir de `count & 0x3F` (ou `count & 0b_11_1111`).

O exemplo a seguir demonstra esse comportamento:

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftByLargeCount)]

## <a name="remarks"></a>Comentários

As operações de deslocamento nunca causam estouros e produzem os mesmos resultados nos contextos [marcados e desmarcados](../keywords/checked-and-unchecked.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `>>`. Se um tipo definido pelo usuário `T` sobrecarregar o operador `>>`, o tipo do primeiro operando deverá ser `T` e o tipo do segundo operando deverá ser `int`. Quando um operador `>>` é sobrecarregado, o [operador de atribuição de deslocamento à direita](right-shift-assignment-operator.md) `>>=` também é implicitamente sobrecarregado.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Saiba mais na seção [Operadores de deslocamento](~/_csharplang/spec/expressions.md#shift-operators) na [Especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Operador <<](left-shift-operator.md)