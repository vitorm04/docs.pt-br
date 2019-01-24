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
ms.openlocfilehash: 185ea3aabff4794ec08cca541773dbec3574ab4b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333506"
---
# <a name="-operator-c-reference"></a>Operador | (referência do C#)

Os operadores binários `|` são predefinidos para os tipos integrais e `bool`. Para tipos integrais, o `|` computa o OR bit a bit de seus operandos. Para operandos `bool`, o `|` computa o OR lógico de seus operandos; ou seja, o resultado será `false` se e somente se, ambos seus operandos forem `false`.

## <a name="remarks"></a>Comentários

O operador binário `|` avalia ambos os operandos, independentemente do valor do primeiro, em contraste ao [operador OR-condicional](conditional-or-operator.md) `||`.

Os tipos definidos pelo usuário podem sobrecarregar o operador `|` (consulte [operador](../keywords/operator.md)).

## <a name="example"></a>Exemplo

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)