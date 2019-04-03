---
title: 'Como: Consulta LINQ to XML usando XPath (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: cff0b5f6e4bb3c64522dc13a44dd79d7c172c1b5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843058"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a><span data-ttu-id="9a870-102">Como: Consulta LINQ to XML usando XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a870-102">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>
<span data-ttu-id="9a870-103">Este tópico apresenta os métodos de extensão que permitem ver uma árvore XML usando o XPath.</span><span class="sxs-lookup"><span data-stu-id="9a870-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="9a870-104">Para obter informações detalhadas sobre como usar esses métodos de extensão, consulte <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9a870-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="9a870-105">A menos que você tenha um motivo específico para muito consulte o XPath em uso, como o uso extensivo de código herdado, usando o XPath com LINQ to XML não é recomendada.</span><span class="sxs-lookup"><span data-stu-id="9a870-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="9a870-106">Consultas de XPath não são executadas tão bem quanto consultas de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a870-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a870-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a870-107">Example</span></span>  
 <span data-ttu-id="9a870-108">O exemplo a seguir cria uma árvore XML pequena e usa <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> para selecionar um conjunto de elementos.</span><span class="sxs-lookup"><span data-stu-id="9a870-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child1>2</Child1>  
        <Child1>3</Child1>  
        <Child2>4</Child2>  
        <Child2>5</Child2>  
        <Child2>6</Child2>  
    </Root>  
  
Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")  
For Each el As XElement In list  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="9a870-109">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9a870-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a870-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a870-110">See also</span></span>

- [<span data-ttu-id="9a870-111">Técnicas avançadas de consulta (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a870-111">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
