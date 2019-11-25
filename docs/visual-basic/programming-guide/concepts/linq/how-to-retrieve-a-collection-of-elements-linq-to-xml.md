---
title: 'Como: Recuperar uma coleção de elementos (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
ms.openlocfilehash: 592ef68206df59bc848644d0a62bf0efdb10609e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347591"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a><span data-ttu-id="bb6b1-102">How to: Retrieve a Collection of Elements (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb6b1-102">How to: Retrieve a Collection of Elements (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="bb6b1-103">Este tópico demonstra o método de <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="bb6b1-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="bb6b1-104">Esse método retorna uma coleção de elementos filho de um elemento.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb6b1-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb6b1-105">Example</span></span>  
 <span data-ttu-id="bb6b1-106">Este exemplo efetua iterações através dos elementos filho do elemento de `purchaseOrder` .</span><span class="sxs-lookup"><span data-stu-id="bb6b1-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="bb6b1-107">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bb6b1-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim childElements As IEnumerable(Of XElement)  
childElements = _  
    From el In po.Elements() _  
    Select el  
For Each el As XElement In childElements  
    Console.WriteLine("Name: " & el.Name.ToString())  
Next  
```  
  
 <span data-ttu-id="bb6b1-108">Este exemplo gerencia a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-108">This example produces the following output.</span></span>  
  
```console  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb6b1-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb6b1-109">See also</span></span>

- [<span data-ttu-id="bb6b1-110">Eixos LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb6b1-110">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
