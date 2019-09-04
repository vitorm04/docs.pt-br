---
title: Escopo de namespace padrão em C#
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 7615351f6e5f8b18bd6466a83d54aa65a6c99b50
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253048"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="52339-102">Escopo de namespace padrão em C\#</span><span class="sxs-lookup"><span data-stu-id="52339-102">Scope of Default Namespaces in C\#</span></span>
<span data-ttu-id="52339-103">Namespaces padrões como representadas na árvore XML não estiver no escopo para consultas.</span><span class="sxs-lookup"><span data-stu-id="52339-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="52339-104">Se você tiver XML que é em um namespace padrão, você ainda deve declarar uma variável de <xref:System.Xml.Linq.XNamespace> , e combina-o com o nome local para fazer um nome qualificado para ser usado na consulta.</span><span class="sxs-lookup"><span data-stu-id="52339-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="52339-105">Um dos problemas mais comuns para o consulte árvores XML é que se a árvore tem um namespace XML padrão, o desenvolvedor escreve às vezes a consulta como se o XML não estar em um namespace.</span><span class="sxs-lookup"><span data-stu-id="52339-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="52339-106">Definir primeiro exemplos neste tópico mostra uma maneira comum que XML em um namespace padrão é carregado, mas é visto de modo inadequado.</span><span class="sxs-lookup"><span data-stu-id="52339-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="52339-107">O segundo conjunto de exemplos a seguir mostra as correções necessárias para que você possa ver XML em um namespace.</span><span class="sxs-lookup"><span data-stu-id="52339-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52339-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52339-108">Example</span></span>  
 <span data-ttu-id="52339-109">Este exemplo mostra como criar XML em um namespace, e uma consulta que retorna um conjunto de resultados vazia.</span><span class="sxs-lookup"><span data-stu-id="52339-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="52339-110">Código</span><span class="sxs-lookup"><span data-stu-id="52339-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="52339-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="52339-111">Comments</span></span>  
 <span data-ttu-id="52339-112">Este exemplo gerencia o resultado seguinte:</span><span class="sxs-lookup"><span data-stu-id="52339-112">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="52339-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52339-113">Example</span></span>  
 <span data-ttu-id="52339-114">Este exemplo mostra como criar XML em um namespace, e uma consulta que é codificado corretamente.</span><span class="sxs-lookup"><span data-stu-id="52339-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="52339-115">Em contraste com incorretamente codificado o exemplo anterior, a abordagem correta para usar C# é declarar e inicializar um objeto de <xref:System.Xml.Linq.XNamespace> , e usá-lo para especificar <xref:System.Xml.Linq.XName> objetos.</span><span class="sxs-lookup"><span data-stu-id="52339-115">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="52339-116">Nesse caso, o argumento para o método de <xref:System.Xml.Linq.XContainer.Elements%2A> é um objeto de <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="52339-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="52339-117">Código</span><span class="sxs-lookup"><span data-stu-id="52339-117">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="52339-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="52339-118">Comments</span></span>  
 <span data-ttu-id="52339-119">Este exemplo gerencia o resultado seguinte:</span><span class="sxs-lookup"><span data-stu-id="52339-119">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="52339-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52339-120">See also</span></span>

- [<span data-ttu-id="52339-121">Visão geral sobre namespaces (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="52339-121">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
