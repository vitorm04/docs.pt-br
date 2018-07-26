---
title: Como consultar o LINQ to XML usando o XPath (C#)
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: a02149719afa19350a9baf15c41bd3548daa1344
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959849"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="a796c-102">Como consultar o LINQ to XML usando o XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="a796c-102">How to: Query LINQ to XML Using XPath (C#)</span></span>
<span data-ttu-id="a796c-103">Este tópico apresenta os métodos de extensão que permitem ver uma árvore XML usando o XPath.</span><span class="sxs-lookup"><span data-stu-id="a796c-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="a796c-104">Para obter informações detalhadas sobre como usar esses métodos de extensão, consulte <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a796c-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="a796c-105">A menos que você tenha um motivo específico para muito consulte o XPath em uso, como o uso extensivo de código herdado, usando o XPath com LINQ to XML não é recomendada.</span><span class="sxs-lookup"><span data-stu-id="a796c-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="a796c-106">Consultas de XPath não são executadas tão bem quanto consultas de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a796c-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a796c-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a796c-107">Example</span></span>  
 <span data-ttu-id="a796c-108">O exemplo a seguir cria uma árvore XML pequena e usa <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> para selecionar um conjunto de elementos.</span><span class="sxs-lookup"><span data-stu-id="a796c-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="a796c-109">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="a796c-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a796c-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a796c-110">See Also</span></span>  
 [<span data-ttu-id="a796c-111">Técnicas avançadas de consulta (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a796c-111">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
