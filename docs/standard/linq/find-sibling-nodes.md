---
title: Como encontrar nós irmãos-LINQ to XML
description: 'Saiba como localizar todos os irmãos de um nó que têm um nome específico. Dois métodos são mostrados: um usa XPathSelectElements, o outro usa LINQ to XML consulta.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: 56833ef3758a6d8af1eb6f0a103b85ad967c9aad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555907"
---
# <a name="how-to-find-sibling-nodes-linq-to-xml"></a><span data-ttu-id="0c70c-104">Como localizar nós irmãos (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="0c70c-104">How to find sibling nodes (LINQ to XML)</span></span>

<span data-ttu-id="0c70c-105">Este artigo mostra como usar o <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> para localizar todos os irmãos de um nó que têm um nome específico e como usar LINQ to XML consulta para fazer a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="0c70c-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to find all siblings of a node that have a specific name, and how to use LINQ to XML query to do the same thing.</span></span>

> [!NOTE]
> <span data-ttu-id="0c70c-106">A coleção resultante incluirá o nó de contexto se ele também tiver o nome específico.</span><span class="sxs-lookup"><span data-stu-id="0c70c-106">The resulting collection includes the context node if it also has the specific name.</span></span>

## <a name="example-find-an-element-named-book-and-all-sibling-elements-named-book"></a><span data-ttu-id="0c70c-107">Exemplo: localizar um elemento chamado `Book` e todos os elementos irmãos chamados `Book`</span><span class="sxs-lookup"><span data-stu-id="0c70c-107">Example: Find an element named `Book`, and all sibling elements named `Book`</span></span>

<span data-ttu-id="0c70c-108">Este exemplo primeiro localiza um `Book` elemento no [arquivo XML de exemplo](sample-xml-file-books.md)de documento XML: livros e localiza todos os elementos irmãos chamados `Book` .</span><span class="sxs-lookup"><span data-stu-id="0c70c-108">This example first finds a `Book` element in XML document [Sample XML file: Books](sample-xml-file-books.md), and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="0c70c-109">A coleção resultante inclui o nó de contexto.</span><span class="sxs-lookup"><span data-stu-id="0c70c-109">The resulting collection includes the context node.</span></span>

<span data-ttu-id="0c70c-110">A expressão XPath é `../Book`</span><span class="sxs-lookup"><span data-stu-id="0c70c-110">The XPath expression is `../Book`</span></span>

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement book =
    books
    .Root
    .Elements("Book")
    .Skip(1)
    .First();

// LINQ to XML query
IEnumerable<XElement> list1 =
    book
    .Parent
    .Elements("Book");

// XPath expression
IEnumerable<XElement> list2 = book.XPathSelectElements("../Book");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim books As XDocument = XDocument.Load("Books.xml")
Dim book As XElement = books.Root.<Book>.Skip(1).First()

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = book.Parent.<Book>

' XPath expression
Dim list2 As IEnumerable(Of XElement) = book.XPathSelectElements("../Book")

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

<span data-ttu-id="0c70c-111">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="0c70c-111">This example produces the following output:</span></span>

```output
Results are identical
<Book id="bk101">
  <Author>Garghentini, Davide</Author>
  <Title>XML Developer's Guide</Title>
  <Genre>Computer</Genre>
  <Price>44.95</Price>
  <PublishDate>2000-10-01</PublishDate>
  <Description>An in-depth look at creating applications
      with XML.</Description>
</Book>
<Book id="bk102">
  <Author>Garcia, Debra</Author>
  <Title>Midnight Rain</Title>
  <Genre>Fantasy</Genre>
  <Price>5.95</Price>
  <PublishDate>2000-12-16</PublishDate>
  <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>
</Book>
```

## <a name="see-also"></a><span data-ttu-id="0c70c-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="0c70c-112">See also</span></span>

- [<span data-ttu-id="0c70c-113">LINQ to XML para usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c70c-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
