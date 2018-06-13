---
title: Operador -&gt; (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: 037229b2081a43077cb4b5d02a8929b06ba9e077
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171974"
---
# <a name="-gt-operator-c-reference"></a>Operador -&gt; (Referência de C#)
O operador `->` combina a desreferência de ponteiro e o acesso de membro.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão da forma,  
  
```csharp  
x->y  
```  
  
 (em que `x` é um ponteiro de tipo `T*` e `y` é um membro de `T`) é equivalente a,  
  
```csharp  
(*x).y  
```  
  
 O operador `->` pode ser usado apenas no código que está marcado como [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
 O operador `->` não pode ser sobrecarregado.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
