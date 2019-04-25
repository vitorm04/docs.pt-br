---
title: Operador &amp; – Referência de C#
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 67d60709e1c6c76071ecfb7aac74c83dec6f372a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310038"
---
# <a name="amp-operator-c-reference"></a>Operador &amp; (Referência de C#)

Há suporte para o operador `&` de duas formas: um operador address-of unário ou um operador lógico binário.

## <a name="unary-address-of-operator"></a>Operador address-of unário

O operador `&` unário retorna o endereço de seu operando. Para obter mais informações, veja [Como obter o endereço de uma variável](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).

O operador address-of `&` requer contexto [não seguro](../keywords/unsafe.md).

## <a name="integer-logical-bitwise-and-operator"></a>Operador AND lógico bit a bit do inteiro

Para os tipos de inteiro, o operador `&` computa o AND lógico bit a bit de seus operandos:

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> O exemplo anterior usa os literais binários [introduzidos no C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) e [aprimorados no C#7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).

Como as operações em tipos de inteiro geralmente são permitidas em tipos de enumeração, o operador `&` também oferece suporte a operandos [enum](../keywords/enum.md).

## <a name="boolean-logical-and-operator"></a>Operador AND lógico booliano

Para operandos [bool](../keywords/bool.md), o operador `&` computa o AND lógico de seus operandos. O resultado de `x & y` será `true` se ambos `x` e `y` forem `true`. Caso contrário, o resultado será `false`.

O operador `&` avalia os dois operandos, mesmo se o primeiro operando for avaliado como `false`, de modo que o resultado deve ser `false`, independentemente do valor do segundo operando. O exemplo a seguir demonstra esse comportamento:

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

O [operador AND condicional](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` também computa o AND lógico e seus operandos, mas não avalia o segundo operando se o primeiro for avaliado como `false`.

Para operandos bool que permitem valor nulo, o comportamento do operador `&` é consistente com a lógica de três valores do SQL. Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](boolean-logical-operators.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Os tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `&` binário. Quando um operador `&` binário é sobrecarregado, o [operador de atribuição AND](and-assignment-operator.md) `&=` também é implicitamente sobrecarregado.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, veja as seções [O operador address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) e [Operadores lógicos](~/_csharplang/spec/expressions.md#logical-operators) da [Especificação de linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Operadores lógicos boolianos](boolean-logical-operators.md)
- [Tipos de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Operador |](or-operator.md)
- [Operador ^](xor-operator.md)
- [Operador ~](bitwise-complement-operator.md)
