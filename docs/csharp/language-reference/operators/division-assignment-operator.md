---
title: Operador /= – Referência de C#
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: ed4dd6c0c944b77543aae4de8d51534b4df4f4ef
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286514"
---
# <a name="-operator-c-reference"></a>Operador /= (Referência de C#)

O operador de atribuição de divisão.

Uma expressão que usa o operador `/=`, como

```csharp
x /= y
```

equivale a

```csharp
x = x / y
```

exceto que `x` é avaliado apenas uma vez.

O [operador de divisão](division-operator.md) `/` divide o primeiro operando pelo segundo. Ele é compatível com todos os tipos numéricos.

O exemplo a seguir demonstra o uso do operador `/=`:

[!code-csharp-interactive[divide and assign](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#DivisionAssignment)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador de divisão](division-operator.md) `/`, o operador de atribuição de divisão`/=` ficará implicitamente sobrecarregado. Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador de atribuição de divisão.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, veja a seção [Atribuição composta](~/_csharplang/spec/expressions.md#compound-assignment) na [especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
