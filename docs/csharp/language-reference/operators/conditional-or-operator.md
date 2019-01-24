---
title: Operador || – Referência de C#
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: 079c021eb68ece097c7f644416f1e9469a82dcea
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415423"
---
# <a name="-operator-c-reference"></a>Operador || (Referência de C#)

O operador OR lógico condicional `||`, também conhecido como operador OR lógico de "curto-circuito", computa o OR lógico de seus operandos [bool](../keywords/bool.md). O resultado de `x || y` será `true` se `x` ou `y` for avaliado como `true`. Caso contrário, o resultado será `false`. Se o primeiro operando for avaliado como `true`, o segundo operando não será avaliado e o resultado da operação será `true`. O exemplo a seguir demonstra esse comportamento:

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#Or)]

O [operador OR lógico](or-operator.md) `|` também computa o OR lógico de seus operandos `bool`, mas sempre avalia os dois operandos.

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Um tipo definido pelo usuário não pode sobrecarregar o operador OR lógico condicional. No entanto, se um tipo definido pelo usuário sobrecarregar os operadores de [OR lógico](or-operator.md), [true e false](../keywords/true-false-operators.md) de uma determinada maneira, a operação `||` poderá ser avaliada para os operandos desse tipo. Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](../language-specification/index.md).

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, veja a seção [Operadores lógicos condicionais](~/_csharplang/spec/expressions.md#conditional-logical-operators) na [especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Operador &&](conditional-and-operator.md)
- [Operador \!](logical-negation-operator.md)
- [Operador |](or-operator.md)
