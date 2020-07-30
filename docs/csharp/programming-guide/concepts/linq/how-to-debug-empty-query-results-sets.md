---
title: Como depurar conjuntos de resultados de consulta vazios (C#)
description: Saiba como depurar conjuntos de resultados de consulta vazios. Esses conjuntos podem ocorrer se um desenvolvedor escrever uma consulta como se o XML não estivesse em um namespace.
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: ad6d39697e5a59fe23ca700ceeb2a9860d05bb94
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302900"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a><span data-ttu-id="affec-104">Como depurar conjuntos de resultados de consulta vazios (C#)</span><span class="sxs-lookup"><span data-stu-id="affec-104">How to debug empty query results sets (C#)</span></span>
<span data-ttu-id="affec-105">Um dos problemas mais comuns para o consulte árvores XML é que se a árvore tem um namespace XML padrão, o desenvolvedor escreve às vezes a consulta como se o XML não estar em um namespace.</span><span class="sxs-lookup"><span data-stu-id="affec-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="affec-106">Definir primeiro exemplos neste tópico mostra uma maneira comum que XML em um namespace padrão é carregado, e deduzido de modo inadequado.</span><span class="sxs-lookup"><span data-stu-id="affec-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="affec-107">O segundo conjunto de exemplos a seguir mostra as correções necessárias para que você possa ver XML em um namespace.</span><span class="sxs-lookup"><span data-stu-id="affec-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="affec-108">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="affec-108">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="affec-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="affec-109">Example</span></span>  
 <span data-ttu-id="affec-110">Este exemplo mostra como criar XML em um namespace, e uma consulta que retorna um conjunto de resultados vazia.</span><span class="sxs-lookup"><span data-stu-id="affec-110">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
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
  
 <span data-ttu-id="affec-111">Este exemplo gerencia o resultado seguinte:</span><span class="sxs-lookup"><span data-stu-id="affec-111">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="affec-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="affec-112">Example</span></span>  
 <span data-ttu-id="affec-113">Este exemplo mostra como criar XML em um namespace, e uma consulta que é codificado corretamente.</span><span class="sxs-lookup"><span data-stu-id="affec-113">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="affec-114">A solução é declarar e inicializar um objeto de <xref:System.Xml.Linq.XNamespace> e usá-lo para especificar <xref:System.Xml.Linq.XName> objetos.</span><span class="sxs-lookup"><span data-stu-id="affec-114">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="affec-115">Nesse caso, o argumento para o método de <xref:System.Xml.Linq.XContainer.Elements%2A> é um objeto de <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="affec-115">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
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
  
 <span data-ttu-id="affec-116">Este exemplo gerencia o resultado seguinte:</span><span class="sxs-lookup"><span data-stu-id="affec-116">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
