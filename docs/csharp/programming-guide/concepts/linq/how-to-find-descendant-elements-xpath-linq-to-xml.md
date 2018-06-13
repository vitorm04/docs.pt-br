---
title: Como localizar elementos descendentes (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
ms.openlocfilehash: c75b797f876df7696a26bb39792fa7cc7566e6f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320983"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="b1972-102">Como localizar elementos descendentes (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b1972-102">How to: Find Descendant Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="b1972-103">Este tópico mostra como obter os elementos descendentes com um nome específico.</span><span class="sxs-lookup"><span data-stu-id="b1972-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="b1972-104">A expressão XPath é `//Name`.</span><span class="sxs-lookup"><span data-stu-id="b1972-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1972-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1972-105">Example</span></span>  
 <span data-ttu-id="b1972-106">Este exemplo localiza os descendentes chamados `Name`.</span><span class="sxs-lookup"><span data-stu-id="b1972-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="b1972-107">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: vários pedidos de compra (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b1972-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="b1972-108">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="b1972-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1972-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1972-109">See Also</span></span>  
 [<span data-ttu-id="b1972-110">Usuários do LINQ to XML para XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="b1972-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
