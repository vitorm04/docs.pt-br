---
title: "Não é possível converter tipo anônimo em árvore de expressão porque ele contém um campo que é usado na inicialização de outro campo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36548
- vbc36548
dev_langs:
- VB
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bcd635d60eab6bae42f7ecd971c68e1b1b456c14
ms.lasthandoff: 03/13/2017

---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a>Não é possível converter tipo anônimo em árvore de expressão porque ele contém um campo usado na inicialização de outro campo
O compilador não aceita conversão de um anônimo em uma árvore de expressão quando uma propriedade do tipo anônimo é usada para inicializar outra propriedade do tipo anônimo. Por exemplo, no código a seguir, `Prop1` é declarado na lista de inicialização e, em seguida, usado como o valor inicial para `Prop2`.  
  
```vb  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 **ID do erro:** BC36548  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Atribua o valor inicial para `Prop1` a uma variável local. Atribuir a variável a ambos `Prop1` e `Prop2`, conforme mostrado no código a seguir.  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Árvores de expressão](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)   
 [Como usar árvores de expressão para compilar consultas dinâmicas](http://msdn.microsoft.com/library/1e37e0cc-eef3-48bb-8b69-3adabf322735)
