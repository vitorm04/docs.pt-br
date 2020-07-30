---
title: Como encontrar uma União de dois caminhos de local (XPath-LINQ to XML) (C#)
description: Saiba como encontrar uma União de dois caminhos de local XPath usando uma expressão XPath. Examine um exemplo de código que usa um arquivo XML de exemplo.
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 65b20fe25a0990fd82ce3bd08c3433499e728512
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303316"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="c8c7d-104">Como encontrar uma União de dois caminhos de local (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c8c7d-104">How to find a union of two location paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="c8c7d-105">O XPath permite que você localize a união de resultados de dois caminhos de local XPath.</span><span class="sxs-lookup"><span data-stu-id="c8c7d-105">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="c8c7d-106">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="c8c7d-106">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="c8c7d-107">Você pode obter os mesmos resultados usando o operador padrão de consulta de <xref:System.Linq.Enumerable.Concat%2A> .</span><span class="sxs-lookup"><span data-stu-id="c8c7d-107">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8c7d-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8c7d-108">Example</span></span>  
 <span data-ttu-id="c8c7d-109">Este exemplo localiza os elementos de `Category` e todos os elementos de `Price` , e os concatena em uma única coleção.</span><span class="sxs-lookup"><span data-stu-id="c8c7d-109">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="c8c7d-110">Observe que a consulta de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] chama <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> para ordenar os resultados.</span><span class="sxs-lookup"><span data-stu-id="c8c7d-110">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="c8c7d-111">Os resultados da avaliação de expressão XPath são também em ordem do documento.</span><span class="sxs-lookup"><span data-stu-id="c8c7d-111">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="c8c7d-112">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: dados numéricos (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c8c7d-112">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="c8c7d-113">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="c8c7d-113">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  