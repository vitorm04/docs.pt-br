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
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: acbbf313b2957b2df53d543b000001263eca9fb0
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="methods-of-39systemnullableof-t39-cannot-be-used-as-operands-of-the-39addressof39-operator"></a><span data-ttu-id="dfc92-102">Métodos de 'System. Nullable (Of T)' não podem ser usados como operandos do operador 'AddressOf'</span><span class="sxs-lookup"><span data-stu-id="dfc92-102">Methods of &#39;System.Nullable(Of T)&#39; cannot be used as operands of the &#39;AddressOf&#39; operator</span></span>
<span data-ttu-id="dfc92-103">Uma instrução usa o `AddressOf` operador com um operando que representa um procedimento do <xref:System.Nullable%601>estrutura.</xref:System.Nullable%601></span><span class="sxs-lookup"><span data-stu-id="dfc92-103">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>  
  
 <span data-ttu-id="dfc92-104">**ID do erro:** BC32126</span><span class="sxs-lookup"><span data-stu-id="dfc92-104">**Error ID:** BC32126</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dfc92-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="dfc92-105">To correct this error</span></span>  
  
-   <span data-ttu-id="dfc92-106">Substitua o nome do procedimento no `AddressOf` cláusula com um operando que não seja um membro do <xref:System.Nullable%601>.</xref:System.Nullable%601></span><span class="sxs-lookup"><span data-stu-id="dfc92-106">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>  
  
-   <span data-ttu-id="dfc92-107">Escrever uma classe que quebra o método de <xref:System.Nullable%601>que você deseja usar.</xref:System.Nullable%601></span><span class="sxs-lookup"><span data-stu-id="dfc92-107">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="dfc92-108">No exemplo a seguir, o `NullableWrapper` classe define um novo método chamado `GetValueOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="dfc92-108">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="dfc92-109">Como esse novo método não é um membro do <xref:System.Nullable%601>, ele pode ser aplicado a `nullInstance`, uma instância de um tipo anulável, para formar um argumento para `AddressOf`.</xref:System.Nullable%601></span><span class="sxs-lookup"><span data-stu-id="dfc92-109">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dfc92-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfc92-110">See Also</span></span>  
 <span data-ttu-id="dfc92-111"><xref:System.Nullable%601></span><span class="sxs-lookup"><span data-stu-id="dfc92-111"><xref:System.Nullable%601></span></span>   
<span data-ttu-id="dfc92-112"> [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="dfc92-112"> [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="dfc92-113"> [Tipos de valor anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span><span class="sxs-lookup"><span data-stu-id="dfc92-113"> [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span></span>  
<span data-ttu-id="dfc92-114"> [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)</span><span class="sxs-lookup"><span data-stu-id="dfc92-114"> [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)</span></span>
