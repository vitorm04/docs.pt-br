---
title: "Operador &amp; (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: db187f168717eb0106bc3a1a1f71ab7c05d5f777
ms.lasthandoff: 03/13/2017

---
# <a name="amp-operator-c-reference"></a>Operador &amp; (Referência de C#)
O operador & pode funcionar como um operador unário ou binário.  
  
## <a name="remarks"></a>Comentários  
 O operador unário & retorna o endereço de seu operando (requer um contexto [unsafe](../../../csharp/language-reference/keywords/unsafe.md)).  
  
 Os operadores binários & são predefinidos para os tipos integrais e `bool`. Para os tipos integrais, o & computa o AND lógico bit a bit de seus operandos. Para operandos `bool`, o & computa o AND lógico de seus operandos; ou seja, o resultado será `true` se e somente se ambos seus operandos forem `true`.  
  
 O operador `&` avalia os dois operadores independentemente do valor do primeiro. Por exemplo:  
  
 [!code-cs[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 Tipos definidos pelo usuário podem sobrecarregar o operador binário `&` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)). As operações em tipos integrais geralmente são permitidas na enumeração. Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
