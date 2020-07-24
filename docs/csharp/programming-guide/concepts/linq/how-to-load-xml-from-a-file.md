---
title: Como carregar XML de um arquivo (C#)
description: Saiba como carregar XML de um URI usando o método XElement. Load em C#. Este exemplo carrega o arquivo XML e imprime a árvore XML no console.
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: 29de914139d1e9abcda2097addca9219d44d2696
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104954"
---
# <a name="how-to-load-xml-from-a-file-c"></a><span data-ttu-id="45627-104">Como carregar XML de um arquivo (C#)</span><span class="sxs-lookup"><span data-stu-id="45627-104">How to load XML from a file (C#)</span></span>
<span data-ttu-id="45627-105">Este tópico mostra como carregar XML de um URI usando o método <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="45627-105">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45627-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45627-106">Example</span></span>  
 <span data-ttu-id="45627-107">O seguinte exemplo mostra como carregar um documento XML de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="45627-107">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="45627-108">O seguinte exemplo carrega books.xml e gera a árvore XML no console.</span><span class="sxs-lookup"><span data-stu-id="45627-108">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="45627-109">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: livros (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="45627-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 <span data-ttu-id="45627-110">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="45627-110">This code produces the following output:</span></span>  
  
```xml  
<Catalog>  
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
</Catalog>  
```  
  