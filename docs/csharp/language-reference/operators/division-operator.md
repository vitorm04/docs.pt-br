---
title: Operador / – Referência de C#
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: 45bcd64b60e7d13f389064faefeda815ea1f32c9
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286527"
---
# <a name="-operator-c-reference"></a>Operador / (Referência de C#)

O operador de divisão `/` divide o primeiro operando pelo segundo. Todos os tipos numéricos são compatíveis com o operador de divisão.

## <a name="integer-division"></a>Divisão de inteiros

Para os operandos de tipos inteiros, o resultado do operador `/` é de um tipo inteiro e igual ao quociente dos dois operandos arredondados para zero:

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#Integer)]

Para obter o quociente dos dois operandos como um número de ponto flutuante, use o tipo `float`, `double` ou `decimal`:

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#IntegerAsFloatingPoint)]

## <a name="floating-point-division"></a>Divisão de ponto flutuante

Para os tipos `float`, `double` e `decimal`, o resultado do operador `/` é o quociente dos dois operandos:

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#FloatingPoint)]

Se um dos operandos é `decimal`, outro operando não pode ser `float` nem `double`, porque nem `float` ou `double` é implicitamente conversível para `decimal`. Você deve converter explicitamente o operando `float` ou `double` para o tipo `decimal`. Para saber mais sobre as conversões implícitas entre tipos numéricos, confira a [Tabela de conversões numéricas implícitas](../keywords/implicit-numeric-conversions-table.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `/`. Quando um operador `/` é sobrecarregado, o [operador de atribuição de divisão](division-assignment-operator.md) `/=` também é implicitamente sobrecarregado.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para saber mais, confira a seção [Operador de divisão](~/_csharplang/spec/expressions.md#division-operator) na [especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Operador %](remainder-operator.md)
