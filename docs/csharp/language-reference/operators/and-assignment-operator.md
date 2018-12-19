---
title: '&amp;Operador = – Referência de C#'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: 223d2f30ee77457e1f9d5304ec299517932499d0
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237019"
---
# <a name="amp-operator-c-reference"></a>&amp;Operador = (Referência de C#)

O operador de atribuição AND.

Uma expressão que usa o operador `&=`, como

```csharp
x &= y
```

equivale a

```csharp
x = x & y
```

exceto que `x` é avaliado apenas uma vez.

Para operandos inteiros, o [operador `&`](and-operator.md) computa o AND lógico bit a bit de seus operandos. Para operandos [bool](../keywords/bool.md), ele computa o AND lógico de seus operandos.

O exemplo a seguir demonstra o uso do operador `&=`:

[!code-csharp-interactive[AND assignment example](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#AndAssignmentExample)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador `&`](and-operator.md), o operador de atribuição AND `&=` ficará implicitamente sobrecarregado. Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador de atribuição AND.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, veja a seção [Atribuição composta](~/_csharplang/spec/expressions.md#compound-assignment) na [especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
