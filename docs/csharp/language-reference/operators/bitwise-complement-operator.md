---
title: Operador ~ (Referência de C#)
ms.date: 11/05/2018
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 1bcb07c5639a098e3a8c566e92083ca0d48efb81
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153209"
---
# <a name="-operator-c-reference"></a>Operador ~ (Referência de C#)

O operador de complemento bit a bit `~` é um operador unário que produz um complemento bit a bit de seu operando por meio da inversão de cada bit. Todos os tipos de inteiros dão suporte ao operador `~`.

> [!NOTE]
> O símbolo `~` também é usado para declarar finalizadores. Para mais informações, consulte [Finalizadores](../../programming-guide/classes-and-structs/destructors.md).

O exemplo a seguir demonstra o uso do operador `~`:

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseComplementExamples.cs#Example)]

> [!NOTE]
> O exemplo anterior usa os literais binários [introduzidos no C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) e [aprimorados no C#7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `~`.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para saber mais, confira a seção [Operador condicional complementar bit a bit](~/_csharplang/spec/expressions.md#bitwise-complement-operator) na [Especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Finalizadores](../../programming-guide/classes-and-structs/destructors.md)
- [Operador &](and-operator.md)
- [Operador |](or-operator.md)
- [Operador ^](xor-operator.md)
