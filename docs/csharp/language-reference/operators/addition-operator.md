---
title: "+ Operador (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5455375148f1924c7fe1cdb10e7924abb83a1565
ms.contentlocale: pt-br
ms.lasthandoff: 09/25/2017

---
# <a name="-operator-c-reference"></a>Operador + (Referência de C#)
O operador `+` pode funcionar como um operador unário ou binário.  
  
## <a name="remarks"></a>Comentários  
 Os operadores `+` unários são predefinidos para todos os tipos numéricos. O resultado de uma operação `+` unária em um tipo numérico é apenas o valor do operando.  
  
 Operadores `+` binários são predefinidos para tipos numéricos e de cadeia de caracteres. Para tipos numéricos, + calcula a soma de dois operandos. Quando um ou os dois operandos forem do tipo de cadeia de caracteres, + concatenará as representações de cadeia de caracteres dos operandos.  
  
 Tipos de delegado também fornecem um operador `+` binário, que executa a concatenação de delegados.  
  
 Tipos definidos pelo usuário podem sobrecarregar os operadores `+` unários e `+` binários. As operações em tipos integrais geralmente são permitidas na enumeração. Para obter mais informações, consulte [operador (Referência de C#)](../../../csharp/language-reference/keywords/operator.md).  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)   
 [operator (Referência de C#)](../../../csharp/language-reference/keywords/operator.md)

