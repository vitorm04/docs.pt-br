---
title: 'Como: Localizar elementos relacionados (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6b0ef058-d704-48a5-98cd-33f00d088af9
ms.openlocfilehash: 58137a1bca93c0281424ba457569631a4b513a55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780426"
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="bcaab-102">Como: Localizar elementos relacionados (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcaab-102">How to: Find Related Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="bcaab-103">Este tópico mostra como obter um elemento que seleciona em um atributo que é chamada pelo valor de outro elemento.</span><span class="sxs-lookup"><span data-stu-id="bcaab-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="bcaab-104">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="bcaab-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="bcaab-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bcaab-105">Example</span></span>  
 <span data-ttu-id="bcaab-106">Este exemplo localiza o 12o elemento de `Order` , e localiza no cliente para essa ordem.</span><span class="sxs-lookup"><span data-stu-id="bcaab-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="bcaab-107">Observe que a indexação em uma lista no .NET é com base em “zero”.</span><span class="sxs-lookup"><span data-stu-id="bcaab-107">Note that indexing into a list in .NET is 'zero' based.</span></span> <span data-ttu-id="bcaab-108">A indexação em uma coleção de nós em um predicado XPath “é um” com base.</span><span class="sxs-lookup"><span data-stu-id="bcaab-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="bcaab-109">Este exemplo reflete essa diferença.</span><span class="sxs-lookup"><span data-stu-id="bcaab-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="bcaab-110">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Clientes e ordens (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bcaab-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XDocument = XDocument.Load("CustomersOrders.xml")  
  
' LINQ to XML query  
Dim customer1 As XElement = ( _  
    From el In co...<Customer> _  
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _  
        ToList()(11).<CustomerID>(0).Value _  
    Select el).First()  
  
' An alternate way to write the query that avoids creation  
' of a System.Collections.Generic.List:  
Dim customer2 As XElement = ( _  
    From el In co...<Customer> _  
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _  
        Skip(11).First().<CustomerID>(0).Value _  
    Select el).First()  
  
' XPath expression  
Dim customer3 As XElement = co.XPathSelectElement _  
    (".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]")  
  
If customer1 Is customer2 And customer1 Is customer3 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(customer1)  
```  
  
 <span data-ttu-id="bcaab-111">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="bcaab-111">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Customer CustomerID="HUNGC">  
  <CompanyName>Hungry Coyote Import Store</CompanyName>  
  <ContactName>Yoshi Latimer</ContactName>  
  <ContactTitle>Sales Representative</ContactTitle>  
  <Phone>(503) 555-6874</Phone>  
  <Fax>(503) 555-2376</Fax>  
  <FullAddress>  
    <Address>City Center Plaza 516 Main St.</Address>  
    <City>Elgin</City>  
    <Region>OR</Region>  
    <PostalCode>97827</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
</Customer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bcaab-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bcaab-112">See also</span></span>

- [<span data-ttu-id="bcaab-113">LINQ to XML para os usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcaab-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
