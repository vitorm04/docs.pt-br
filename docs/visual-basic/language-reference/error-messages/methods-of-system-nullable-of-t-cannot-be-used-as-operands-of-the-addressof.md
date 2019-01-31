---
title: Os métodos de 'System.Nullable(Of T)' não podem ser usados como operandos do operador 'AddressOf'
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 59e89b24eca6a034dc1df2216f6f0d68e8191a18
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278549"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a><span data-ttu-id="785c0-102">Os métodos de 'System.Nullable(Of T)' não podem ser usados como operandos do operador 'AddressOf'</span><span class="sxs-lookup"><span data-stu-id="785c0-102">Methods of 'System.Nullable(Of T)' cannot be used as operands of the 'AddressOf' operator</span></span>
<span data-ttu-id="785c0-103">Uma instrução usa o `AddressOf` operador com um operando que representa um procedimento do <xref:System.Nullable%601> estrutura.</span><span class="sxs-lookup"><span data-stu-id="785c0-103">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>  
  
 <span data-ttu-id="785c0-104">**ID do erro:** BC32126</span><span class="sxs-lookup"><span data-stu-id="785c0-104">**Error ID:** BC32126</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="785c0-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="785c0-105">To correct this error</span></span>  
  
-   <span data-ttu-id="785c0-106">Substitua o nome do procedimento na `AddressOf` cláusula com um operando que não é um membro de <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="785c0-106">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>  
  
-   <span data-ttu-id="785c0-107">Escrever uma classe que encapsula o método de <xref:System.Nullable%601> que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="785c0-107">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="785c0-108">No exemplo a seguir, o `NullableWrapper` classe define um novo método chamado `GetValueOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="785c0-108">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="785c0-109">Como esse novo método não é um membro da <xref:System.Nullable%601>, ele pode ser aplicado a `nullInstance`, uma instância de um tipo anulável, para formar um argumento para `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="785c0-109">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="785c0-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="785c0-110">See also</span></span>
- <xref:System.Nullable%601>
- [<span data-ttu-id="785c0-111">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="785c0-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="785c0-112">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="785c0-112">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="785c0-113">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="785c0-113">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
