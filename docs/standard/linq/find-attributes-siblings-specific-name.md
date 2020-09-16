---
title: Como localizar atributos de irmãos com um nome específico-LINQ to XML
description: 'Saiba como localizar todos os atributos que têm um nome específico e que também pertencem a um irmão do nó de contexto. Dois métodos são mostrados: um usa XPathEvaluate, o outro usa LINQ to XML consulta.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 869c63f26c14bedc8d9911915b8974aa530685fa
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557131"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-linq-to-xml"></a><span data-ttu-id="f9bb2-104">Como localizar atributos de irmãos com um nome específico (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f9bb2-104">How to find attributes of siblings with a specific name (LINQ to XML)</span></span>

<span data-ttu-id="f9bb2-105">Este artigo mostra como usar o <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> para localizar cada atributo que tem um nome específico e que também pertence a um irmão do nó de contexto.</span><span class="sxs-lookup"><span data-stu-id="f9bb2-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find every attribute that has a specific name and that also belongs to a sibling of the context node.</span></span> <span data-ttu-id="f9bb2-106">O artigo também mostra como usar LINQ to XML consulta para fazer a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="f9bb2-106">The article also shows how to use LINQ to XML query to do the same thing.</span></span>

## <a name="example-find-all-sibling-elements-named-book-and-then-find-all-attributes-named-id"></a><span data-ttu-id="f9bb2-107">Exemplo: localizar todos os elementos irmãos chamados `Book` e, em seguida, localizar todos os atributos chamados `id`</span><span class="sxs-lookup"><span data-stu-id="f9bb2-107">Example: Find all sibling elements named `Book`, and then find all attributes named `id`</span></span>

<span data-ttu-id="f9bb2-108">Este exemplo localiza um `Book` elemento no [arquivo XML de exemplo](sample-xml-file-books.md)de documento XML: livros.</span><span class="sxs-lookup"><span data-stu-id="f9bb2-108">This example finds a `Book` element in XML document [Sample XML file: Books](sample-xml-file-books.md).</span></span> <span data-ttu-id="f9bb2-109">Em seguida, ele localiza todos os elementos irmãos chamados `Book` e todos os atributos nomeados `id` desses elementos.</span><span class="sxs-lookup"><span data-stu-id="f9bb2-109">It then finds all sibling elements named `Book`, and all attributes named `id` of those elements.</span></span> <span data-ttu-id="f9bb2-110">O resultado é uma coleção de atributos.</span><span class="sxs-lookup"><span data-stu-id="f9bb2-110">The result is a collection of attributes.</span></span>

<span data-ttu-id="f9bb2-111">A expressão XPath é `../Book/@id`.</span><span class="sxs-lookup"><span data-stu-id="f9bb2-111">The XPath expression is `../Book/@id`.</span></span>

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement book =
    books
    .Root
    .Element("Book");

// LINQ to XML query
IEnumerable<XAttribute> list1 =
    from el in book.Parent.Elements("Book")
    select el.Attribute("id");

// XPath expression
IEnumerable<XAttribute> list2 =
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XAttribute el in list1)
    Console.WriteLine(el);
```

```vb
Dim books as XDocument = XDocument.Load("Books.xml")
Dim book As XElement = books.Root.<Book>(0)

' LINQ to XML query
Dim list1 As IEnumerable(Of XAttribute) = _
    From el In book.Parent.<Book> _
    Select el.Attribute("id")

' XPath expression
Dim list2 As IEnumerable(Of XAttribute) = DirectCast(book. _
    XPathEvaluate("../Book/@id"), IEnumerable).Cast(Of XAttribute)()

If list1.Count() = list2.Count() And _
        (list1.Intersect(list2)).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If

For Each el As XAttribute In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="f9bb2-112">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="f9bb2-112">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
id="bk102"
```

## <a name="see-also"></a><span data-ttu-id="f9bb2-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="f9bb2-113">See also</span></span>

- [<span data-ttu-id="f9bb2-114">LINQ to XML para usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9bb2-114">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
