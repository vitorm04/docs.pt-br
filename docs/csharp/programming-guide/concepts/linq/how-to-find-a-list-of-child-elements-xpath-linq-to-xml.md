---
title: 'Como: Localizar uma lista de elementos filho (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7c589dd8-f680-4cdb-9d6a-78d57e2555e8
ms.openlocfilehash: 8a2ddc13a0a48fbe30ce629527149bacaaab3fd1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593667"
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="0ccaa-102">Como: Localizar uma lista de elementos filho (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0ccaa-102">How to: Find a List of Child Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="0ccaa-103">Este tópico compara o eixo de elementos filho XPath com o eixo [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ccaa-103">This topic compares the XPath child elements axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>  
  
 <span data-ttu-id="0ccaa-104">A expressão XPath é: `./*`</span><span class="sxs-lookup"><span data-stu-id="0ccaa-104">The XPath expression is: `./*`</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ccaa-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ccaa-105">Example</span></span>  
 <span data-ttu-id="0ccaa-106">Este exemplo localiza os elementos filho do elemento `Address`.</span><span class="sxs-lookup"><span data-stu-id="0ccaa-106">This example finds all of the child elements of the `Address` element.</span></span>  
  
 <span data-ttu-id="0ccaa-107">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Várias ordens de compra (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0ccaa-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder").Element("Address");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Elements();  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("./*");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="0ccaa-108">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="0ccaa-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
  