---
title: Não é possível converter tipo anônimo em árvore de expressão porque ele contém um campo usado na inicialização de outro campo
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: d43f6ef19591af326d06a4ce21194d8f9fa58c2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a>Não é possível converter tipo anônimo em árvore de expressão porque ele contém um campo usado na inicialização de outro campo
O compilador não aceitar a conversão de um anônimo em uma árvore de expressão quando uma propriedade do tipo anônimo é usada para inicializar outra propriedade do tipo anônimo. Por exemplo, no código a seguir, `Prop1` é declarado na lista de inicialização e, em seguida, usado como o valor inicial de `Prop2`.  
  
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
  
-   Atribuir o valor inicial de `Prop1` a uma variável local. Atribuir a variável a ambos `Prop1` e `Prop2`, conforme mostrado no código a seguir.  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Tipos Anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Árvores de Expressão](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [Como usar árvores de expressão para compilar consultas dinâmicas](http://msdn.microsoft.com/library/1e37e0cc-eef3-48bb-8b69-3adabf322735)
