---
title: 'Como: Carregar XML de um arquivo (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e2d337ad-8ac8-4671-b694-30e5ca1413b7
ms.openlocfilehash: b4f1f9abfa33b76e702b51221715da80c3f66421
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814935"
---
# <a name="how-to-load-xml-from-a-file-visual-basic"></a><span data-ttu-id="184e8-102">Como: Carregar XML de um arquivo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="184e8-102">How to: Load XML from a File (Visual Basic)</span></span>
<span data-ttu-id="184e8-103">Este tópico mostra como carregar XML de um URI usando o método <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="184e8-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="184e8-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="184e8-104">Example</span></span>  
 <span data-ttu-id="184e8-105">O seguinte exemplo mostra como carregar um documento XML de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="184e8-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="184e8-106">O seguinte exemplo carrega books.xml e gera a árvore XML no console.</span><span class="sxs-lookup"><span data-stu-id="184e8-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="184e8-107">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Livros (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="184e8-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim booksFromFile As XElement = XElement.Load("books.xml")  
Console.WriteLine(booksFromFile)  
```  
  
 <span data-ttu-id="184e8-108">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="184e8-108">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="184e8-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="184e8-109">See also</span></span>

- [<span data-ttu-id="184e8-110">Analisando XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="184e8-110">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
