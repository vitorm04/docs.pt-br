---
title: Métodos de &#39;System. Nullable (Of T)&#39; não podem ser usados como operandos do &#39;AddressOf&#39; operador
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 3a3e4fc033f47fb6a72076dff79f1eece8d01a30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="methods-of-39systemnullableof-t39-cannot-be-used-as-operands-of-the-39addressof39-operator"></a>Métodos de &#39;System. Nullable (Of T)&#39; não podem ser usados como operandos do &#39;AddressOf&#39; operador
Usa uma instrução de `AddressOf` operador com um operando que representa um procedimento com o <xref:System.Nullable%601> estrutura.  
  
 **ID do erro:** BC32126  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Substitua o nome do procedimento no `AddressOf` cláusula com um operando que não é um membro de <xref:System.Nullable%601>.  
  
-   Escrever uma classe que quebra o método de <xref:System.Nullable%601> que você deseja usar. No exemplo a seguir, o `NullableWrapper` classe define um novo método chamado `GetValueOrDefault`. Como esse novo método não é um membro de <xref:System.Nullable%601>, ele pode ser aplicado a `nullInstance`, uma instância de um tipo anulável, para formar um argumento para `AddressOf`.  
  
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
 [Tipos de Valor Anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
