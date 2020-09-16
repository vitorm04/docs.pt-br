---
title: Como depurar conjuntos de resultados de consulta vazios-LINQ to XML
description: Quando você consulta uma árvore XML em um namespace padrão, evite o erro comum de consultar como se o XML não estivesse em um namespace.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 8fc6b1a80b183f8e2b0f80fc554a12c2657dcb55
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557138"
---
# <a name="how-to-debug-empty-query-results-sets-linq-to-xml"></a><span data-ttu-id="de672-103">Como depurar conjuntos de resultados de consulta vazios (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="de672-103">How to debug empty query results sets (LINQ to XML)</span></span>

<span data-ttu-id="de672-104">Um dos problemas mais comuns para o consulte árvores XML é que se a árvore tem um namespace XML padrão, o desenvolvedor escreve às vezes a consulta como se o XML não estar em um namespace.</span><span class="sxs-lookup"><span data-stu-id="de672-104">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>

<span data-ttu-id="de672-105">O primeiro conjunto de exemplos neste artigo mostra uma maneira típica de o XML em um namespace padrão ser carregado e, em seguida, consultado de forma inadequada.</span><span class="sxs-lookup"><span data-stu-id="de672-105">The first set of examples in this article shows a typical way that XML in a default namespace is loaded, and then queried improperly.</span></span>

<span data-ttu-id="de672-106">O segundo conjunto de exemplos a seguir mostra as correções necessárias para que você possa ver XML em um namespace.</span><span class="sxs-lookup"><span data-stu-id="de672-106">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>

<span data-ttu-id="de672-107">Para obter mais informações, consulte [visão geral de namespaces](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="de672-107">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

## <a name="example-an-improper-query-on-xml-in-a-namespace"></a><span data-ttu-id="de672-108">Exemplo: uma consulta inadequada em XML em um namespace</span><span class="sxs-lookup"><span data-stu-id="de672-108">Example: An improper query on XML in a namespace</span></span>

<span data-ttu-id="de672-109">Este exemplo mostra como criar XML em um namespace, e uma consulta que retorna um conjunto de resultados vazia.</span><span class="sxs-lookup"><span data-stu-id="de672-109">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>

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

```vb
Dim root As XElement = _
    <Root xmlns='http://www.adventure-works.com'>
        <Child>1</Child>
        <Child>2</Child>
        <Child>3</Child>
        <AnotherChild>4</AnotherChild>
        <AnotherChild>5</AnotherChild>
        <AnotherChild>6</AnotherChild>
    </Root>
Dim c1 As IEnumerable(Of XElement) = _
        From el In root.<Child> _
        Select el
Console.WriteLine("Result set follows:")
For Each el As XElement In c1
    Console.WriteLine(el.Value)
Next
Console.WriteLine("End of result set")
```

<span data-ttu-id="de672-110">O exemplo produz esse resultado:</span><span class="sxs-lookup"><span data-stu-id="de672-110">The example produces this result:</span></span>

```output
Result set follows:
End of result set
```

## <a name="example-a-proper-query-on-xml-in-a-namespace"></a><span data-ttu-id="de672-111">Exemplo: uma consulta apropriada em XML em um namespace</span><span class="sxs-lookup"><span data-stu-id="de672-111">Example: A proper query on XML in a namespace</span></span>

<span data-ttu-id="de672-112">Este exemplo mostra a criação de XML em um namespace e uma consulta que é codificada corretamente.</span><span class="sxs-lookup"><span data-stu-id="de672-112">This example shows creation of XML in a namespace, and a query that's  coded properly.</span></span>

<span data-ttu-id="de672-113">A solução é declarar e inicializar um objeto de <xref:System.Xml.Linq.XNamespace> e usá-lo para especificar <xref:System.Xml.Linq.XName> objetos.</span><span class="sxs-lookup"><span data-stu-id="de672-113">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="de672-114">Nesse caso, o argumento para o método de <xref:System.Xml.Linq.XContainer.Elements%2A> é um objeto de <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="de672-114">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>

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

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="de672-115">O exemplo produz esse resultado:</span><span class="sxs-lookup"><span data-stu-id="de672-115">The example produces this result:</span></span>

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="de672-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="de672-116">See also</span></span>

- [<span data-ttu-id="de672-117">Consultas básicas (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de672-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](./find-element-specific-attribute.md)
