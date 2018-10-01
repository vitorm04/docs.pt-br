---
title: Operador != (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: e974ffb1b25944e24fca23864dc7e932ec1876d5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47455468"
---
# <a name="-operator-c-reference"></a>Operador != (Referência de C#)
O operador de desigualdade (`!=`) retornará false se seus operandos forem iguais; caso contrário, true. Os operadores de desigualdade são predefinidos para todos os tipos, incluindo cadeia de caracteres e objeto. Os tipos definidos pelo usuário podem sobrecarregar o operador `!=`.  
  
## <a name="remarks"></a>Comentários  
 Para tipos de valor predefinidos, o operador de desigualdade (`!=`) retornará true se os valores dos seus operandos forem diferentes; caso contrário, false. Para tipos de referência diferentes de `string`, o `!=` retornará true se seus dois operandos se referirem a objetos diferentes. Para o tipo `string`, o `!=` compara os valores das cadeias de caracteres.  
  
 Os tipos de valor definidos pelo usuário podem sobrecarregar o operador `!=` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)). Os tipos de referência definidos pelo usuário também podem fazer isso, embora o `!=` se comporte, por padrão, conforme descrito acima para os tipos de referência predefinidos e definidos pelo usuário. Se `!=` estiver sobrecarregado, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) também deverá estar sobrecarregado. As operações em tipos integrais geralmente são permitidas na enumeração.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
