---
title: 'Como: Localizar o irmão imediatamente anterior (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: ca3602a24b80d9002a639d9a319a731541aeb2df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61854991"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="94c48-102">Como: Localizar o irmão imediatamente anterior (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94c48-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="94c48-103">Às vezes você deseja encontrar o irmão anterior imediato a um nó.</span><span class="sxs-lookup"><span data-stu-id="94c48-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="94c48-104">Devido a diferença na semântica de predicados posicionais para os eixos anterior irmãos no XPath ao contrário de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], essa é uma das comparações mais interessantes.</span><span class="sxs-lookup"><span data-stu-id="94c48-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94c48-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94c48-105">Example</span></span>  
 <span data-ttu-id="94c48-106">Neste exemplo, a consulta [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usa o operador <xref:System.Linq.Enumerable.Last%2A> para encontrar o último nó na coleção retornada por <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="94c48-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="94c48-107">Por outro lado, a expressão XPath usa um predicado com um valor de 1 para localizar o elemento imediatamente anterior.</span><span class="sxs-lookup"><span data-stu-id="94c48-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```vb  
Dim root As XElement = _   
    <Root>  
        <Child1/>  
        <Child2/>  
        <Child3/>  
        <Child4/>  
    </Root>  
Dim child4 As XElement = root.Element("Child4")  
  
' LINQ to XML query  
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()  
  
' XPath expression  
Dim el2 As XElement = _  
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _  
    IEnumerable).Cast(Of XElement)().First()  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 <span data-ttu-id="94c48-108">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="94c48-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="94c48-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94c48-109">See also</span></span>

- [<span data-ttu-id="94c48-110">LINQ to XML para os usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94c48-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
