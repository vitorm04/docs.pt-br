---
title: + Operador (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: b49694bc8937c58bd295f0f8e57c378802d0dfb9
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47232378"
---
# <a name="-operator-c-reference"></a>Operador + (Referência de C#)
O operador `+` pode funcionar como um operador unário ou binário.  
  
## <a name="remarks"></a>Comentários  
 Os operadores `+` unários são predefinidos para todos os tipos numéricos. O resultado de uma operação `+` unária em um tipo numérico é apenas o valor do operando.  
  
 Operadores `+` binários são predefinidos para tipos numéricos e de cadeia de caracteres. Para tipos numéricos, + calcula a soma de dois operandos. Quando um ou os dois operandos forem do tipo de cadeia de caracteres, + concatenará as representações de cadeia de caracteres dos operandos.  
  
 Tipos de delegado também fornecem um operador `+` binário, que executa a concatenação de delegados.  
  
 Tipos definidos pelo usuário podem sobrecarregar os operadores `+` unários e `+` binários. As operações em tipos integrais geralmente são permitidas na enumeração. Para obter mais informações, consulte [operador (Referência de C#)](../../../csharp/language-reference/keywords/operator.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)  
- [operator (Referência de C#)](../../../csharp/language-reference/keywords/operator.md)
