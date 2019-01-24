---
title: Operador -= – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 3b6890be4460a599a5d2f5f5f6ee1627be933f0b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333324"
---
# <a name="--operator-c-reference"></a>Operador -= (referência do C#)

O operador de atribuição de subtração.

## <a name="remarks"></a>Comentários

Uma expressão que usa o operador de atribuição `-=`, como

```csharp
x -= y
```

 equivale a

```csharp
x = x - y
```

exceto que `x` é avaliado apenas uma vez. O significado do [operador –](subtraction-operator.md) depende dos tipos do `x` e `y` (subtração para operandos numéricos, remoção de delegado para operandos de delegado e assim por diante).

O operador `-=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [- operador](subtraction-operator.md) (consulte [operador](../keywords/operator.md)).

O operador -= também é usado em C# para cancelar a assinatura de um evento. Para obter mais informações, confira [Como: realizar e cancelar a assinatura de eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="example"></a>Exemplo

[!code-csharp[csRefOperators#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#6)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
