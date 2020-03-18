---
title: Como encontrar um atributo do pai (XPath-LINQ para XML) (C#)
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: bfe7554a5c767adde5e7170c8e1ea0537155f6df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141167"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="de523-102">Como encontrar um atributo do pai (XPath-LINQ para XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="de523-102">How to find an attribute of the parent (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="de523-103">Este tópico mostra como navegar para o elemento pai e localizar um atributo deles.</span><span class="sxs-lookup"><span data-stu-id="de523-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>

<span data-ttu-id="de523-104">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="de523-104">The XPath expression is:</span></span>

`../@id`

## <a name="example"></a><span data-ttu-id="de523-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de523-105">Example</span></span>

<span data-ttu-id="de523-106">Este exemplo localiza primeiro um elemento de `Author` .</span><span class="sxs-lookup"><span data-stu-id="de523-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="de523-107">Localiza no atributo de `id` de elemento pai.</span><span class="sxs-lookup"><span data-stu-id="de523-107">It then finds the `id` attribute of the parent element.</span></span>

<span data-ttu-id="de523-108">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: livros (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="de523-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>

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

<span data-ttu-id="de523-109">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="de523-109">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
```
