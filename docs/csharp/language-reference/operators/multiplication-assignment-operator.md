---
title: Operador *= – Referência de C#
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 70461f79e714e44354fe4137e5360769fa048d3e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967380"
---
# <a name="-operator-c-reference"></a>\*Operador = (Referência de C#)

O operador de atribuição de multiplicação.

Uma expressão que usa o operador `*=`, como

```csharp
x *= y
```

equivale a

```csharp
x = x * y
```

exceto que `x` é avaliado apenas uma vez.

Para tipos numéricos, o [\*operador ](multiplication-operator.md) calcula o produto dos operandos.

O exemplo a seguir demonstra o uso do operador `*=`:

[!code-csharp-interactive[multiply and assign](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#MultiplyAndAssign)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador de multiplicação](multiplication-operator.md) `*`, o operador de atribuição de multiplicação `*=` ficará implicitamente sobrecarregado. Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador de atribuição de multiplicação.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, veja a seção [Atribuição composta](~/_csharplang/spec/expressions.md#compound-assignment) na [especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
