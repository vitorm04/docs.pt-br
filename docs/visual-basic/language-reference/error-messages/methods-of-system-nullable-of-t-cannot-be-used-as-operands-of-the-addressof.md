---
title: "Métodos de &quot;System. Nullable (Of T)&quot; não podem ser usados como operandos do operador &quot;AddressOf&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32126
- bc32126
dev_langs:
- VB
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
caps.latest.revision: 5
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
ms.openlocfilehash: b57f303cd4b18af87c3d82ba801af764e9628213
ms.lasthandoff: 03/13/2017

---
# <a name="methods-of-39systemnullableof-t39-cannot-be-used-as-operands-of-the-39addressof39-operator"></a>Métodos de 'System. Nullable (Of T)' não podem ser usados como operandos do operador 'AddressOf'
Uma instrução usa o `AddressOf` operador com um operando que representa um procedimento do <xref:System.Nullable%601>estrutura.</xref:System.Nullable%601>  
  
 **ID do erro:** BC32126  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Substitua o nome do procedimento no `AddressOf` cláusula com um operando que não seja um membro do <xref:System.Nullable%601>.</xref:System.Nullable%601>  
  
-   Escrever uma classe que quebra o método de <xref:System.Nullable%601>que você deseja usar.</xref:System.Nullable%601> No exemplo a seguir, o `NullableWrapper` classe define um novo método chamado `GetValueOrDefault`. Como esse novo método não é um membro do <xref:System.Nullable%601>, ele pode ser aplicado a `nullInstance`, uma instância de um tipo anulável, para formar um argumento para `AddressOf`.</xref:System.Nullable%601>  
  
```vb  
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
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Nullable%601>   
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Tipos de valor anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
