---
title: Como consultar o LINQ to XML usando o XPath (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1cb47b5b4b85536feeb5006fe6dd31580ca651b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="30a98-102">Como consultar o LINQ to XML usando o XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="30a98-102">How to: Query LINQ to XML Using XPath (C#)</span></span>
<span data-ttu-id="30a98-103">Este tópico apresenta os métodos de extensão que permitem ver uma árvore XML usando o XPath.</span><span class="sxs-lookup"><span data-stu-id="30a98-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="30a98-104">Para obter informações detalhadas sobre como usar esses métodos de extensão, consulte <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30a98-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="30a98-105">A menos que você tenha um motivo específico para muito consulte o XPath em uso, como o uso extensivo de código herdado, usando o XPath com LINQ to XML não é recomendada.</span><span class="sxs-lookup"><span data-stu-id="30a98-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="30a98-106">Consultas de XPath não são executadas tão bem quanto consultas de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="30a98-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30a98-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30a98-107">Example</span></span>  
 <span data-ttu-id="30a98-108">O exemplo a seguir cria uma árvore XML pequena e usa <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> para selecionar um conjunto de elementos.</span><span class="sxs-lookup"><span data-stu-id="30a98-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
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
  
 <span data-ttu-id="30a98-109">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="30a98-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="30a98-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30a98-110">See Also</span></span>  
 [<span data-ttu-id="30a98-111">Técnicas avançadas de consulta (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="30a98-111">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
