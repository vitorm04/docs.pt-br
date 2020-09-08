---
title: Como escrever uma consulta que localiza elementos com base em LINQ to XML de contexto
description: Escrever uma consulta que seleciona elementos com base no contexto; por exemplo, filtre os resultados com base nos elementos irmãos anteriores ou seguintes.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: df4f6bcd52331a7b6c81cf816260df4355ebf987
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551870"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-linq-to-xml"></a><span data-ttu-id="154eb-103">Como escrever uma consulta que localiza elementos com base no contexto (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="154eb-103">How to write a query that finds elements based on context (LINQ to XML)</span></span>

<span data-ttu-id="154eb-104">Muitas vezes você pode ter que escrever uma consulta que seleciona elementos com base no contexto.</span><span class="sxs-lookup"><span data-stu-id="154eb-104">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="154eb-105">Por exemplo, você pode querer filtrar com base nos elementos irmãos precedentes ou seguintes, ou em elementos filho ou ancestral.</span><span class="sxs-lookup"><span data-stu-id="154eb-105">For example, you might want to filter based on preceding or following sibling elements, or on child or ancestor elements.</span></span>

<span data-ttu-id="154eb-106">Você pode fazer isso escrevendo uma consulta e usando os resultados da consulta na cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="154eb-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="154eb-107">Se você precisa primeiro testar em relação a NULL e, em seguida, testar o valor, é mais conveniente fazer a consulta em uma `let` cláusula e, em seguida, usar os resultados na `where` cláusula.</span><span class="sxs-lookup"><span data-stu-id="154eb-107">If you have to first test against null, and then test the value, it's more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>

## <a name="example-select-p-elements-that-are-immediately-followed-by-a-ul-element"></a><span data-ttu-id="154eb-108">Exemplo: selecionar `p` elementos que são seguidos imediatamente por um `ul` elemento</span><span class="sxs-lookup"><span data-stu-id="154eb-108">Example: Select `p` elements that are immediately followed by a `ul` element</span></span>

<span data-ttu-id="154eb-109">O exemplo a seguir seleciona todos os elementos `p` que são imediatamente seguidos por um elemento `ul`.</span><span class="sxs-lookup"><span data-stu-id="154eb-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>

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

```vb
Dim doc As XElement = _
    <Root>
        <p id='1'/>
        <ul>abc</ul>
        <Child>
            <p id='2'/>
            <notul/>
            <p id='3'/>
            <ul>def</ul>
            <p id='4'/>
        </Child>
        <Child>
            <p id='5'/>
            <notul/>
            <p id='6'/>
            <ul>abc</ul>
            <p id='7'/>
        </Child>
    </Root>

Dim items As IEnumerable(Of XElement) = _
    From e In doc...<p> _
    Let z = e.ElementsAfterSelf().FirstOrDefault() _
    Where z IsNot Nothing AndAlso z.Name.LocalName = "ul" _
    Select e

For Each e As XElement In items
    Console.WriteLine("id = {0}", e.@<id>)
Next
```

<span data-ttu-id="154eb-110">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="154eb-110">This example produces the following output:</span></span>

```output
id = 1
id = 3
id = 6
```

## <a name="example-in-a-namespace-select-p-elements-that-are-immediately-followed-by-a-ul-element"></a><span data-ttu-id="154eb-111">Exemplo: em um namespace, selecione os `p` elementos que são seguidos imediatamente por um `ul` elemento</span><span class="sxs-lookup"><span data-stu-id="154eb-111">Example: In a namespace select `p` elements that are immediately followed by a `ul` element</span></span>

<span data-ttu-id="154eb-112">O exemplo a seguir mostra a mesma consulta como acima, mas para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="154eb-112">The following example shows the same query as above, but for XML that's in a namespace.</span></span> <span data-ttu-id="154eb-113">Para obter mais informações, consulte [visão geral de namespaces](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="154eb-113">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

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

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim doc As XElement = _
            <Root>
                <p id='1'/>
                <ul>abc</ul>
                <Child>
                    <p id='2'/>
                    <notul/>
                    <p id='3'/>
                    <ul>def</ul>
                    <p id='4'/>
                </Child>
                <Child>
                    <p id='5'/>
                    <notul/>
                    <p id='6'/>
                    <ul>abc</ul>
                    <p id='7'/>
                </Child>
            </Root>

        Dim items As IEnumerable(Of XElement) = _
            From e In doc...<p> _
            Let z = e.ElementsAfterSelf().FirstOrDefault() _
            Where z IsNot Nothing AndAlso z.Name = GetXmlNamespace().GetName("ul") _
            Select e

        For Each e As XElement In items
            Console.WriteLine("id = {0}", e.@<id>)
        Next
    End Sub
End Module
```

<span data-ttu-id="154eb-114">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="154eb-114">This example produces the following output:</span></span>

```output
id = 1
id = 3
id = 6
```

## <a name="see-also"></a><span data-ttu-id="154eb-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="154eb-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [<span data-ttu-id="154eb-116">Consultas básicas (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="154eb-116">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
