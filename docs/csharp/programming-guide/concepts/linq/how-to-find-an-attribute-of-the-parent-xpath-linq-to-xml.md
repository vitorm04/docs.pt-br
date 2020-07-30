---
title: Como encontrar um atributo do pai (XPath-LINQ to XML) (C#)
description: Saiba como localizar um atributo do elemento pai. Consulte um exemplo de código que usa um documento XML de exemplo.
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 03344bb66f617970d9598c91366eb7d69514397a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303290"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="a2309-104">Como encontrar um atributo do pai (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a2309-104">How to find an attribute of the parent (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="a2309-105">Este tópico mostra como navegar para o elemento pai e localizar um atributo deles.</span><span class="sxs-lookup"><span data-stu-id="a2309-105">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>

<span data-ttu-id="a2309-106">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="a2309-106">The XPath expression is:</span></span>

`../@id`

## <a name="example"></a><span data-ttu-id="a2309-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2309-107">Example</span></span>

<span data-ttu-id="a2309-108">Este exemplo localiza primeiro um elemento de `Author` .</span><span class="sxs-lookup"><span data-stu-id="a2309-108">This example first finds an `Author` element.</span></span> <span data-ttu-id="a2309-109">Localiza no atributo de `id` de elemento pai.</span><span class="sxs-lookup"><span data-stu-id="a2309-109">It then finds the `id` attribute of the parent element.</span></span>

<span data-ttu-id="a2309-110">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: livros (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a2309-110">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>

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

<span data-ttu-id="a2309-111">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="a2309-111">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
```
