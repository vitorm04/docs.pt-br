---
title: Como calcular valores intermediários (C#)
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 3ead3bfb02f7c9192db96996c1f1e01a86a4191a
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141440"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="24fc6-102">Como calcular valores intermediários (C#)</span><span class="sxs-lookup"><span data-stu-id="24fc6-102">How to calculate intermediate values (C#)</span></span>
<span data-ttu-id="24fc6-103">Este exemplo mostra como calcular valores intermediários que podem ser usados na classificação, filtragem, e em selecionar.</span><span class="sxs-lookup"><span data-stu-id="24fc6-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24fc6-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24fc6-104">Example</span></span>  
 <span data-ttu-id="24fc6-105">O exemplo a seguir utiliza a cláusula de `Let` .</span><span class="sxs-lookup"><span data-stu-id="24fc6-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="24fc6-106">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: dados numéricos (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="24fc6-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="24fc6-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="24fc6-107">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="24fc6-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24fc6-108">Example</span></span>  
 <span data-ttu-id="24fc6-109">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="24fc6-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="24fc6-110">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="24fc6-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="24fc6-111">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: dados numéricos em um namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="24fc6-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="24fc6-112">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="24fc6-112">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
