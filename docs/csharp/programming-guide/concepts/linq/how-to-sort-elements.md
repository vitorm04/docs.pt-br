---
title: 'Como: Classificar elementos (C#)'
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 074428413fa57d8f0e5ae94970c2aeeeb9e4cc7c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592463"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="e08ec-102">Como: Classificar elementos (C#)</span><span class="sxs-lookup"><span data-stu-id="e08ec-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="e08ec-103">Este exemplo mostra como escrever uma consulta que classifica seus resultados.</span><span class="sxs-lookup"><span data-stu-id="e08ec-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e08ec-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e08ec-104">Example</span></span>  
 <span data-ttu-id="e08ec-105">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Dados numéricos (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e08ec-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> prices =  
    from el in root.Elements("Data")  
    let price = (decimal)el.Element("Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="e08ec-106">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e08ec-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="e08ec-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e08ec-107">Example</span></span>  
 <span data-ttu-id="e08ec-108">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="e08ec-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e08ec-109">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e08ec-109">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="e08ec-110">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Dados numéricos em um namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="e08ec-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace aw = "http://www.adatum.com";  
IEnumerable<decimal> prices =  
    from el in root.Elements(aw + "Data")  
    let price = (decimal)el.Element(aw + "Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="e08ec-111">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e08ec-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="e08ec-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e08ec-112">See also</span></span>

- [<span data-ttu-id="e08ec-113">Classificando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="e08ec-113">Sorting Data (C#)</span></span>](./sorting-data.md)
