---
title: 'Como: Localizar elementos descendentes (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e7e2dc9e-bda9-420d-a5b1-4fabf1cca46b
ms.openlocfilehash: 09f12dca7b6278327394126ffb0950682d285f88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780556"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="5d952-102">Como: Localizar elementos descendentes (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d952-102">How to: Find Descendant Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="5d952-103">Este tópico mostra como obter os elementos descendentes com um nome específico.</span><span class="sxs-lookup"><span data-stu-id="5d952-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="5d952-104">A expressão XPath é `//Name`.</span><span class="sxs-lookup"><span data-stu-id="5d952-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d952-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5d952-105">Example</span></span>  
 <span data-ttu-id="5d952-106">Este exemplo localiza os descendentes chamados `Name`.</span><span class="sxs-lookup"><span data-stu-id="5d952-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="5d952-107">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Várias ordens de compra (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5d952-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
      Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = po...<Name>  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("//Name")  
  
If (list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="5d952-108">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="5d952-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d952-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d952-109">See also</span></span>

- [<span data-ttu-id="5d952-110">LINQ to XML para os usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d952-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
