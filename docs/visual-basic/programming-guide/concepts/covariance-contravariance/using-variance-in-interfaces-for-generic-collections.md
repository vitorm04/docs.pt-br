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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 86184c7de3fe16148bf954b16d703ca682216337
ms.lasthandoff: 03/13/2017

---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a>Usando variação em Interfaces para coleções genéricas (Visual Basic)
Uma interface de covariante permite que seus métodos retornar mais tipos derivados daquelas especificadas na interface. Uma interface contravariant permite que seus métodos aceitar parâmetros de menos tipos derivados que aqueles especificados na interface.  
  
 No .NET Framework 4, várias interfaces existentes se tornou covariantes e contravariante. Esses incluem <xref:System.Collections.Generic.IEnumerable%601>e <xref:System.IComparable%601>.</xref:System.IComparable%601> </xref:System.Collections.Generic.IEnumerable%601> Isso permite que você reutilize métodos que operam com coleções genéricas de tipos base para coleções de tipos derivados.  
  
 Para obter uma lista de interfaces variantes no .NET Framework, consulte [variação em Interfaces genéricas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="converting-generic-collections"></a>Convertendo de coleções genéricas  
 O exemplo a seguir ilustra os benefícios de suporte a covariância de <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601> O `PrintFullName` método aceita uma coleção do `IEnumerable(Of Person)` tipo como um parâmetro. No entanto, você pode reutilizá-lo para uma coleção do `IEnumerable(Of Person)` tipo porque `Employee` herda `Person`.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="comparing-generic-collections"></a>Comparando coleções genéricas  
 O exemplo a seguir ilustra os benefícios de suporte contravariância o <xref:System.Collections.Generic.IComparer%601>interface.</xref:System.Collections.Generic.IComparer%601> O `PersonComparer` classe implementa o `IComparer(Of Person)` interface. No entanto, você pode reutilizar essa classe para comparar uma sequência de objetos do `Employee` tipo porque `Employee` herda `Person`.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Variação em Interfaces genéricas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
