---
title: Como localizar uma lista de elementos filho-LINQ to XML
description: Este artigo compara o eixo dos elementos filho do XPath com o eixo LINQ to XML XContainer. Elements.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7c589dd8-f680-4cdb-9d6a-78d57e2555e8
ms.openlocfilehash: 84b820f3192a173130c485f3e7cdadf9499932f1
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551942"
---
# <a name="how-to-find-a-list-of-child-elements-linq-to-xml"></a><span data-ttu-id="4e418-103">Como localizar uma lista de elementos filho (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="4e418-103">How to find a list of child elements (LINQ to XML)</span></span>

<span data-ttu-id="4e418-104">Este artigo compara o eixo dos elementos filho do XPath com o eixo de LINQ to XML <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="4e418-104">This article compares the XPath child elements axis to the LINQ to XML <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>

## <a name="example-find-all-child-elements-of-an-element"></a><span data-ttu-id="4e418-105">Exemplo: localizar todos os elementos filho de um elemento</span><span class="sxs-lookup"><span data-stu-id="4e418-105">Example: Find all child elements of an element</span></span>

<span data-ttu-id="4e418-106">Este exemplo localiza todos os elementos filho do `Address` elemento no [arquivo XML de exemplo documento XML: várias ordens de compra](sample-xml-file-multiple-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="4e418-106">This example finds all of the child elements of the `Address` element in XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

<span data-ttu-id="4e418-107">A expressão XPath é: `./*`</span><span class="sxs-lookup"><span data-stu-id="4e418-107">The XPath expression is: `./*`</span></span>

```csharp
XDocument cpo = XDocument.Load("PurchaseOrders.xml");
XElement po = cpo.Root.Element("PurchaseOrder").Element("Address");

// LINQ to XML query
IEnumerable<XElement> list1 = po.Elements();

// XPath expression
IEnumerable<XElement> list2 = po.XPathSelectElements("./*");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")
Dim po As XElement = cpo.Root.<PurchaseOrder>.<Address>.FirstOrDefault

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = po.Elements()

' XPath expression
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("./*")

If (list1.Count() = list2.Count()) AndAlso _
    (list1.Intersect(list2).Count() = list1.Count()) Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="4e418-108">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="4e418-108">This example produces the following output:</span></span>

```output
Results are identical
<Name>Ellen Adams</Name>
<Street>123 Maple Street</Street>
<City>Mill Valley</City>
<State>CA</State>
<Zip>10999</Zip>
<Country>USA</Country>
```

## <a name="see-also"></a><span data-ttu-id="4e418-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="4e418-109">See also</span></span>

- [<span data-ttu-id="4e418-110">LINQ to XML para usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e418-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
