---
title: Operador <<= – Referência de C#
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: d2105fbee4ddfe1b2cb3325d82b0f2f8c5559297
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219434"
---
# <a name="-operator-c-reference"></a>Operador \<\<= (referência do C#)

O operador de atribuição de deslocamento para a esquerda.

Uma expressão que usa o operador `<<=`, como

```csharp
x <<= y
```

equivale a

```csharp
x = x << y
```

exceto que `x` é avaliado apenas uma vez.

O [operador `<<`](left-shift-operator.md) desloca o primeiro operando à esquerda pelo número de bits definido pelo seu segundo operando.

O exemplo a seguir demonstra o uso do operador `<<=`:

[!code-csharp-interactive[left shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftAssignment)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador `<<`](left-shift-operator.md), o operador de atribuição à esquerda `<<=` ficará implicitamente sobrecarregado. Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador de atribuição à esquerda.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, veja a seção [Atribuição composta](~/_csharplang/spec/expressions.md#compound-assignment) na [especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
