---
title: 'Como: Controlar o tipo de uma projeção (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a0171276-0b46-4817-aee5-a8d5191b12fe
ms.openlocfilehash: dd09914a75a8d4b20ddf9ff452f046bf7671152f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051780"
---
# <a name="how-to-control-the-type-of-a-projection-visual-basic"></a><span data-ttu-id="01d8d-102">Como: Controlar o tipo de uma projeção (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01d8d-102">How to: Control the Type of a Projection (Visual Basic)</span></span>
<span data-ttu-id="01d8d-103">A projeção é o processo de receber um dataset, de filtre-o, para alterar sua forma, e mesmo de alterar seu tipo.</span><span class="sxs-lookup"><span data-stu-id="01d8d-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="01d8d-104">A maioria das expressões de consulta executam projeções.</span><span class="sxs-lookup"><span data-stu-id="01d8d-104">Most query expressions perform projections.</span></span> <span data-ttu-id="01d8d-105">A maioria das expressões de consulta mostradas nesta seção valor para <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, mas você pode controlar o tipo de projeção para criar coleções de outros tipos.</span><span class="sxs-lookup"><span data-stu-id="01d8d-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="01d8d-106">Este tópico mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="01d8d-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01d8d-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="01d8d-107">Example</span></span>  
 <span data-ttu-id="01d8d-108">O exemplo a seguir define um novo tipo, `Customer`.</span><span class="sxs-lookup"><span data-stu-id="01d8d-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="01d8d-109">A expressão de consulta cria uma instância em novos objetos de `Customer` na cláusula `Select` .</span><span class="sxs-lookup"><span data-stu-id="01d8d-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="01d8d-110">Isso faz com que o tipo da expressão de consulta para ser <xref:System.Collections.Generic.IEnumerable%601> de `Customer`.</span><span class="sxs-lookup"><span data-stu-id="01d8d-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="01d8d-111">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Clientes e ordens (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="01d8d-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Public Class Customer  
    Private customerIDValue As String  
    Public Property CustomerID() As String  
        Get  
            Return customerIDValue  
        End Get  
        Set(ByVal value As String)  
            customerIDValue = value  
        End Set  
    End Property  
  
    Private companyNameValue As String  
    Public Property CompanyName() As String  
        Get  
            Return companyNameValue  
        End Get  
        Set(ByVal value As String)  
            companyNameValue = value  
        End Set  
    End Property  
  
    Private contactNameValue As String  
    Public Property ContactName() As String  
        Get  
            Return contactNameValue  
        End Get  
        Set(ByVal value As String)  
            contactNameValue = value  
        End Set  
    End Property  
  
    Public Sub New(ByVal customerID As String, _  
                   ByVal companyName As String, _  
                   ByVal contactName As String)  
        CustomerIDValue = customerID  
        CompanyNameValue = companyName  
        ContactNameValue = contactName  
    End Sub  
  
    Public Overrides Function ToString() As String  
        Return String.Format("{0}:{1}:{2}", Me.CustomerID, Me.CompanyName, Me.ContactName)  
    End Function  
End Class  
  
Sub Main()  
    Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
    Dim custList As IEnumerable(Of Customer) = _  
        From el In custOrd.<Customers>.<Customer> _  
        Select New Customer( _  
            el.@<CustomerID>, _  
            el.<CompanyName>.Value, _  
            el.<ContactName>.Value _  
        )  
    For Each cust In custList  
        Console.WriteLine(cust)  
    Next  
End Sub  
```  
  
 <span data-ttu-id="01d8d-112">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="01d8d-112">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="01d8d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01d8d-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
- [<span data-ttu-id="01d8d-114">Projeções e transformações (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01d8d-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
