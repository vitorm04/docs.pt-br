---
title: Como criar hierarquia usando o agrupamento-LINQ to XML
description: Veja um exemplo de como os dados podem ser agrupados com base em valores relacionados em diferentes elementos e, em seguida, reordenados para posicionar os elementos relacionados em um elemento que reflete a relação.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 0213d59e-5f76-438c-9cab-4bf11f7b971d
ms.openlocfilehash: cd913a2546227154fc48ee4e4ae7d007b7e926a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552020"
---
# <a name="how-to-create-hierarchy-using-grouping-linq-to-xml"></a><span data-ttu-id="cdb9e-103">Como criar hierarquia usando o agrupamento (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="cdb9e-103">How to create hierarchy using grouping (LINQ to XML)</span></span>

<span data-ttu-id="cdb9e-104">Os dados podem ser agrupados com base em valores relacionados em diferentes elementos e, em seguida, reordenados para posicionar os elementos relacionados em um elemento que reflita a relação.</span><span class="sxs-lookup"><span data-stu-id="cdb9e-104">Data can be grouped based on related values in different elements, then reordered to place related elements together under an element that reflects the relationship.</span></span> <span data-ttu-id="cdb9e-105">Este artigo fornece um exemplo de C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cdb9e-105">This article provides an example for C# and Visual Basic.</span></span>

## <a name="example-create-a-new-xml-document-in-which-data-is-grouped-by-category"></a><span data-ttu-id="cdb9e-106">Exemplo: criar um novo documento XML no qual os dados são agrupados por categoria</span><span class="sxs-lookup"><span data-stu-id="cdb9e-106">Example: Create a new XML document in which data is grouped by category</span></span>

<span data-ttu-id="cdb9e-107">O exemplo a seguir mostra como agrupar dados e gerar XML com base no agrupamento.</span><span class="sxs-lookup"><span data-stu-id="cdb9e-107">The following example shows how to group data, and generate XML based on the grouping.</span></span> <span data-ttu-id="cdb9e-108">Ele primeiro agrupa dados por igualdade de valor dos `<Category>` elementos e gera um novo arquivo XML no qual a hierarquia XML reflete o agrupamento.</span><span class="sxs-lookup"><span data-stu-id="cdb9e-108">It first groups data by equality of value of the `<Category>` elements, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>

<span data-ttu-id="cdb9e-109">Este exemplo usa arquivo XML de exemplo de documento XML [: dados numéricos](sample-xml-file-numerical-data.md).</span><span class="sxs-lookup"><span data-stu-id="cdb9e-109">This example uses XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md).</span></span>

```csharp
XElement doc = XElement.Load("Data.xml");
var newData =
    new XElement("Root",
        from data in doc.Elements("Data")
        group data by (string)data.Element("Category") into groupedData
        select new XElement("Group",
            new XAttribute("ID", groupedData.Key),
            from g in groupedData
            select new XElement("Data",
                g.Element("Quantity"),
                g.Element("Price")
            )
        )
    );
Console.WriteLine(newData);
```

```vb
Dim doc As XElement = XElement.Load("Data.xml")
Dim newData As XElement = _
    <Root>
        <%= _
            From data In doc.<Data> _
            Group By category = data.<Category>(0).Value _
            Into groupedData = Group _
            Select <Group ID=<%= category %>>
                       <%= _
                           From g In groupedData _
                           Select _
                           <Data>
                               <%= g.<Quantity>(0) %>
                               <%= g.<Price>(0) %>
                           </Data> _
                       %>
                   </Group> _
        %>
    </Root>
Console.WriteLine(newData)
```

<span data-ttu-id="cdb9e-110">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="cdb9e-110">This example produces the following output:</span></span>

```xml
<Root>
  <Group ID="A">
    <Data>
      <Quantity>3</Quantity>
      <Price>24.50</Price>
    </Data>
    <Data>
      <Quantity>5</Quantity>
      <Price>4.95</Price>
    </Data>
    <Data>
      <Quantity>3</Quantity>
      <Price>66.00</Price>
    </Data>
    <Data>
      <Quantity>15</Quantity>
      <Price>29.00</Price>
    </Data>
  </Group>
  <Group ID="B">
    <Data>
      <Quantity>1</Quantity>
      <Price>89.99</Price>
    </Data>
    <Data>
      <Quantity>10</Quantity>
      <Price>.99</Price>
    </Data>
    <Data>
      <Quantity>8</Quantity>
      <Price>6.99</Price>
    </Data>
  </Group>
</Root>
```
