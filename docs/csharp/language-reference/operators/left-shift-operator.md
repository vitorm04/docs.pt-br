---
title: Operador << – Referência de C#
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: deea2d0f720ba7f096e65c67378586bc88f24673
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219427"
---
# <a name="-operator-c-reference"></a>Operador \<\< (referência do C#)

O operador de deslocamento à esquerda `<<` desloca o primeiro operando à esquerda pelo número de bits definido pelo segundo operando. Todos os tipos de inteiros dão suporte ao operador `<<`. No entanto, o tipo do segundo operando deve ser [int](../keywords/int.md) ou um tipo que tem uma [conversão numérica implícita predefinida](../keywords/implicit-numeric-conversions-table.md) para `int`.

Os bits de ordem superior que estão fora do intervalo do tipo de resultado são descartados e as posições de bits vazios de ordem inferior são definidas como zero, como mostra o exemplo a seguir:

[!code-csharp-interactive[left shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShift)]

## <a name="shift-count"></a>Contagem de deslocamentos

Para a expressão `x << count`, a contagem real de deslocamento depende do tipo de `x` da seguinte maneira:

- Se o tipo de `x` for [int](../keywords/int.md) ou [uint](../keywords/uint.md), a contagem de deslocamentos será determinada pelos *cinco* bits de ordem inferior do segundo operando. Ou seja, a contagem de deslocamentos é calculada a partir de `count & 0x1F` (ou `count & 0b_1_1111`).

- Se o tipo de `x` for [long](../keywords/long.md) ou [ulong](../keywords/ulong.md), a contagem de deslocamentos será determinada pelos *seis* bits de ordem inferior do segundo operando. Ou seja, a contagem de deslocamentos é calculada a partir de `count & 0x3F` (ou `count & 0b_11_1111`).

O exemplo a seguir demonstra esse comportamento:

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftByLargeCount)]

## <a name="remarks"></a>Comentários

As operações de deslocamento nunca causam estouros e produzem os mesmos resultados nos contextos [marcados e desmarcados](../keywords/checked-and-unchecked.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `<<`. Se um tipo definido pelo usuário `T` sobrecarregar o operador `<<`, o tipo do primeiro operando deverá ser `T` e o tipo do segundo operando deverá ser `int`. Quando um operador `<<` é sobrecarregado, o [operador de atribuição de deslocamento para a esquerda](left-shift-assignment-operator.md) `<<=` também é implicitamente sobrecarregado.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Saiba mais na seção [Operadores de deslocamento](~/_csharplang/spec/expressions.md#shift-operators) na [Especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Operador >>](right-shift-operator.md)
