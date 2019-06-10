---
title: Operadores de comparação – referência em C#
description: Saiba mais sobre operadores de comparação em C# que você pode usar para verificar a ordem dos valores numéricos.
ms.date: 04/25/2019
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: 3b123ea1ae57735cdcb763087f12c30b8008dc11
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758205"
---
# <a name="comparison-operators-c-reference"></a>Operadores de comparação (referência em C#)

Os operadores de comparação [`<` (menor que)](#less-than-operator-), [`>` (maior que)](#greater-than-operator-), [`<=` (menor ou igual)](#less-than-or-equal-operator-) e [`>=` ( maior que ou igual)](#greater-than-or-equal-operator-), também conhecida como relacionais, comparam seus operandos. Esses operadores dão suporte a todos os tipos numéricos [integrais](../keywords/integral-types-table.md) e de [ponto flutuante](../keywords/floating-point-types-table.md).

> [!NOTE]
> Para os operadores `==`, `<`, `>`, `<=` e `>=`, se nenhum dos operandos for um número (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), o resultado da operação será `false`. Isso significa que o valor `NaN` não é superior, inferior nem igual a nenhum outro valor `double` (ou `float`), incluindo `NaN`. Para obter mais informações e exemplos, consulte o artigo de referência <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.

Tipos de enumeração também dão suporte a operadores de comparação. No caso dos operandos do mesmo tipo de [enum](../keywords/enum.md), os valores correspondentes do tipo integral subjacente são comparados.

Os operadores [`==` e `!=`](equality-operators.md) verificam se seus operandos são iguais ou não.

## <a name="less-than-operator-"></a>Operador menor que \<

O operador `<` retornará `true` se o primeiro operando for menor do que o segundo; caso contrário, `false`:

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>Operador maior que >

O operador `>` retornará `true` se o primeiro operando for maior do que o segundo; caso contrário, `false`:

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Operador menor ou igual \<=

O operador `<=` retornará `true` se o primeiro operando for menor ou igual ao segundo; caso contrário, `false`:

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Operador maior ou igual >=

O operador `>=` retornará `true` se o primeiro operando for maior ou igual ao segundo; caso contrário, `false`:

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Os tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) os operadores `<`, `>`, `<=` e `>=`.

Se um tipo sobrecarregar um dos operadores `<` ou `>`, ele deverá sobrecarregar tanto `<` quanto `>`. Se um tipo sobrecarregar um dos operadores `<=` ou `>=`, ele deverá sobrecarregar tanto `<=` quanto `>=`.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Operadores de igualdade](equality-operators.md)
