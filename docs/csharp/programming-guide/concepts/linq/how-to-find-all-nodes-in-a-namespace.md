---
title: 'Como: Localizar todos os nós em um namespace (C#)'
ms.date: 07/20/2015
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: f8a6f33084417e0dd489002eaa5d2de509e30d39
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253781"
---
# <a name="how-to-find-all-nodes-in-a-namespace-c"></a><span data-ttu-id="82855-102">Como: Localizar todos os nós em um namespace (C#)</span><span class="sxs-lookup"><span data-stu-id="82855-102">How to: Find All Nodes in a Namespace (C#)</span></span>
<span data-ttu-id="82855-103">Você pode filtrar no namespace de cada elemento ou atributo para localizar todos os nós nesse namespace específico.</span><span class="sxs-lookup"><span data-stu-id="82855-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82855-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82855-104">Example</span></span>  
 <span data-ttu-id="82855-105">O exemplo a seguir cria uma árvore XML com as duas namespaces.</span><span class="sxs-lookup"><span data-stu-id="82855-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="82855-106">Em itera através da árvore e imprime os nomes de todos os elementos e atributos em uma desses namespaces.</span><span class="sxs-lookup"><span data-stu-id="82855-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
```csharp  
string markup = @"<aw:Root xmlns:aw='http://www.adventure-works.com' xmlns:fc='www.fourthcoffee.com'>  
  <fc:Child1>abc</fc:Child1>  
  <fc:Child2>def</fc:Child2>  
  <aw:Child3>ghi</aw:Child3>  
  <fc:Child4>  
    <fc:GrandChild1>jkl</fc:GrandChild1>  
    <aw:GrandChild2>mno</aw:GrandChild2>  
  </fc:Child4>  
</aw:Root>";  
XElement xmlTree = XElement.Parse(markup);  
Console.WriteLine("Nodes in the http://www.adventure-works.com namespace");  
IEnumerable<XElement> awElements =  
    from el in xmlTree.Descendants()  
    where el.Name.Namespace == "http://www.adventure-works.com"  
    select el;  
foreach (XElement el in awElements)  
    Console.WriteLine(el.Name.ToString());  
```  
  
 <span data-ttu-id="82855-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="82855-107">This code produces the following output:</span></span>  
  
```output  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="82855-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82855-108">Example</span></span>  
 <span data-ttu-id="82855-109">O arquivo XML acessado pela consulta contém pedidos de compra em dois namespaces diferentes.</span><span class="sxs-lookup"><span data-stu-id="82855-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="82855-110">A consulta cria uma nova árvore com apenas os elementos em uma namespaces.</span><span class="sxs-lookup"><span data-stu-id="82855-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="82855-111">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Ordens de compra consolidadas](./sample-xml-file-consolidated-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="82855-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](./sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("ConsolidatedPurchaseOrders.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement newTree = new XElement("Root",  
    from el in cpo.Root.Elements()  
    where el.Name.Namespace == aw  
    select el  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="82855-112">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="82855-112">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <aw:PurchaseOrder PONumber="11223" Date="2000-01-15" xmlns:aw="http://www.adventure-works.com">  
    <aw:ShippingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:ShippingAddress>  
    <aw:BillingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:BillingAddress>  
    <aw:DeliveryInstructions>Ship only complete order.</aw:DeliveryInstructions>  
    <aw:Item PartNum="LIT-01">  
      <aw:ProductID>Litware Networking Card</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>20.99</aw:Price>  
    </aw:Item>  
    <aw:Item PartNum="LIT-25">  
      <aw:ProductID>Litware 17in LCD Monitor</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>199.99</aw:Price>  
    </aw:Item>  
  </aw:PurchaseOrder>  
</Root>  
```  
