---
title: 'Como: Localizar elementos relacionados (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 41b386ee-562d-4841-bd6b-e44a7eb69f26
ms.openlocfilehash: 2aa3f6c6c2c2ac327ff2dffc206cdd294e12d7a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253637"
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="cd868-102">Como: Localizar elementos relacionados (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cd868-102">How to: Find Related Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="cd868-103">Este tópico mostra como obter um elemento que seleciona em um atributo que é chamada pelo valor de outro elemento.</span><span class="sxs-lookup"><span data-stu-id="cd868-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="cd868-104">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="cd868-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="cd868-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd868-105">Example</span></span>  
 <span data-ttu-id="cd868-106">Este exemplo localiza o 12o elemento de `Order` , e localiza no cliente para essa ordem.</span><span class="sxs-lookup"><span data-stu-id="cd868-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="cd868-107">Observe que a indexação em uma lista no .NET é com base em “zero”.</span><span class="sxs-lookup"><span data-stu-id="cd868-107">Note that indexing into a list in .NET is 'zero' based.</span></span> <span data-ttu-id="cd868-108">A indexação em uma coleção de nós em um predicado XPath “é um” com base.</span><span class="sxs-lookup"><span data-stu-id="cd868-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="cd868-109">Este exemplo reflete essa diferença.</span><span class="sxs-lookup"><span data-stu-id="cd868-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="cd868-110">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Clientes e ordens (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="cd868-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XDocument co = XDocument.Load("CustomersOrders.xml");  
  
// LINQ to XML query  
XElement customer1 =  
    (from el in co.Descendants("Customer")  
     where (string)el.Attribute("CustomerID") ==  
          (string)(co  
              .Element("Root")  
              .Element("Orders")  
              .Elements("Order")  
              .ToList()[11]  
              .Element("CustomerID"))  
    select el)  
    .First();  
  
// An alternate way to write the query that avoids creation  
// of a System.Collections.Generic.List:  
XElement customer2 =  
    (from el in co.Descendants("Customer")  
     where (string)el.Attribute("CustomerID") ==  
          (string)(co  
              .Element("Root")  
              .Element("Orders")  
              .Elements("Order")  
              .Skip(11).First()  
              .Element("CustomerID"))  
    select el)  
    .First();  
  
// XPath expression  
XElement customer3 = co.XPathSelectElement(  
  ".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]");  
  
if (customer1 == customer2 && customer1 == customer3)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(customer1);  
```  
  
 <span data-ttu-id="cd868-111">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="cd868-111">This example produces the following output:</span></span>  
  
```output  
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
 