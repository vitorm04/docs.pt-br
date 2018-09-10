---
title: Como localizar o irmão imediatamente anterior (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: c610ce4884e0760a03ec77aae4f38cf9c84a797a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507127"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="8b1d3-102">Como localizar o irmão imediatamente anterior (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8b1d3-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="8b1d3-103">Às vezes você deseja encontrar o irmão anterior imediato a um nó.</span><span class="sxs-lookup"><span data-stu-id="8b1d3-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="8b1d3-104">Devido a diferença na semântica de predicados posicionais para os eixos anterior irmãos no XPath ao contrário de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], essa é uma das comparações mais interessantes.</span><span class="sxs-lookup"><span data-stu-id="8b1d3-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b1d3-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b1d3-105">Example</span></span>  
 <span data-ttu-id="8b1d3-106">Neste exemplo, a consulta [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usa o operador <xref:System.Linq.Enumerable.Last%2A> para encontrar o último nó na coleção retornada por <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b1d3-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="8b1d3-107">Por outro lado, a expressão XPath usa um predicado com um valor de 1 para localizar o elemento imediatamente anterior.</span><span class="sxs-lookup"><span data-stu-id="8b1d3-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
    @"<Root>  
    <Child1/>  
    <Child2/>  
    <Child3/>  
    <Child4/>  
</Root>");  
XElement child4 = root.Element("Child4");  
  
// LINQ to XML query  
XElement el1 =  
    child4  
    .ElementsBeforeSelf()  
    .Last();  
  
// XPath expression  
XElement el2 =  
    ((IEnumerable)child4  
                 .XPathEvaluate("preceding-sibling::*[1]"))  
                 .Cast<XElement>()  
                 .First();  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="8b1d3-108">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="8b1d3-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b1d3-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b1d3-109">See Also</span></span>

- [<span data-ttu-id="8b1d3-110">Usuários do LINQ to XML para XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="8b1d3-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
