---
title: 'Como: Calcular valores intermediários (C#)'
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 12c8a87114859ce7b47b8206acb454cdc2838470
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604317"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="52bd8-102">Como: Calcular valores intermediários (C#)</span><span class="sxs-lookup"><span data-stu-id="52bd8-102">How to: Calculate Intermediate Values (C#)</span></span>
<span data-ttu-id="52bd8-103">Este exemplo mostra como calcular valores intermediários que podem ser usados na classificação, filtragem, e em selecionar.</span><span class="sxs-lookup"><span data-stu-id="52bd8-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52bd8-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52bd8-104">Example</span></span>  
 <span data-ttu-id="52bd8-105">O exemplo a seguir utiliza a cláusula de `Let` .</span><span class="sxs-lookup"><span data-stu-id="52bd8-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="52bd8-106">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Dados numéricos (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="52bd8-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="52bd8-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="52bd8-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="52bd8-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52bd8-108">Example</span></span>  
 <span data-ttu-id="52bd8-109">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="52bd8-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="52bd8-110">Para obter mais informações, consulte [Trabalhando com namespaces XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="52bd8-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="52bd8-111">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Dados numéricos em um namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="52bd8-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="52bd8-112">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="52bd8-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="52bd8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52bd8-113">See also</span></span>

- [<span data-ttu-id="52bd8-114">Consultas básicas (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="52bd8-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
