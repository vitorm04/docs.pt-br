---
title: Operador | – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 19a37bbb54d2ef3e15e4465df05c9b6df705206c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240353"
---
# <a name="-operator-c-reference"></a>Operador | (Referência de C#)
Os operadores binários `|` são predefinidos para os tipos integrais e `bool`. Para tipos integrais, o `|` computa o OR bit a bit de seus operandos. Para operandos `bool`, o `|` computa o OR lógico de seus operandos; ou seja, o resultado será `false` se e somente se, ambos seus operandos forem `false`.  
  
## <a name="remarks"></a>Comentários  
 O operador binário `|` avalia ambos os operandos, independentemente do valor do primeiro, em contraste ao [operador OR-condicional](conditional-or-operator.md) `||`.
 
 Os tipos definidos pelo usuário podem sobrecarregar o operador `|` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
