---
title: Como localizar nós irmãos (XPath-LINQ to XML) (C#)
description: Este exemplo C# compara XPath com LINQ to XML para saber como localizar todos os irmãos de um nó que têm um nome específico.
ms.date: 07/20/2015
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: 2936fc4ad088580a9644f79f1797e679fe877e00
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105212"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a><span data-ttu-id="d3ad5-103">Como localizar nós irmãos (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d3ad5-103">How to find sibling nodes (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="d3ad5-104">Você pode desejar localizar todos os seus irmãos de um nó que têm um nome específico.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-104">You might want to find all siblings of a node that have a specific name.</span></span> <span data-ttu-id="d3ad5-105">A coleção resultante pode incluir o nó de contexto se o nó de contexto também tem o nome específico.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-105">The resulting collection might include the context node if the context node also has the specific name.</span></span>  
  
 <span data-ttu-id="d3ad5-106">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="d3ad5-106">The XPath expression is:</span></span>  
  
 `../Book`  
  
## <a name="example"></a><span data-ttu-id="d3ad5-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3ad5-107">Example</span></span>  
 <span data-ttu-id="d3ad5-108">Este exemplo localiza primeiro um elemento de `Book` , e localiza em todos os elementos irmãos nomeados `Book`.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-108">This example first finds a `Book` element, and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="d3ad5-109">A coleção resultante inclui o nó de contexto.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-109">The resulting collection includes the context node.</span></span>  
  
 <span data-ttu-id="d3ad5-110">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: livros (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d3ad5-110">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="d3ad5-111">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="d3ad5-111">This example produces the following output:</span></span>  
  
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
