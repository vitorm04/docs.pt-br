---
title: Como classificar elementos (C#)
description: Saiba como classificar elementos. Veja exemplos de como escrever uma consulta que classifica seus resultados em um documento XML.
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 669d9cf583e6ab70c93be39ad271eaf104f88718
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301431"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="3a582-104">Como classificar elementos (C#)</span><span class="sxs-lookup"><span data-stu-id="3a582-104">How to sort elements (C#)</span></span>
<span data-ttu-id="3a582-105">Este exemplo mostra como escrever uma consulta que classifica seus resultados.</span><span class="sxs-lookup"><span data-stu-id="3a582-105">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a582-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3a582-106">Example</span></span>  
 <span data-ttu-id="3a582-107">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: dados numéricos (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3a582-107">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="3a582-108">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3a582-108">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="3a582-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3a582-109">Example</span></span>  
 <span data-ttu-id="3a582-110">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="3a582-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="3a582-111">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3a582-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="3a582-112">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: dados numéricos em um namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="3a582-112">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="3a582-113">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3a582-113">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a582-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="3a582-114">See also</span></span>

- [<span data-ttu-id="3a582-115">Classificando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="3a582-115">Sorting Data (C#)</span></span>](./sorting-data.md)
