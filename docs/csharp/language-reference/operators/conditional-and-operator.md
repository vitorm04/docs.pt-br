---
title: Operador &amp;&amp; – Referência de C#
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 82442f50275f21e0a0748951dc50628a8d7e11bb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243569"
---
# <a name="ampamp-operator-c-reference"></a>Operador &amp;&amp; (Referência de C#)

O operador AND lógico condicional `&&`, também conhecido como operador AND lógico de "curto-circuito", computa o AND lógico de seus operandos [bool](../keywords/bool.md). O resultado de `x && y` será `true` se ambos `x` e `y` forem avaliados como `true`. Caso contrário, o resultado será `false`. Se o primeiro operando for avaliado como `false`, o segundo operando não será avaliado e o resultado da operação será `false`. O exemplo a seguir demonstra esse comportamento:

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#And)]

O [operador AND lógico](and-operator.md) `&` também computa o AND lógico de seus `bool` operandos, mas sempre avalia os dois operandos.

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Um tipo definido pelo usuário não pode sobrecarregar o operador AND lógico condicional. No entanto, se um tipo definido pelo usuário sobrecarregar os operadores de [AND lógico](and-operator.md), [true e false](../keywords/true-false-operators.md) de uma determinada maneira, a operação `&&` poderá ser avaliada para os operandos desse tipo. Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](../language-specification/index.md).

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, veja a seção [Operadores lógicos condicionais](~/_csharplang/spec/expressions.md#conditional-logical-operators) na [especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Operador ||](conditional-or-operator.md)
- [Operador \!](logical-negation-operator.md)
- [Operador &](and-operator.md)
