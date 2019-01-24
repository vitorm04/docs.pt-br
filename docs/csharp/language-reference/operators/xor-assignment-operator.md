---
title: Operador ^= – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: 12189d6469a9716d3b7ebcffef23423a75692d1a
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333545"
---
# <a name="-operator-c-reference"></a>Operador ^= (referência do C#)

O operador de atribuição OR exclusivo.

## <a name="remarks"></a>Comentários

Uma expressão da forma

```csharp
x ^= y
```

é avaliada como

```csharp
x = x ^ y
```

exceto que `x` é avaliado apenas uma vez. O [operador ^](xor-operator.md) realiza uma operação OR exclusiva bit a bit em operandos integrais e OR exclusiva lógica em operandos [bool](../keywords/bool.md).

O operador ^= não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador ^](xor-operator.md) (consulte [operador](../keywords/operator.md)).

## <a name="example"></a>Exemplo

[!code-csharp[csRefOperators#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#23)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)