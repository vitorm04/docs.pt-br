---
title: Como localizar irmãos precedentes-LINQ to XML
description: 'Saiba como localizar elementos irmãos que precedem um determinado elemento. Dois métodos são mostrados: um usa XPathSelectElements ao longo do eixo irmão precedente, o outro usa XNode. ElementsBeforeSelf.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: 0cfd516f274eaf2940a7b944d34c6ea494e7eaa1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546185"
---
# <a name="how-to-find-preceding-siblings-linq-to-xml"></a><span data-ttu-id="3436a-104">Como localizar irmãos precedentes (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="3436a-104">How to find preceding siblings (LINQ to XML)</span></span>

<span data-ttu-id="3436a-105">Este artigo mostra como usar <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> ao longo do eixo irmão precedente para localizar elementos irmãos que precedem um determinado elemento e como usar <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> para localizar os mesmos elementos.</span><span class="sxs-lookup"><span data-stu-id="3436a-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> along the preceding-sibling axis to find sibling elements that precede a given element, and how to use <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> to find the same elements.</span></span>

## <a name="example-use-two-methods-to-find-sibling-elements-that-precede-an-element"></a><span data-ttu-id="3436a-106">Exemplo: usar dois métodos para localizar elementos irmãos que precedem um elemento</span><span class="sxs-lookup"><span data-stu-id="3436a-106">Example: Use two methods to find sibling elements that precede an element</span></span>

<span data-ttu-id="3436a-107">O exemplo a seguir localiza o `FullAddress` elemento em arquivo XML de exemplo de documento XML [: Customers e Orders](sample-xml-file-customers-orders.md)e recupera os elementos irmãos precedentes de duas maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="3436a-107">The following example finds the `FullAddress` element in XML document [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md), and retrieves the preceding sibling elements in two different ways.</span></span> <span data-ttu-id="3436a-108">Em seguida, ele compara os resultados e os encontra idênticos.</span><span class="sxs-lookup"><span data-stu-id="3436a-108">It then compares the results and finds them identical.</span></span>

> [!NOTE]
> <span data-ttu-id="3436a-109">Os dois métodos fornecem resultados que estão na ordem do documento.</span><span class="sxs-lookup"><span data-stu-id="3436a-109">Both methods provide results that are in document order.</span></span>

<span data-ttu-id="3436a-110">A expressão XPath usada é `preceding-sibling::*` .</span><span class="sxs-lookup"><span data-stu-id="3436a-110">The XPath expression used is `preceding-sibling::*`.</span></span>

```csharp
XElement co = XElement.Load("CustomersOrders.xml");

XElement add = co.Element("Customers").Element("Customer").Element("FullAddress");

// LINQ to XML query
IEnumerable<XElement> list1 = add.ElementsBeforeSelf();

// XPath expression
IEnumerable<XElement> list2 = add.XPathSelectElements("preceding-sibling::*");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list2)
    Console.WriteLine(el);
```

```vb
Dim co As XElement = XElement.Load("CustomersOrders.xml")
Dim add As XElement = co.<Customers>.<Customer>. _
        <FullAddress>.FirstOrDefault

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = add.ElementsBeforeSelf()

' XPath expression
Dim list2 As IEnumerable(Of XElement) = add.XPathSelectElements("preceding-sibling::*")

If list1.Count() = list2.Count() And _
        list1.Intersect(list2).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
For Each el As XElement In list2
    Console.WriteLine(el)
Next
```

<span data-ttu-id="3436a-111">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="3436a-111">This example produces the following output:</span></span>

```output
Results are identical
<CompanyName>Great Lakes Food Market</CompanyName>
<ContactName>Howard Snyder</ContactName>
<ContactTitle>Marketing Manager</ContactTitle>
<Phone>(503) 555-7555</Phone>
```

## <a name="see-also"></a><span data-ttu-id="3436a-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="3436a-112">See also</span></span>

- [<span data-ttu-id="3436a-113">LINQ to XML para usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3436a-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
