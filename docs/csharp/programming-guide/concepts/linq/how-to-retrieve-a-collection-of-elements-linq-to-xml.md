---
title: Como recuperar uma coleção de elementos (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 8d2aab59a6c2a72d796bfaf40755bdf280c81b6a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320411"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="ebba3-102">Como recuperar uma coleção de elementos (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ebba3-102">How to: Retrieve a Collection of Elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="ebba3-103">Este tópico demonstra o método de <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="ebba3-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="ebba3-104">Esse método retorna uma coleção de elementos filho de um elemento.</span><span class="sxs-lookup"><span data-stu-id="ebba3-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebba3-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ebba3-105">Example</span></span>  
 <span data-ttu-id="ebba3-106">Este exemplo efetua iterações através dos elementos filho do elemento de `purchaseOrder` .</span><span class="sxs-lookup"><span data-stu-id="ebba3-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="ebba3-107">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="ebba3-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="ebba3-108">Este exemplo gerencia a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="ebba3-108">This example produces the following output.</span></span>  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebba3-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebba3-109">See Also</span></span>  
 [<span data-ttu-id="ebba3-110">Eixos do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ebba3-110">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
