---
title: Como depurar conjuntos de resultados de consultas vazios (C#)
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 4760b1e5274634954bd5fe4b3880fd4415af2510
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677845"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a><span data-ttu-id="b0fd3-102">Como depurar conjuntos de resultados de consultas vazios (C#)</span><span class="sxs-lookup"><span data-stu-id="b0fd3-102">How to: Debug Empty Query Results Sets (C#)</span></span>
<span data-ttu-id="b0fd3-103">Um dos problemas mais comuns para o consulte árvores XML é que se a árvore tem um namespace XML padrão, o desenvolvedor escreve às vezes a consulta como se o XML não estar em um namespace.</span><span class="sxs-lookup"><span data-stu-id="b0fd3-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="b0fd3-104">Definir primeiro exemplos neste tópico mostra uma maneira comum que XML em um namespace padrão é carregado, e deduzido de modo inadequado.</span><span class="sxs-lookup"><span data-stu-id="b0fd3-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="b0fd3-105">O segundo conjunto de exemplos a seguir mostra as correções necessárias para que você possa ver XML em um namespace.</span><span class="sxs-lookup"><span data-stu-id="b0fd3-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="b0fd3-106">Para obter mais informações, consulte [Trabalhando com namespaces XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="b0fd3-106">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0fd3-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b0fd3-107">Example</span></span>  
 <span data-ttu-id="b0fd3-108">Este exemplo mostra como criar XML em um namespace, e uma consulta que retorna um conjunto de resultados vazia.</span><span class="sxs-lookup"><span data-stu-id="b0fd3-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 <span data-ttu-id="b0fd3-109">Este exemplo gerencia o resultado seguinte:</span><span class="sxs-lookup"><span data-stu-id="b0fd3-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="b0fd3-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b0fd3-110">Example</span></span>  
 <span data-ttu-id="b0fd3-111">Este exemplo mostra como criar XML em um namespace, e uma consulta que é codificado corretamente.</span><span class="sxs-lookup"><span data-stu-id="b0fd3-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="b0fd3-112">A solução é declarar e inicializar um objeto de <xref:System.Xml.Linq.XNamespace> e usá-lo para especificar <xref:System.Xml.Linq.XName> objetos.</span><span class="sxs-lookup"><span data-stu-id="b0fd3-112">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="b0fd3-113">Nesse caso, o argumento para o método de <xref:System.Xml.Linq.XElement.Elements%2A> é um objeto de <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="b0fd3-113">In this case, the argument to the <xref:System.Xml.Linq.XElement.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 <span data-ttu-id="b0fd3-114">Este exemplo gerencia o resultado seguinte:</span><span class="sxs-lookup"><span data-stu-id="b0fd3-114">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0fd3-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0fd3-115">See Also</span></span>

- [<span data-ttu-id="b0fd3-116">Consultas básicas (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b0fd3-116">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
