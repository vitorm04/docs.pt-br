---
title: 'Como: Localizar elementos em um Namespace (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c7cb3b77-3424-4b54-9efa-4dc715948e41
ms.openlocfilehash: f48ae0a03d625a3510b2280aa6361e2a731e5afe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780465"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="28a67-102">Como: Localizar elementos em um Namespace (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28a67-102">How to: Find Elements in a Namespace (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="28a67-103">As expressões XPath pode localizar nós em um namespace específico.</span><span class="sxs-lookup"><span data-stu-id="28a67-103">XPath expressions can find nodes in a particular namespace.</span></span> <span data-ttu-id="28a67-104">Prefixos de namespace do uso de expressões XPath para especificar namespaces.</span><span class="sxs-lookup"><span data-stu-id="28a67-104">XPath expressions use namespace prefixes for specifying namespaces.</span></span> <span data-ttu-id="28a67-105">Para analisar uma expressão XPath que contém prefixos de namespace, você deve passar um objeto para os métodos XPath que implementa <xref:System.Xml.IXmlNamespaceResolver>.</span><span class="sxs-lookup"><span data-stu-id="28a67-105">To parse an XPath expression that contains namespace prefixes, you must pass an object to the XPath methods that implements <xref:System.Xml.IXmlNamespaceResolver>.</span></span> <span data-ttu-id="28a67-106">Este exemplo usa <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="28a67-106">This example uses <xref:System.Xml.XmlNamespaceManager>.</span></span>  
  
 <span data-ttu-id="28a67-107">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="28a67-107">The XPath expression is:</span></span>  
  
 `./aw:*`  
  
## <a name="example"></a><span data-ttu-id="28a67-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28a67-108">Example</span></span>  
 <span data-ttu-id="28a67-109">O exemplo a seguir lê uma árvore XML que contém dois namespaces.</span><span class="sxs-lookup"><span data-stu-id="28a67-109">The following example reads an XML tree that contains two namespaces.</span></span> <span data-ttu-id="28a67-110">Usa <xref:System.Xml.XmlReader> para ler o documento XML.</span><span class="sxs-lookup"><span data-stu-id="28a67-110">It uses an <xref:System.Xml.XmlReader> to read the XML document.</span></span> <span data-ttu-id="28a67-111">Então obtém <xref:System.Xml.XmlNameTable> de <xref:System.Xml.XmlReader>, e <xref:System.Xml.XmlNamespaceManager> de <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="28a67-111">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="28a67-112">Usa <xref:System.Xml.XmlNamespaceManager> ao selecionar elementos.</span><span class="sxs-lookup"><span data-stu-id="28a67-112">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>  
  
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
  
 <span data-ttu-id="28a67-113">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="28a67-113">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="28a67-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28a67-114">See also</span></span>

- [<span data-ttu-id="28a67-115">LINQ to XML para os usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28a67-115">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
