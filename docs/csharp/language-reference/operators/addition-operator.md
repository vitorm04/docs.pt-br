---
title: + Operador – Referência de C#
ms.custom: seodec18
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 0f04ba837f9c03107acd0b2174cbd07c14a8c213
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504464"
---
# <a name="-operator-c-reference"></a>Operador + (Referência de C#)

Há suporte para o operador `+` de duas formas: unário mais operador ou um operador de adição binário.

## <a name="unary-plus-operator"></a>Operador unário de adição

O operador unário `+` retorna o valor do operando. Compatível com todos os tipos numéricos.

## <a name="numeric-addition"></a>Adição numérica

Para tipos numéricos, o operador `+` calcula a soma dos operandos:

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

Para obter mais informações sobre operadores aritméticos, confira [Operadores aritméticos](arithmetic-operators.md).

## <a name="string-concatenation"></a>Concatenação de cadeia de caracteres

Quando um ou os dois operandos forem do tipo [cadeia de caracteres](../keywords/string.md), o operador `+` concatenará as representações de cadeia de caracteres de seus operandos:

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

Começando com C# 6, [interpolação de cadeia de caracteres](../tokens/interpolated.md) oferece uma maneira mais conveniente de formatar cadeias de caracteres:

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Combinação de delegados

Para tipos [delegados](../keywords/delegate.md), o operador `+` retorna uma nova instância de delegado que, quando invocada, invoca o primeiro operando e, em seguida, invoca o segundo operando. Se qualquer um dos operandos for `null`, o operador `+` retornará o valor de outro operando (que também pode ser `null`). O exemplo a seguir mostra como os delegados podem ser combinados com o operador `+`:

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

Para obter mais informações sobre tipos de delegado, veja [Delegados](../../programming-guide/delegates/index.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) os operadores `+` unários e binários. Quando um operador `+` binário é sobrecarregado, o [operador de atribuição de adição](addition-assignment-operator.md) `+=` também é implicitamente sobrecarregado.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, veja as seções [Operador de adição unário](~/_csharplang/spec/expressions.md#unary-plus-operator) e [Operador de adição](~/_csharplang/spec/expressions.md#addition-operator) da [Especificação de linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Interpolação de cadeia de caracteres](../tokens/interpolated.md)
- [Como: concatenar várias cadeias de caracteres](../../how-to/concatenate-multiple-strings.md)
- [Delegados](../../programming-guide/delegates/index.md)
- [Checked e unchecked](../keywords/checked-and-unchecked.md)
