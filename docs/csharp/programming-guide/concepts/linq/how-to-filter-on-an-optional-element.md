---
title: 'Como: Filtrar em um elemento opcional (C#)'
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: 0f8e17d99085ad04ed76b83bce806418ca6d60cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253826"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="bc515-102">Como: Filtrar em um elemento opcional (C#)</span><span class="sxs-lookup"><span data-stu-id="bc515-102">How to: Filter on an Optional Element (C#)</span></span>
<span data-ttu-id="bc515-103">Às vezes você deseja filtrar um elemento mesmo que você não tenha certeza ele existe em seu documento XML.</span><span class="sxs-lookup"><span data-stu-id="bc515-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="bc515-104">A pesquisa deve ser executada de modo que se o elemento específico não tem o elemento filho, você não dispare uma exceção de referência nula filtragem para ele.</span><span class="sxs-lookup"><span data-stu-id="bc515-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="bc515-105">No exemplo a seguir, o elemento de `Child5` não tiver um elemento filho de `Type` , mas a consulta ainda executa corretamente.</span><span class="sxs-lookup"><span data-stu-id="bc515-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc515-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc515-106">Example</span></span>  
 <span data-ttu-id="bc515-107">Este exemplo usa o método de extensão de <xref:System.Xml.Linq.Extensions.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="bc515-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
var cList =  
    from typeElement in root.Elements().Elements("Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element("Text");  
foreach(string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="bc515-108">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="bc515-108">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="bc515-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc515-109">Example</span></span>  
 <span data-ttu-id="bc515-110">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="bc515-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="bc515-111">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bc515-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
XNamespace ad = "http://www.adatum.com";  
var cList =  
    from typeElement in root.Elements().Elements(ad + "Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element(ad + "Text");  
foreach (string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="bc515-112">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="bc515-112">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc515-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc515-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bc515-114">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="bc515-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="bc515-115">Operações de projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="bc515-115">Projection Operations (C#)</span></span>](./projection-operations.md)
