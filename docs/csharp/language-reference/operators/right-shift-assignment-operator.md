---
title: '>>Operador = – Referência de C#'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 51914bb5e9ebffd5d868528b5a8d3072a956cea6
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220907"
---
# <a name="-operator-c-reference"></a>Operador >>= (Referência de C#)

O operador de atribuição de deslocamento para a direita.

Uma expressão que usa o operador `>>=`, como

```csharp
x >>= y
```

equivale a

```csharp
x = x >> y
```

exceto que `x` é avaliado apenas uma vez.

O [operador `>>`](right-shift-operator.md) desloca o primeiro operando à direita pelo número de bits definido pelo seu segundo operando.

O exemplo a seguir demonstra o uso do operador `>>=`:

[!code-csharp-interactive[right shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftAssignment)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador `>>`](right-shift-operator.md), o operador de atribuição à direita `>>=` ficará implicitamente sobrecarregado. Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador de atribuição à direita.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, veja a seção [Atribuição composta](~/_csharplang/spec/expressions.md#compound-assignment) na [especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)