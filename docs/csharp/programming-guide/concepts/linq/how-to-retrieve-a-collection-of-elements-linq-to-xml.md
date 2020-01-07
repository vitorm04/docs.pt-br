---
title: Como recuperar uma coleção de elementos (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 89799b17115fb56a93bda5fbc144b21b334a6974
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345014"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="51337-102">Como recuperar uma coleção de elementos (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="51337-102">How to retrieve a collection of elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="51337-103">Este tópico demonstra o método de <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="51337-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="51337-104">Esse método retorna uma coleção de elementos filho de um elemento.</span><span class="sxs-lookup"><span data-stu-id="51337-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51337-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51337-105">Example</span></span>  
 <span data-ttu-id="51337-106">Este exemplo efetua iterações através dos elementos filho do elemento de `purchaseOrder` .</span><span class="sxs-lookup"><span data-stu-id="51337-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="51337-107">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="51337-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="51337-108">Este exemplo gerencia a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="51337-108">This example produces the following output.</span></span>  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="51337-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="51337-109">See also</span></span>

- [<span data-ttu-id="51337-110">Eixos do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="51337-110">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
