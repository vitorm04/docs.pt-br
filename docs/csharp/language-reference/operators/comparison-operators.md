---
title: Operadores de comparação – referência do C#
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
ms.openlocfilehash: 68502205193a1fc8ab7410053e13274560ffffb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399241"
---
# <a name="comparison-operators-c-reference"></a>Operadores de comparação (referência do C#)

A [ `<` ](#less-than-operator-)comparação (menor [ `>` que) (maior que)](#greater-than-operator-) [ `<=` (menor ou igual)](#less-than-or-equal-operator-)e [ `>=` (maior ou igual),](#greater-than-or-equal-operator-) também conhecida como relacional, os operadores comparam seus operands. Esses operadores são suportados por todos os tipos numéricos [integrais](../builtin-types/integral-numeric-types.md) e [de ponto flutuante.](../builtin-types/floating-point-numeric-types.md)

> [!NOTE]
> Para os operadores `==`, `<`, `>`, `<=` e `>=`, se nenhum dos operandos for um número (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), o resultado da operação será `false`. Isso significa que o valor `NaN` não é superior, inferior nem igual a nenhum outro valor `double` (ou `float`), incluindo `NaN`. Para obter mais informações e exemplos, consulte o artigo de referência <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.

Tipos de enumeração também dão suporte a operadores de comparação. No caso dos operandos do mesmo tipo de [enum](../builtin-types/enum.md), os valores correspondentes do tipo integral subjacente são comparados.

Os [ `==` `!=` operadores e operadores](equality-operators.md) verificam se seus operands são iguais ou não.

## <a name="less-than-operator-"></a>Operador menor que \<

O operador `<` retornará `true` se o operando à esquerda for menor do que o operando à direita, caso contrário, `false`:

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>Operador maior que >

O operador `>` retornará `true` se o operando à esquerda for maior do que o operando à direita, caso contrário, `false`:

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Operador menor ou igual \<=

O operador `<=` retornará `true` se o operando à esquerda for menor ou igual ao operando à direita, caso contrário, `false`:

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Operador maior ou igual >=

O operador `>=` retornará `true` se o operando à esquerda for maior ou igual ao operando à direita, caso contrário, `false`:

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Um tipo definido pelo usuário `>` `<=`pode `>=` [sobrecarregar](operator-overloading.md) os `<`operadores e operadores.

Se um tipo sobrecarregar um dos operadores `<` ou `>`, ele deverá sobrecarregar tanto `<` quanto `>`. Se um tipo sobrecarregar um dos operadores `<=` ou `>=`, ele deverá sobrecarregar tanto `<=` quanto `>=`.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Operadores do C#](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Operadores de igualdade](equality-operators.md)
