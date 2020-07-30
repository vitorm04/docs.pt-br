---
title: Como escrever uma consulta que localiza elementos com base no contexto (C#)
description: Saiba como escrever uma consulta que localiza elementos com base no contexto. Consulte exemplos de código e exiba recursos adicionais.
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 64f09a41c2c1d01b0be8f776461f9be9df9ecb5f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303186"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="92497-104">Como escrever uma consulta que localiza elementos com base no contexto (C#)</span><span class="sxs-lookup"><span data-stu-id="92497-104">How to write a query that finds elements based on context (C#)</span></span>
<span data-ttu-id="92497-105">Muitas vezes você pode ter que escrever uma consulta que seleciona elementos com base no contexto.</span><span class="sxs-lookup"><span data-stu-id="92497-105">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="92497-106">Você pode querer filtrar com base nos elementos irmãos precedentes ou seguintes.</span><span class="sxs-lookup"><span data-stu-id="92497-106">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="92497-107">Você pode querer filtrar com base nos elementos filhos ou ancestrais.</span><span class="sxs-lookup"><span data-stu-id="92497-107">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="92497-108">Você pode fazer isso escrevendo uma consulta e usando os resultados da consulta na cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="92497-108">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="92497-109">Se você primeiro tiver que testar com zero e, em seguida, testar o valor, é mais conveniente fazer a consulta em uma cláusula `let` e usar os resultados na cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="92497-109">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92497-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92497-110">Example</span></span>  
 <span data-ttu-id="92497-111">O exemplo a seguir seleciona todos os elementos `p` que são imediatamente seguidos por um elemento `ul`.</span><span class="sxs-lookup"><span data-stu-id="92497-111">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants("p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name.LocalName == "ul"  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="92497-112">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="92497-112">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="92497-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92497-113">Example</span></span>  
 <span data-ttu-id="92497-114">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="92497-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="92497-115">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="92497-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
XNamespace ad = "http://www.adatum.com";  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants(ad + "p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name == ad.GetName("ul")  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="92497-116">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="92497-116">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="92497-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="92497-117">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
