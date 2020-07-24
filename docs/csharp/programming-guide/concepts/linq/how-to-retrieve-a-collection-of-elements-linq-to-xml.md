---
title: Como recuperar uma coleção de elementos (LINQ to XML) (C#)
description: O método Elements em C# recupera uma coleção dos elementos filho de um elemento. Este exemplo de LINQ to XML itera por meio de elementos filho de um elemento.
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 4f9b6ae4713af9ce1a4eeb5257f57cd9724f68b2
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103350"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="91250-104">Como recuperar uma coleção de elementos (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="91250-104">How to retrieve a collection of elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="91250-105">Este tópico demonstra o método de <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="91250-105">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="91250-106">Esse método retorna uma coleção de elementos filho de um elemento.</span><span class="sxs-lookup"><span data-stu-id="91250-106">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91250-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="91250-107">Example</span></span>  
 <span data-ttu-id="91250-108">Este exemplo efetua iterações através dos elementos filho do elemento de `purchaseOrder` .</span><span class="sxs-lookup"><span data-stu-id="91250-108">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="91250-109">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="91250-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="91250-110">Este exemplo gerencia a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="91250-110">This example produces the following output.</span></span>  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="91250-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="91250-111">See also</span></span>

- [<span data-ttu-id="91250-112">Eixos do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="91250-112">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
