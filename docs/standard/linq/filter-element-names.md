---
title: Como filtrar em nomes de elementos-LINQ to XML
description: Saiba como filtrar o nome do elemento ao chamar um método que retorna um IEnumerable de XElement.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 1f831fe0008c94b3956e93f3ced7176d8c0bf34e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551851"
---
# <a name="how-to-filter-on-element-names-linq-to-xml"></a><span data-ttu-id="0ff01-103">Como filtrar em nomes de elemento (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="0ff01-103">How to filter on element names (LINQ to XML)</span></span>

<span data-ttu-id="0ff01-104">Quando você chamar um dos métodos que <xref:System.Collections.Generic.IEnumerable%601> de retorno de <xref:System.Xml.Linq.XElement>, você pode filtrar no nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="0ff01-104">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>

## <a name="example-retrieve-descendants-filtered-to-a-specified-name"></a><span data-ttu-id="0ff01-105">Exemplo: recuperar descendentes filtrados para um nome especificado</span><span class="sxs-lookup"><span data-stu-id="0ff01-105">Example: Retrieve descendants filtered to a specified name</span></span>

<span data-ttu-id="0ff01-106">Este exemplo recupera uma coleção de descendentes que é filtrada para conter somente descendentes com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="0ff01-106">This example retrieves a collection of descendants that's filtered to contain only descendants with the specified name.</span></span>

<span data-ttu-id="0ff01-107">Este exemplo usa arquivo XML de exemplo de documento XML [: ordem de compra típica](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="0ff01-107">This example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> items =
    from el in po.Descendants("ProductName")
    select el;
foreach(XElement prdName in items)
    Console.WriteLine(prdName.Name + ":" + (string) prdName);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim items As IEnumerable(Of XElement) = _
    From el In po...<ProductName> _
    Select el
For Each prdName As XElement In items
    Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)
Next
```

<span data-ttu-id="0ff01-108">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="0ff01-108">This example produces the following output:</span></span>

```output
ProductName:Lawnmower
ProductName:Baby Monitor
```

<span data-ttu-id="0ff01-109">Os outros métodos que <xref:System.Collections.Generic.IEnumerable%601> de retorno de coleções de <xref:System.Xml.Linq.XElement> segue o mesmo padrão.</span><span class="sxs-lookup"><span data-stu-id="0ff01-109">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="0ff01-110">Suas assinaturas são semelhantes a <xref:System.Xml.Linq.XContainer.Elements%2A> e a <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ff01-110">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="0ff01-111">O seguinte é a lista completa dos métodos semelhantes que tenham assinaturas de método:</span><span class="sxs-lookup"><span data-stu-id="0ff01-111">The following is the complete list of methods that have similar method signatures:</span></span>

- <xref:System.Xml.Linq.XNode.Ancestors%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a><span data-ttu-id="0ff01-112">Exemplo: recuperar do XML que está em um namespace</span><span class="sxs-lookup"><span data-stu-id="0ff01-112">Example: Retrieve from XML that's in a namespace</span></span>

<span data-ttu-id="0ff01-113">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="0ff01-113">The following example shows the same query for XML that's in a namespace.</span></span> <span data-ttu-id="0ff01-114">Para obter mais informações, consulte [visão geral de namespaces](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0ff01-114">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="0ff01-115">O exemplo usa arquivo XML de exemplo de documento XML [: ordem de compra típica em um namespace](sample-xml-file-typical-purchase-order-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="0ff01-115">The example uses XML document [Sample XML file: Typical purchase order in a namespace](sample-xml-file-typical-purchase-order-namespace.md).</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");
IEnumerable<XElement> items =
    from el in po.Descendants(aw + "ProductName")
    select el;
foreach (XElement prdName in items)
    Console.WriteLine(prdName.Name + ":" + (string)prdName);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim items As IEnumerable(Of XElement) = _
            From el In po...<aw:ProductName> _
            Select el
        For Each prdName As XElement In items
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)
        Next
    End Sub
End Module
```

<span data-ttu-id="0ff01-116">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="0ff01-116">This example produces the following output:</span></span>

```output
{http://www.adventure-works.com}ProductName:Lawnmower
{http://www.adventure-works.com}ProductName:Baby Monitor
```

## <a name="see-also"></a><span data-ttu-id="0ff01-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="0ff01-117">See also</span></span>

- [<span data-ttu-id="0ff01-118">Visão geral dos eixos de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="0ff01-118">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
