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
# <a name="methods-of-39systemnullableof-t39-cannot-be-used-as-operands-of-the-39addressof39-operator"></a><span data-ttu-id="788f0-102">Métodos de &#39;System. Nullable (Of T)&#39; não podem ser usados como operandos do &#39;AddressOf&#39; operador</span><span class="sxs-lookup"><span data-stu-id="788f0-102">Methods of &#39;System.Nullable(Of T)&#39; cannot be used as operands of the &#39;AddressOf&#39; operator</span></span>
<span data-ttu-id="788f0-103">Usa uma instrução de `AddressOf` operador com um operando que representa um procedimento com o <xref:System.Nullable%601> estrutura.</span><span class="sxs-lookup"><span data-stu-id="788f0-103">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>  
  
 <span data-ttu-id="788f0-104">**ID do erro:** BC32126</span><span class="sxs-lookup"><span data-stu-id="788f0-104">**Error ID:** BC32126</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="788f0-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="788f0-105">To correct this error</span></span>  
  
-   <span data-ttu-id="788f0-106">Substitua o nome do procedimento no `AddressOf` cláusula com um operando que não é um membro de <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="788f0-106">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>  
  
-   <span data-ttu-id="788f0-107">Escrever uma classe que quebra o método de <xref:System.Nullable%601> que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="788f0-107">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="788f0-108">No exemplo a seguir, o `NullableWrapper` classe define um novo método chamado `GetValueOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="788f0-108">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="788f0-109">Como esse novo método não é um membro de <xref:System.Nullable%601>, ele pode ser aplicado a `nullInstance`, uma instância de um tipo anulável, para formar um argumento para `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="788f0-109">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="788f0-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="788f0-110">See Also</span></span>  
 <xref:System.Nullable%601>  
 [<span data-ttu-id="788f0-111">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="788f0-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="788f0-112">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="788f0-112">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="788f0-113">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="788f0-113">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
