---
title: Como localizar o LINQ to XML irmão precedentes imediatos
description: 'Saiba como localizar o irmão que precede imediatamente um nó. Dois métodos são mostrados: um usa XPathEvaluate, o outro usa LINQ to XML consulta.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: ca3f7bea150ebcfab100475ceb13b1624c91094f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551943"
---
# <a name="how-to-find-the-immediate-preceding-sibling-linq-to-xml"></a><span data-ttu-id="f83d8-104">Como localizar o irmão precedentes imediatos (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f83d8-104">How to find the immediate preceding sibling (LINQ to XML)</span></span>

<span data-ttu-id="f83d8-105">Este artigo mostra como usar <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> o para localizar o irmão que precede imediatamente um nó e como usar LINQ to XML consulta para fazer a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="f83d8-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find the sibling that immediately precedes a node, and how to use LINQ to XML query to do the same thing.</span></span> <span data-ttu-id="f83d8-106">Devido à diferença na semântica de predicados de posição para os eixos irmãos precedentes em XPath em oposição a LINQ to XML, essa é uma das comparações mais interessantes.</span><span class="sxs-lookup"><span data-stu-id="f83d8-106">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to LINQ to XML, this is one of the more interesting comparisons.</span></span>

## <a name="example-find-the-next-to-last-element"></a><span data-ttu-id="f83d8-107">Exemplo: encontrar o próximo ao último elemento</span><span class="sxs-lookup"><span data-stu-id="f83d8-107">Example: Find the next to last element</span></span>

<span data-ttu-id="f83d8-108">Neste exemplo, a consulta LINQ to XML usa o <xref:System.Linq.Enumerable.Last%2A> operador para localizar o último nó na coleção retornada por <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> .</span><span class="sxs-lookup"><span data-stu-id="f83d8-108">In this example, the LINQ to XML query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="f83d8-109">Por outro lado, a expressão XPath usa um predicado com um valor de 1 para localizar o elemento imediatamente anterior.</span><span class="sxs-lookup"><span data-stu-id="f83d8-109">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>

```csharp
XElement root = XElement.Parse(
    @"<Root>
    <Child1/>
    <Child2/>
    <Child3/>
    <Child4/>
</Root>");
XElement child4 = root.Element("Child4");

// LINQ to XML query
XElement el1 =
    child4
    .ElementsBeforeSelf()
    .Last();

// XPath expression
XElement el2 =
    ((IEnumerable)child4
                 .XPathEvaluate("preceding-sibling::*[1]"))
                 .Cast<XElement>()
                 .First();

if (el1 == el2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(el1);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1/>
        <Child2/>
        <Child3/>
        <Child4/>
    </Root>
Dim child4 As XElement = root.Element("Child4")

' LINQ to XML query
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()

' XPath expression
Dim el2 As XElement = _
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _
    IEnumerable).Cast(Of XElement)().First()

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1)
```

<span data-ttu-id="f83d8-110">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="f83d8-110">This example produces the following output:</span></span>

```output
Results are identical
<Child3 />
```

## <a name="see-also"></a><span data-ttu-id="f83d8-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="f83d8-111">See also</span></span>

- [<span data-ttu-id="f83d8-112">LINQ to XML para usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f83d8-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
