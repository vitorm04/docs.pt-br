---
title: Como recuperar uma coleção de elementos-LINQ to XML
description: Saiba como usar o método XContainer. Elements para recuperar uma coleção de elementos filho de um elemento.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: e73f608cff13f75f769f77372dc1c09949e00b0e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551865"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml"></a><span data-ttu-id="98a31-103">Como recuperar uma coleção de elementos (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="98a31-103">How to retrieve a collection of elements (LINQ to XML)</span></span>

<span data-ttu-id="98a31-104">Este artigo demonstra o <xref:System.Xml.Linq.XContainer.Elements%2A> método, que recupera uma coleção dos elementos filho de um elemento.</span><span class="sxs-lookup"><span data-stu-id="98a31-104">This article demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method, which retrieves a collection of the child elements of an element.</span></span>

## <a name="example-iterate-through-the-child-elements-of-an-element"></a><span data-ttu-id="98a31-105">Exemplo: iterar pelos elementos filho de um elemento</span><span class="sxs-lookup"><span data-stu-id="98a31-105">Example: Iterate through the child elements of an element</span></span>

<span data-ttu-id="98a31-106">Este exemplo efetua iterações através dos elementos filho do elemento de `purchaseOrder` .</span><span class="sxs-lookup"><span data-stu-id="98a31-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span> <span data-ttu-id="98a31-107">Ele usa arquivo XML de exemplo de documento XML [: ordem de compra típica](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="98a31-107">It uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> childElements =
    from el in po.Elements()
    select el;
foreach (XElement el in childElements)
    Console.WriteLine("Name: " + el.Name);
```

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

<span data-ttu-id="98a31-108">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="98a31-108">This example produces the following output:</span></span>

```output
Name: Address
Name: Address
Name: DeliveryNotes
Name: Items
```

## <a name="see-also"></a><span data-ttu-id="98a31-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="98a31-109">See also</span></span>

- [<span data-ttu-id="98a31-110">Visão geral dos eixos de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="98a31-110">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
