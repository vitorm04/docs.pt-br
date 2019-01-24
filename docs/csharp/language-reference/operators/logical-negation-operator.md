---
title: '! Operador – referência do C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- '! operator [C#]'
- logical negation operator (!) [C#]
- NOT operator [C#]
ms.assetid: f5ae133f-8f64-4560-b34f-cd9cd5eed4ad
ms.openlocfilehash: 6b6d1796032f536aac0be49d4f101c1380b4e98f
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333220"
---
# <a name="-operator-c-reference"></a>! operator (Referência de C#)

O operador de negação lógica (`!`) é um operador unário que nega seu operando. Ele é definido para `bool` e retornará `true` se e somente se, o operando for `false`.

## <a name="remarks"></a>Comentários

Os tipos definidos pelo usuário podem sobrecarregar o operador `!` (consulte [operador](../keywords/operator.md)).

## <a name="example"></a>Exemplo

[!code-csharp[csRefOperators#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#7)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)