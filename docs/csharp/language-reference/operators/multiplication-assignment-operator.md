---
title: Operador *= – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 2038f3b55d46f3503496275b3d25b17663b8c1db
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333428"
---
# <a name="-operator-c-reference"></a>\*Operador = (Referência de C#)

O operador de atribuição de multiplicação binária.

## <a name="remarks"></a>Comentários

Uma expressão que usa o operador de atribuição `*=`, como

```csharp
x *= y
```

equivale a

```csharp
x = x * y
```

exceto que `x` é avaliado apenas uma vez. O [operador\*](multiplication-operator.md) é predefinido para que os tipos numéricos executem multiplicação.

O operador `*=` não pode ser sobrecarregado diretamente, mas os tipos definidos pelo usuário podem sobrecarregar o [operador \*](multiplication-operator.md) (confira [operator](../keywords/operator.md)).

## <a name="example"></a>Exemplo

[!code-csharp[csRefOperators#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#13)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
