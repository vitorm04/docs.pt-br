---
title: Como calcular valores intermediários-LINQ to XML
description: Calcule valores intermediários para uso em classificação, filtragem e seleção.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: aa5b83e9bf359481773db673fd3de9c4dcff6af2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551887"
---
# <a name="how-to-calculate-intermediate-values-linq-to-xml"></a><span data-ttu-id="feab0-103">Como calcular valores intermediários (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="feab0-103">How to calculate intermediate values (LINQ to XML)</span></span>

<span data-ttu-id="feab0-104">Este artigo mostra como calcular valores intermediários para uso em classificação, filtragem e seleção em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="feab0-104">This article shows how to calculate intermediate values for use in sorting, filtering, and selecting in C# and Visual Basic.</span></span>

## <a name="example-use-the-let-clause-to-calculate-based-on-element-data"></a><span data-ttu-id="feab0-105">Exemplo: Use a `let` cláusula para calcular com base nos dados do elemento</span><span class="sxs-lookup"><span data-stu-id="feab0-105">Example: Use the `let` clause to calculate based on element data</span></span>

<span data-ttu-id="feab0-106">O exemplo a seguir usa a `let` cláusula para calcular produtos de valores numéricos de elementos.</span><span class="sxs-lookup"><span data-stu-id="feab0-106">The following example uses the `let` clause to calculate products of numerical values from elements.</span></span> <span data-ttu-id="feab0-107">Ele usa arquivo XML de exemplo de documento XML [: dados numéricos](sample-xml-file-numerical-data.md).</span><span class="sxs-lookup"><span data-stu-id="feab0-107">It uses XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md).</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
IEnumerable<decimal> extensions =
    from el in root.Elements("Data")
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")
    where extension >= 25
    orderby extension
    select extension;
foreach (decimal ex in extensions)
    Console.WriteLine(ex);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim extensions As IEnumerable(Of Decimal) = _
    From el In root.<Data> _
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _
    Where extension > 25 _
    Order By extension _
    Select extension
For Each ex As Decimal In extensions
    Console.WriteLine(ex)
Next
```

<span data-ttu-id="feab0-108">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="feab0-108">This example produces the following output:</span></span>

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="example-calculate-from-xml-thats-in-a-namespace"></a><span data-ttu-id="feab0-109">Exemplo: calcular do XML que está em um namespace</span><span class="sxs-lookup"><span data-stu-id="feab0-109">Example: Calculate from XML that's in a namespace</span></span>

<span data-ttu-id="feab0-110">O exemplo a seguir mostra a mesma consulta que antes, mas para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="feab0-110">The following example shows the same query as before, but for XML that's in a namespace.</span></span> <span data-ttu-id="feab0-111">Ele usa o arquivo XML de exemplo de documento XML [: dados numéricos em um namespace](sample-xml-file-numerical-data-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="feab0-111">It uses the XML document [Sample XML file: Numerical data in a namespace](sample-xml-file-numerical-data-namespace.md).</span></span>

<span data-ttu-id="feab0-112">Para obter mais informações, consulte [visão geral de namespaces](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="feab0-112">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Load("DataInNamespace.xml");
XNamespace ad = "http://www.adatum.com";
IEnumerable<decimal> extensions =
    from el in root.Elements(ad + "Data")
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")
    where extension >= 25
    orderby extension
    select extension;
foreach (decimal ex in extensions)
    Console.WriteLine(ex);
```

```vb
Imports <xmlns="http://www.adatum.com">

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("DataInNamespace.xml")
        Dim extensions As IEnumerable(Of Decimal) = _
            From el In root.<Data> _
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _
            Where extension > 25 _
            Order By extension _
            Select extension
        For Each ex As Decimal In extensions
            Console.WriteLine(ex)
        Next
    End Sub
End Module
```

<span data-ttu-id="feab0-113">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="feab0-113">This example produces the following output:</span></span>

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="see-also"></a><span data-ttu-id="feab0-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="feab0-114">See also</span></span>

- [<span data-ttu-id="feab0-115">Consultas básicas (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="feab0-115">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
