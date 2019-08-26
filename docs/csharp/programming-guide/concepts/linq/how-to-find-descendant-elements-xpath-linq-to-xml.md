---
title: 'Como: Localizar elementos descendentes (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
ms.openlocfilehash: 8e9a2a1767f718d236682f0340a1f410a5cf70f6
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593422"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="d589f-102">Como: Localizar elementos descendentes (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d589f-102">How to: Find Descendant Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="d589f-103">Este tópico mostra como obter os elementos descendentes com um nome específico.</span><span class="sxs-lookup"><span data-stu-id="d589f-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="d589f-104">A expressão XPath é `//Name`.</span><span class="sxs-lookup"><span data-stu-id="d589f-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d589f-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d589f-105">Example</span></span>  
 <span data-ttu-id="d589f-106">Este exemplo localiza os descendentes chamados `Name`.</span><span class="sxs-lookup"><span data-stu-id="d589f-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="d589f-107">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Várias ordens de compra (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d589f-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Root.Descendants("Name");  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("//Name");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="d589f-108">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="d589f-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
