---
title: "N&#227;o &#233; poss&#237;vel converter tipo an&#244;nimo em &#225;rvore de express&#227;o porque ele cont&#233;m um campo usado na inicializa&#231;&#227;o de outro campo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36548"
  - "vbc36548"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36548"
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel converter tipo an&#244;nimo em &#225;rvore de express&#227;o porque ele cont&#233;m um campo usado na inicializa&#231;&#227;o de outro campo
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O compilador não aceita conversão de um anônimo em um árvore de expressão quando uma propriedade do tipo anônimo é usada para inicializar outra propriedade do tipo anônimo.  Por exemplo, no código a seguir, `Prop1` é declarado na lista de inicialização e, em seguida, usado como o valor inicial para `Prop2`.  
  
```vb#  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 **Identificação do erro:**  BC36548  
  
### Para corrigir este erro  
  
-   Atribua o valor inicial para `Prop1` a uma variável local.  Atribuir a variável a ambos `Prop1` e `Prop2`, conforme mostrado no seguinte código.  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## Consulte também  
 [Tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Árvores de expressão](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)   
 [Como usar árvores de expressão para compilar consultas dinâmicas](../Topic/How%20to:%20Use%20Expression%20Trees%20to%20Build%20Dynamic%20Queries%20\(C%23%20and%20Visual%20Basic\).md)