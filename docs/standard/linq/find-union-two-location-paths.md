---
title: Como localizar uma União de dois caminhos de local-LINQ to XML
description: 'Saiba como localizar a União dos resultados de dois caminhos de local XPath. Dois métodos são mostrados: um usa XPathSelectElements, o outro usa o operador de consulta padrão Concat.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: ba2a1eef73a586074c75a7fec84c912acb8b25e9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551912"
---
# <a name="how-to-find-a-union-of-two-location-paths-linq-to-xml"></a><span data-ttu-id="fab8a-104">Como localizar uma União de dois caminhos de local (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="fab8a-104">How to find a union of two location paths (LINQ to XML)</span></span>

<span data-ttu-id="fab8a-105">Este artigo mostra como usar <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> o para localizar a União dos resultados de dois caminhos de local XPath e como usar o operador de <xref:System.Linq.Enumerable.Concat%2A> consulta padrão para fazer a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="fab8a-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to find the union of the results of two XPath location paths, and how to use the <xref:System.Linq.Enumerable.Concat%2A> standard query operator to do the same thing.</span></span>

## <a name="example-find-all-category-and-price-elements-and-concatenate-them"></a><span data-ttu-id="fab8a-106">Exemplo: localizar todos `Category` os `Price` elementos e e concatena-los</span><span class="sxs-lookup"><span data-stu-id="fab8a-106">Example: Find all `Category` and `Price` elements and concatenate them</span></span>

<span data-ttu-id="fab8a-107">Este exemplo localiza todos os `Category` elementos e todos os `Price` elementos em um arquivo XML de exemplo de documento XML [: dados numéricos](sample-xml-file-numerical-data.md)e os concatena em uma única coleção.</span><span class="sxs-lookup"><span data-stu-id="fab8a-107">This example finds all of the `Category` elements and all of the `Price` elements in XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md), and concatenates them into a single collection.</span></span> <span data-ttu-id="fab8a-108">A expressão XPath é `//Category|//Price`.</span><span class="sxs-lookup"><span data-stu-id="fab8a-108">The XPath expression is `//Category|//Price`.</span></span>

> [!NOTE]
> <span data-ttu-id="fab8a-109">A consulta LINQ to XML chama <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> para colocar os resultados em ordem de documento.</span><span class="sxs-lookup"><span data-stu-id="fab8a-109">The LINQ to XML query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to put the results in document order.</span></span> <span data-ttu-id="fab8a-110">Os resultados da expressão XPath também estão em ordem de documento.</span><span class="sxs-lookup"><span data-stu-id="fab8a-110">The XPath expression results are also in document order.</span></span>

```csharp
XDocument data = XDocument.Load("Data.xml");

// LINQ to XML query
IEnumerable<XElement> list1 =
    data
    .Descendants("Category")
    .Concat(
        data
        .Descendants("Price")
    )
    .InDocumentOrder();

// XPath expression
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim data As XDocument = XDocument.Load("Data.xml")

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    data...<Category>.Concat(data...<Price>).InDocumentOrder()

' XPath expression
Dim list2 As IEnumerable(Of XElement) = _
    data.XPathSelectElements("//Category|//Price")

If list1.Count() = list2.Count() And _
        list1.Intersect(list2).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="fab8a-111">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="fab8a-111">This example produces the following output:</span></span>

```output
Results are identical
<Category>A</Category>
<Price>24.50</Price>
<Category>B</Category>
<Price>89.99</Price>
<Category>A</Category>
<Price>4.95</Price>
<Category>A</Category>
<Price>66.00</Price>
<Category>B</Category>
<Price>.99</Price>
<Category>A</Category>
<Price>29.00</Price>
<Category>B</Category>
<Price>6.99</Price>
```

## <a name="see-also"></a><span data-ttu-id="fab8a-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="fab8a-112">See also</span></span>

- [<span data-ttu-id="fab8a-113">LINQ to XML para usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fab8a-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
