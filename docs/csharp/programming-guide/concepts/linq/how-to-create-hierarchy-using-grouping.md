---
title: Como criar uma hierarquia usando o agrupamento (C#)
ms.date: 07/20/2015
ms.assetid: 0213d59e-5f76-438c-9cab-4bf11f7b971d
ms.openlocfilehash: 8fa384ced04a90002f8f721266f163c874d6e0ff
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45649686"
---
# <a name="how-to-create-hierarchy-using-grouping-c"></a><span data-ttu-id="407d5-102">Como criar uma hierarquia usando o agrupamento (C#)</span><span class="sxs-lookup"><span data-stu-id="407d5-102">How to: Create Hierarchy Using Grouping (C#)</span></span>
<span data-ttu-id="407d5-103">Este exemplo mostra como agrupar dados, e gerencia em XML baseado em agrupamento.</span><span class="sxs-lookup"><span data-stu-id="407d5-103">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="407d5-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="407d5-104">Example</span></span>  
 <span data-ttu-id="407d5-105">Este exemplo primeiro agrupa dados por uma categoria, então gerencia um novo arquivo XML na hierarquia XML reflete o agrupamento.</span><span class="sxs-lookup"><span data-stu-id="407d5-105">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="407d5-106">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: dados numéricos (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="407d5-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="407d5-107">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="407d5-107">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="407d5-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="407d5-108">See Also</span></span>

- [<span data-ttu-id="407d5-109">Técnicas avançadas de consulta (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="407d5-109">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
