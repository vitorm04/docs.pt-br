---
title: Operador &lt;&lt;= – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: 4513c4b78dea3e8102c72a43249b4a44ffa2421d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333246"
---
# <a name="ltlt-operator-c-reference"></a>Operador &lt;&lt;= (referência do C#)

O operador de atribuição de deslocamento para a esquerda.

## <a name="remarks"></a>Comentários

Uma expressão da forma

```csharp
x <<= y
```

é avaliada como

```csharp
x = x << y
```

exceto que `x` é avaliado apenas uma vez. O [operador <<](left-shift-operator.md) desloca `x` para a esquerda pelo número de bits especificado pelo `y`.

O operador `<<=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador <<](left-shift-operator.md) (consulte [operador](../keywords/operator.md)).

## <a name="example"></a>Exemplo

[!code-csharp[csRefOperators#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#12)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
