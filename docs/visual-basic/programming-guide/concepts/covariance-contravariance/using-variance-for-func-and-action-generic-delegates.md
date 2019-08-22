---
title: Usando a variação para Func e delegados genéricos de ação (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: ce560f6246469620032ececa4afeeffe69baf407
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664356"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="b2aad-102">Usando a variação para Func e delegados genéricos de ação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2aad-102">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>
<span data-ttu-id="b2aad-103">Esses exemplos demonstram como usar covariância e contravariância nos delegados genéricos `Func` e `Action` para permitir a reutilização dos métodos e fornecer mais flexibilidade em seu código.</span><span class="sxs-lookup"><span data-stu-id="b2aad-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="b2aad-104">Para obter mais informações sobre covariância e contravariância, consulte [variação em delegados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="b2aad-104">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="b2aad-105">Usando delegados com parâmetros de tipo covariantes</span><span class="sxs-lookup"><span data-stu-id="b2aad-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="b2aad-106">O exemplo a seguir ilustra os benefícios do suporte à covariância nos delegados genéricos `Func`.</span><span class="sxs-lookup"><span data-stu-id="b2aad-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="b2aad-107">O método `FindByTitle` assume um parâmetro do tipo `String` e retorna um objeto do tipo `Employee`.</span><span class="sxs-lookup"><span data-stu-id="b2aad-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="b2aad-108">No entanto, você pode atribuir esse método ao delegado `Func(Of String, Person)` porque `Employee` herda `Person`.</span><span class="sxs-lookup"><span data-stu-id="b2aad-108">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>  
  
```vb  
' Simple hierarchy of classes.  
Public Class Person  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
  
Class Finder  
    Public Shared Function FindByTitle(  
        ByVal title As String) As Employee  
        ' This is a stub for a method that returns  
        ' an employee that has the specified title.  
        Return New Employee  
    End Function  
  
    Sub Test()  
        ' Create an instance of the delegate without using variance.  
        Dim findEmployee As Func(Of String, Employee) =  
            AddressOf FindByTitle  
  
        ' The delegate expects a method to return Person,  
        ' but you can assign it a method that returns Employee.  
        Dim findPerson As Func(Of String, Person) =  
            AddressOf FindByTitle  
  
        ' You can also assign a delegate   
        ' that returns a more derived type to a delegate   
        ' that returns a less derived type.  
        findPerson = findEmployee  
    End Sub  
End Class  
```  
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="b2aad-109">Usando delegados com parâmetros de tipo contravariantes</span><span class="sxs-lookup"><span data-stu-id="b2aad-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="b2aad-110">O exemplo a seguir ilustra os benefícios do suporte à contravariância nos delegados genéricos `Action`.</span><span class="sxs-lookup"><span data-stu-id="b2aad-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="b2aad-111">O método `AddToContacts` assume um parâmetro do tipo `Person`.</span><span class="sxs-lookup"><span data-stu-id="b2aad-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="b2aad-112">No entanto, você pode atribuir esse método ao delegado `Action(Of Employee)` porque `Employee` herda `Person`.</span><span class="sxs-lookup"><span data-stu-id="b2aad-112">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>  
  
```vb  
Public Class Person  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
  
Class AddressBook  
    Shared Sub AddToContacts(ByVal person As Person)  
        ' This method adds a Person object  
        ' to a contact list.  
    End Sub  
  
    Sub Test()  
        ' Create an instance of the delegate without using variance.  
        Dim addPersonToContacts As Action(Of Person) =  
            AddressOf AddToContacts  
  
        ' The Action delegate expects   
        ' a method that has an Employee parameter,  
        ' but you can assign it a method that has a Person parameter  
        ' because Employee derives from Person.  
        Dim addEmployeeToContacts As Action(Of Employee) =  
            AddressOf AddToContacts  
  
        ' You can also assign a delegate   
        ' that accepts a less derived parameter   
        ' to a delegate that accepts a more derived parameter.  
        addEmployeeToContacts = addPersonToContacts  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2aad-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2aad-113">See also</span></span>

- [<span data-ttu-id="b2aad-114">Covariância e contravariância (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2aad-114">Covariance and Contravariance (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="b2aad-115">Genéricos</span><span class="sxs-lookup"><span data-stu-id="b2aad-115">Generics</span></span>](../../../../standard/generics/index.md)
