---
title: Como localizar elementos com um atributo específico-LINQ to XML
description: 'Saiba como localizar todos os elementos que têm um atributo específico (independentemente do valor). Dois métodos são mostrados: um usa XPathEvaluate, o outro usa LINQ to XML consulta.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: fc9f5acdda457eea1790f76695a71afe5fefa070
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551831"
---
# <a name="how-to-find-elements-with-a-specific-attribute-linq-to-xml"></a><span data-ttu-id="db86c-104">Como localizar elementos com um atributo específico (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="db86c-104">How to find elements with a specific attribute (LINQ to XML)</span></span>

<span data-ttu-id="db86c-105">Este artigo mostra como usar o <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> para localizar todos os elementos que têm um atributo específico (independentemente do valor) e como usar LINQ to XML consulta para fazer a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="db86c-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find all elements that have a specific attribute (regardless of value), and how to use LINQ to XML query to do the same thing.</span></span>

## <a name="example-find-all-elements-that-have-the-select-attribute"></a><span data-ttu-id="db86c-106">Exemplo: localizar todos os elementos que têm o `Select` atributo</span><span class="sxs-lookup"><span data-stu-id="db86c-106">Example: Find all elements that have the `Select` attribute</span></span>

<span data-ttu-id="db86c-107">O exemplo a seguir cria uma árvore XML e, em seguida, localiza os elementos que têm o `Select` atributo.</span><span class="sxs-lookup"><span data-stu-id="db86c-107">The following example creates an XML tree and then finds the elements that have the `Select` attribute.</span></span>

<span data-ttu-id="db86c-108">A expressão XPath é `./*[@Select]`.</span><span class="sxs-lookup"><span data-stu-id="db86c-108">The XPath expression is `./*[@Select]`.</span></span>

```csharp
XElement doc = XElement.Parse(
@"<Root>
    <Child1>1</Child1>
    <Child2 Select='true'>2</Child2>
    <Child3>3</Child3>
    <Child4 Select='true'>4</Child4>
    <Child5>5</Child5>
</Root>");

// LINQ to XML query
IEnumerable<XElement> list1 =
    from el in doc.Elements()
    where el.Attribute("Select") != null
    select el;

// XPath expression
IEnumerable<XElement> list2 =
    ((IEnumerable)doc.XPathEvaluate("./*[@Select]")).Cast<XElement>();

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim doc As XElement = _
    <Root>
        <Child1>1</Child1>
        <Child2 Select='true'>2</Child2>
        <Child3>3</Child3>
        <Child4 Select='true'>4</Child4>
        <Child5>5</Child5>
    </Root>

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    From el In doc.Elements() _
    Where el.@Select <> Nothing _
    Select el

' XPath expression
Dim list2 As IEnumerable(Of XElement) = DirectCast(doc.XPathEvaluate _
    ("./*[@Select]"), IEnumerable).Cast(Of XElement)()

If list1.Count() = list2.Count() And _
    list1.Intersect(list2).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If

For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="db86c-109">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="db86c-109">This example produces the following output:</span></span>

```output
Results are identical
<Child2 Select="true">2</Child2>
<Child4 Select="true">4</Child4>
```

## <a name="see-also"></a><span data-ttu-id="db86c-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="db86c-110">See also</span></span>

- [<span data-ttu-id="db86c-111">LINQ to XML para usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db86c-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
