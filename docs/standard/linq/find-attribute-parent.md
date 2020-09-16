---
title: Como localizar um atributo do LINQ to XML pai
description: 'Saiba como navegar para um elemento e localizar um atributo de seu pai. Dois métodos são mostrados: um usa XPathEvaluate, o outro usa LINQ to XML consulta.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 6d5d1ce768f91aa6e32bf09668bad66f3c4f2334
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556356"
---
# <a name="how-to-find-an-attribute-of-the-parent-linq-to-xml"></a><span data-ttu-id="7e131-104">Como localizar um atributo do pai (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7e131-104">How to find an attribute of the parent (LINQ to XML)</span></span>

<span data-ttu-id="7e131-105">Este artigo mostra como usar <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> o para localizar um atributo de um elemento pai e como usar LINQ to XML consulta para fazer a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="7e131-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find an attribute of a parent element, and how to use LINQ to XML query to do the same thing.</span></span>

## <a name="example-find-the-author-element-and-then-find-the-id-attribute-of-its-parent"></a><span data-ttu-id="7e131-106">Exemplo: Localize o `Author` elemento e, em seguida, localize o `id` atributo de seu pai</span><span class="sxs-lookup"><span data-stu-id="7e131-106">Example: Find the `Author` element, and then find the `id` attribute of its parent</span></span>

<span data-ttu-id="7e131-107">Este exemplo primeiro localiza um `Author` elemento no [arquivo XML de exemplo](sample-xml-file-books.md)de documento XML: livros e, em seguida, localiza o `id` atributo de seu elemento pai.</span><span class="sxs-lookup"><span data-stu-id="7e131-107">This example first finds an `Author` element in XML document [Sample XML file: Books](sample-xml-file-books.md), and then finds the `id` attribute of its parent element.</span></span>

<span data-ttu-id="7e131-108">A expressão XPath é `../@id`.</span><span class="sxs-lookup"><span data-stu-id="7e131-108">The XPath expression is `../@id`.</span></span>

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement author =
    books
    .Root
    .Element("Book")
    .Element("Author");

// LINQ to XML query
XAttribute att1 =
    author
    .Parent
    .Attribute("id");

// XPath expression
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();

if (att1 == att2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(att1);
```

```vb
Dim books As XDocument = XDocument.Load("Books.xml")
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()

' LINQ to XML query
Dim att1 As XAttribute = author.Parent.Attribute("id")

' XPath expression
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _
    IEnumerable).Cast(Of XAttribute)().First()

If att1 Is att2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(att1)
```

<span data-ttu-id="7e131-109">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="7e131-109">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
```

## <a name="see-also"></a><span data-ttu-id="7e131-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="7e131-110">See also</span></span>

- [<span data-ttu-id="7e131-111">LINQ to XML para usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e131-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
