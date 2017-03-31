---
title: "Operador -&gt; (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ->_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
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
ms.openlocfilehash: 09cf5a2828ef0e3adae378a9fb93dabd564df256
ms.lasthandoff: 03/13/2017

---
# <a name="-gt-operator-c-reference"></a>Operador -&gt; (Referência de C#)
O operador `->` combina a desreferência de ponteiro e o acesso de membro.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão da forma,  
  
```  
x->y  
```  
  
 (em que `x` é um ponteiro de tipo `T*` e `y` é um membro de `T`) é equivalente a,  
  
```  
(*x).y  
```  
  
 O operador `->` pode ser usado apenas no código que está marcado como [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
 O operador `->` não pode ser sobrecarregado.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
