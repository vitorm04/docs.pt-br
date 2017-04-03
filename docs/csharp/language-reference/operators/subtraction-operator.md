---
title: "- Operator (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- -_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 418166f412a5821ffcb1f0cd53ae46829fde9dc5
ms.lasthandoff: 03/13/2017

---
# <a name="--operator-c-reference"></a>Operador - (Referência de C#)
O operador `-` pode funcionar como um operador unário ou binário.  
  
## <a name="remarks"></a>Comentários  
 Os operadores `-` unários são predefinidos para todos os tipos numéricos. O resultado de uma operação `-` unária em um tipo numérico é a negação numérica do operando.  
  
 Os operadores `-` binários são predefinidos para todos os tipos numéricos e de enumeração para subtrair o segundo operando do primeiro.  
  
 Os tipos delegados também fornecem um operador `-` binário, que executa a remoção de delegados.  
  
 Tipos definidos pelo usuário podem sobrecarregar os operadores `-` unários e `-` binários. Para obter mais informações, consulte [operador (Referência de C#)](../../../csharp/language-reference/keywords/operator.md).  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#40](../../../csharp/language-reference/operators/codesnippet/CSharp/subtraction-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
