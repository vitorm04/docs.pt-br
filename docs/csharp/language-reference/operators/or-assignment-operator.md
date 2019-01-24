---
title: Operador |= – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: f4f7806c8679af400a371decd0c367929b3fb81d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333259"
---
# <a name="-operator-c-reference"></a>Operador |= (referência do C#)

O operador de atribuição OR.

## <a name="remarks"></a>Comentários

Uma expressão que usa o operador de atribuição `|=`, como

```csharp
x |= y
```

equivale a

```csharp
x = x | y
```

exceto que `x` é avaliado apenas uma vez. O [operador &#124;](or-operator.md) executa uma operação OR lógica bit a bit em operandos integrais e OR lógica em operandos bool.

O operador `|=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador &#124;](or-operator.md) (consulte [operador](../keywords/operator.md)).

## <a name="example"></a>Exemplo

[!code-csharp[csRefOperators#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#10)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)