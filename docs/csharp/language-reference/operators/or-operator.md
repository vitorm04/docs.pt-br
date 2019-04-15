---
title: Operador | – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 38f8e21dbd07868441e0c4fbb6074f9897905222
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312872"
---
# <a name="-operator-c-reference"></a>Operador | (referência do C#)

Os operadores binários `|` são predefinidos para os tipos integrais e `bool`. Para tipos integrais, o `|` computa o OR bit a bit de seus operandos. Para operandos `bool`, o `|` computa o OR lógico de seus operandos; ou seja, o resultado será `false` se e somente se, ambos seus operandos forem `false`.

## <a name="remarks"></a>Comentários

O operador binário `|` avalia ambos os operandos, independentemente do valor do primeiro, em contraste ao [operador OR-condicional](boolean-logical-operators.md#conditional-logical-or-operator-) `||`.

Os tipos definidos pelo usuário podem sobrecarregar o operador `|` (consulte [operador](../keywords/operator.md)).

## <a name="example"></a>Exemplo

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores C#](index.md)