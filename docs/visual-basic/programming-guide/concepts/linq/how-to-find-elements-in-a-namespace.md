---
title: 'Como: localizar elementos em um Namespace (XPath-LINQ para XML) (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7cb3b77-3424-4b54-9efa-4dc715948e41
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 257d4c37f849bbc50aac6b9cb4531d1084163db2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="d25b7-102">Como: localizar elementos em um Namespace (XPath-LINQ para XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d25b7-102">How to: Find Elements in a Namespace (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="d25b7-103">As expressões XPath pode localizar nós em um namespace específico.</span><span class="sxs-lookup"><span data-stu-id="d25b7-103">XPath expressions can find nodes in a particular namespace.</span></span> <span data-ttu-id="d25b7-104">Prefixos de namespace do uso de expressões XPath para especificar namespaces.</span><span class="sxs-lookup"><span data-stu-id="d25b7-104">XPath expressions use namespace prefixes for specifying namespaces.</span></span> <span data-ttu-id="d25b7-105">Para analisar uma expressão XPath que contém prefixos de namespace, você deve passar um objeto para os métodos XPath que implementa <xref:System.Xml.IXmlNamespaceResolver>.</span><span class="sxs-lookup"><span data-stu-id="d25b7-105">To parse an XPath expression that contains namespace prefixes, you must pass an object to the XPath methods that implements <xref:System.Xml.IXmlNamespaceResolver>.</span></span> <span data-ttu-id="d25b7-106">Este exemplo usa <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="d25b7-106">This example uses <xref:System.Xml.XmlNamespaceManager>.</span></span>  
  
 <span data-ttu-id="d25b7-107">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="d25b7-107">The XPath expression is:</span></span>  
  
 `./aw:*`  
  
## <a name="example"></a><span data-ttu-id="d25b7-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d25b7-108">Example</span></span>  
 <span data-ttu-id="d25b7-109">O exemplo a seguir lê uma árvore XML que contém dois namespaces.</span><span class="sxs-lookup"><span data-stu-id="d25b7-109">The following example reads an XML tree that contains two namespaces.</span></span> <span data-ttu-id="d25b7-110">Usa <xref:System.Xml.XmlReader> para ler o documento XML.</span><span class="sxs-lookup"><span data-stu-id="d25b7-110">It uses an <xref:System.Xml.XmlReader> to read the XML document.</span></span> <span data-ttu-id="d25b7-111">Então obtém <xref:System.Xml.XmlNameTable> de <xref:System.Xml.XmlReader>, e <xref:System.Xml.XmlNamespaceManager> de <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="d25b7-111">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="d25b7-112">Usa <xref:System.Xml.XmlNamespaceManager> ao selecionar elementos.</span><span class="sxs-lookup"><span data-stu-id="d25b7-112">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>  
  
```vb  
Dim reader As XmlReader = _  
        XmlReader.Create("ConsolidatedPurchaseOrders.xml")  
Dim root As XElement = XElement.Load(reader)  
Dim nameTable As XmlNameTable = reader.NameTable  
Dim namespaceManager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)  
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com")  
  
Dim list1 As IEnumerable(Of XElement) = _  
        root.XPathSelectElements("./aw:*", namespaceManager)  
Dim list2 As IEnumerable(Of XElement) = _  
    From el In root.Elements() _  
    Where el.Name.Namespace = "http://www.adventure-works.com" _  
    Select el  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list2  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="d25b7-113">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="d25b7-113">This example produces the following output:</span></span>  
  
```  
Results are identical  
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
```  
  
## <a name="see-also"></a><span data-ttu-id="d25b7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d25b7-114">See Also</span></span>  
 [<span data-ttu-id="d25b7-115">LINQ to XML para XPath usuários (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d25b7-115">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
