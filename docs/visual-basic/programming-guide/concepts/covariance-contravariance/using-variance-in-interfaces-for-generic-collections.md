---
title: "Usando variação em Interfaces para coleções genéricas (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 86184c7de3fe16148bf954b16d703ca682216337
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a><span data-ttu-id="36027-102">Usando variação em Interfaces para coleções genéricas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36027-102">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>
<span data-ttu-id="36027-103">Uma interface de covariante permite que seus métodos retornar mais tipos derivados daquelas especificadas na interface.</span><span class="sxs-lookup"><span data-stu-id="36027-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="36027-104">Uma interface contravariant permite que seus métodos aceitar parâmetros de menos tipos derivados que aqueles especificados na interface.</span><span class="sxs-lookup"><span data-stu-id="36027-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="36027-105">No .NET Framework 4, várias interfaces existentes se tornou covariantes e contravariante.</span><span class="sxs-lookup"><span data-stu-id="36027-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="36027-106">Esses incluem <xref:System.Collections.Generic.IEnumerable%601>e <xref:System.IComparable%601>.</xref:System.IComparable%601> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="36027-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="36027-107">Isso permite que você reutilize métodos que operam com coleções genéricas de tipos base para coleções de tipos derivados.</span><span class="sxs-lookup"><span data-stu-id="36027-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="36027-108">Para obter uma lista de interfaces variantes no .NET Framework, consulte [variação em Interfaces genéricas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="36027-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="36027-109">Convertendo de coleções genéricas</span><span class="sxs-lookup"><span data-stu-id="36027-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="36027-110">O exemplo a seguir ilustra os benefícios de suporte a covariância de <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="36027-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="36027-111">O `PrintFullName` método aceita uma coleção do `IEnumerable(Of Person)` tipo como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="36027-111">The `PrintFullName` method accepts a collection of the `IEnumerable(Of Person)` type as a parameter.</span></span> <span data-ttu-id="36027-112">No entanto, você pode reutilizá-lo para uma coleção do `IEnumerable(Of Person)` tipo porque `Employee` herda `Person`.</span><span class="sxs-lookup"><span data-stu-id="36027-112">However, you can reuse it for a collection of the `IEnumerable(Of Person)` type because `Employee` inherits `Person`.</span></span>  
  
<span data-ttu-id="36027-113"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="36027-113"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
## <a name="comparing-generic-collections"></a><span data-ttu-id="36027-114">Comparando coleções genéricas</span><span class="sxs-lookup"><span data-stu-id="36027-114">Comparing Generic Collections</span></span>  
 <span data-ttu-id="36027-115">O exemplo a seguir ilustra os benefícios de suporte contravariância o <xref:System.Collections.Generic.IComparer%601>interface.</xref:System.Collections.Generic.IComparer%601></span><span class="sxs-lookup"><span data-stu-id="36027-115">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="36027-116">O `PersonComparer` classe implementa o `IComparer(Of Person)` interface.</span><span class="sxs-lookup"><span data-stu-id="36027-116">The `PersonComparer` class implements the `IComparer(Of Person)` interface.</span></span> <span data-ttu-id="36027-117">No entanto, você pode reutilizar essa classe para comparar uma sequência de objetos do `Employee` tipo porque `Employee` herda `Person`.</span><span class="sxs-lookup"><span data-stu-id="36027-117">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
```vb  
' Simple hierarhcy of classes.  
Public Class Person  
    Public Property FirstName As String  
    Public Property LastName As String  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
' The custom comparer for the Person type  
' with standard implementations of Equals()  
' and GetHashCode() methods.  
Class PersonComparer  
    Implements IEqualityComparer(Of Person)  
  
    Public Function Equals1(  
        ByVal x As Person,  
        ByVal y As Person) As Boolean _  
        Implements IEqualityComparer(Of Person).Equals  
  
        If x Is y Then Return True  
        If x Is Nothing OrElse y Is Nothing Then Return False  
        Return (x.FirstName = y.FirstName) AndAlso  
            (x.LastName = y.LastName)  
    End Function  
    Public Function GetHashCode1(  
        ByVal person As Person) As Integer _  
        Implements IEqualityComparer(Of Person).GetHashCode  
  
        If person Is Nothing Then Return 0  
        Dim hashFirstName =  
            If(person.FirstName Is Nothing,  
            0, person.FirstName.GetHashCode())  
        Dim hashLastName = person.LastName.GetHashCode()  
        Return hashFirstName Xor hashLastName  
    End Function  
End Class  
  
Sub Main()  
    Dim employees = New List(Of Employee) From {  
        New Employee With {.FirstName = "Michael", .LastName = "Alexander"},  
        New Employee With {.FirstName = "Jeff", .LastName = "Price"}  
    }  
  
    ' You can pass PersonComparer,   
    ' which implements IEqualityComparer(Of Person),  
    ' although the method expects IEqualityComparer(Of Employee)  
  
    Dim noduplicates As IEnumerable(Of Employee) = employees.Distinct(New PersonComparer())  
  
    For Each employee In noduplicates  
        Console.WriteLine(employee.FirstName & " " & employee.LastName)  
    Next  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="36027-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36027-118">See Also</span></span>  
 [<span data-ttu-id="36027-119">Variação em Interfaces genéricas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36027-119">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
