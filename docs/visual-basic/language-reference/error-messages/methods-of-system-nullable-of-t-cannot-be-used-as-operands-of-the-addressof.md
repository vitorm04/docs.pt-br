---
title: "Os m&#233;todos de &#39;System.Nullable(Of T)&#39; n&#227;o podem ser usados como operandos do operador &#39;AddressOf&#39; | Microsoft Docs"
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
  - "vbc32126"
  - "bc32126"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32126"
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Os m&#233;todos de &#39;System.Nullable(Of T)&#39; n&#227;o podem ser usados como operandos do operador &#39;AddressOf&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma instrução usa o operador `AddressOf` com um operando que representa um procedimento da estrutura <xref:System.Nullable%601>.  
  
 **Identificação do erro:**  BC32126  
  
### Para corrigir este erro  
  
-   Substitua o nome do procedimento na cláusula `AddressOf` com um operando que não seja um membro de <xref:System.Nullable%601>.  
  
-   Escreva uma classe que quebra o método de <xref:System.Nullable%601> que você deseja usar.  No exemplo a seguir, a classe `NullableWrapper` define um novo método chamado `GetValueOrDefault`.  Como esse novo método não é um membro do <xref:System.Nullable%601>, ele pode ser aplicado a `nullInstance`, uma instância de uma tipo anulável, para formar um argumento para `AddressOf`.  
  
    ```vb#  
    Module Module1  
  
        Delegate Function Deleg() As Integer  
  
        Sub Main()  
            Dim nullInstance As New Nullable(Of Integer)(1)  
  
            Dim del As Deleg  
  
            ' GetValueOrDefault is a method of the Nullable generic  
            ' type. It cannot be used as an operand of AddressOf.  
            ' del = AddressOf nullInstance.GetValueOrDefault  
  
            ' The following line uses the GetValueOrDefault method  
            ' defined in the NullableWrapper class.  
            del = AddressOf (New NullableWrapper(  
                Of Integer)(nullInstance)).GetValueOrDefault  
  
            Console.WriteLine(del.Invoke())  
        End Sub  
  
        Class NullableWrapper(Of T As Structure)  
            Private m_Value As Nullable(Of T)  
  
            Sub New(ByVal Value As Nullable(Of T))  
                m_Value = Value  
            End Sub  
  
            Public Function GetValueOrDefault() As T  
                Return m_Value.Value  
            End Function  
        End Class  
    End Module  
    ```  
  
## Consulte também  
 <xref:System.Nullable%601>   
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Tipos de valor que permitem valor nulo](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)