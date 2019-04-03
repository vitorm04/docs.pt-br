---
title: 'Como: Localizar um elemento filho (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: adb46c98-a650-42e2-b62d-835920fe8421
ms.openlocfilehash: 96ad54d6f89aefd004a7803baef855d656b8a82d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821524"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="9e821-102">Como: Localizar um elemento filho (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e821-102">How to: Find a Child Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="9e821-103">Este tópico compara o eixo de elemento filho XPath com o método [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A>.</span><span class="sxs-lookup"><span data-stu-id="9e821-103">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="9e821-104">A expressão XPath é `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="9e821-104">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e821-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e821-105">Example</span></span>  
 <span data-ttu-id="9e821-106">Este exemplo localiza o elemento filho `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="9e821-106">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="9e821-107">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Várias ordens de compra (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9e821-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")  
Dim po As XElement = cpo.Root.<PurchaseOrder>.FirstOrDefault  
  
'LINQ to XML query  
Dim el1 As XElement = po.<DeliveryNotes>.FirstOrDefault  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("DeliveryNotes")  
' same as "child::DeliveryNotes"  
' same as "./DeliveryNotes"  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 <span data-ttu-id="9e821-108">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9e821-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e821-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e821-109">See also</span></span>

- [<span data-ttu-id="9e821-110">LINQ to XML para os usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e821-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
