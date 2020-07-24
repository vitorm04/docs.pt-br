---
title: Como calcular valores intermediários (C#)
description: Este LINQ to XML exemplo no C# mostra como calcular valores intermediários que podem ser usados em classificação, filtragem e seleção.
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: fc648f20550de13735a1f6da6b2f811fd0d39004
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103619"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="cbe0c-103">Como calcular valores intermediários (C#)</span><span class="sxs-lookup"><span data-stu-id="cbe0c-103">How to calculate intermediate values (C#)</span></span>
<span data-ttu-id="cbe0c-104">Este exemplo mostra como calcular valores intermediários que podem ser usados na classificação, filtragem, e em selecionar.</span><span class="sxs-lookup"><span data-stu-id="cbe0c-104">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbe0c-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cbe0c-105">Example</span></span>  
 <span data-ttu-id="cbe0c-106">O exemplo a seguir utiliza a cláusula de `Let` .</span><span class="sxs-lookup"><span data-stu-id="cbe0c-106">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="cbe0c-107">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: dados numéricos (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cbe0c-107">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="cbe0c-108">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="cbe0c-108">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="cbe0c-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cbe0c-109">Example</span></span>  
 <span data-ttu-id="cbe0c-110">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="cbe0c-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="cbe0c-111">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cbe0c-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="cbe0c-112">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: dados numéricos em um namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="cbe0c-112">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="cbe0c-113">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="cbe0c-113">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
