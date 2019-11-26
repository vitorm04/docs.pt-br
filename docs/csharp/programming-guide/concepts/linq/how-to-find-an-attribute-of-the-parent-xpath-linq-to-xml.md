---
title: Como localizar um atributo do pai (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: bfe7554a5c767adde5e7170c8e1ea0537155f6df
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141167"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>Como localizar um atributo do pai (XPath-LINQ to XML) (C#)

Este tópico mostra como navegar para o elemento pai e localizar um atributo deles.

A expressão XPath é:

`../@id`

## <a name="example"></a>Exemplo

Este exemplo localiza primeiro um elemento de `Author` . Localiza no atributo de `id` de elemento pai.

Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: livros (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).

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

Este exemplo gera a seguinte saída:

```output
Results are identical
id="bk101"
```
