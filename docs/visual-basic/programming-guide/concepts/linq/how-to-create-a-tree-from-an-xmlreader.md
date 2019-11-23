---
title: Como criar uma árvore de um XmlReader
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: 7d8d7f5b6389bef520e11fd2b7cc3e1c7e862e73
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353082"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a><span data-ttu-id="3ffa1-102">How to: Create a Tree from an XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ffa1-102">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>

<span data-ttu-id="3ffa1-103">Este tópico mostra como criar uma árvore de XML diretamente de <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="3ffa1-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="3ffa1-104">Para criar um <xref:System.Xml.Linq.XElement> de um <xref:System.Xml.XmlReader>, você deverá posicionar o <xref:System.Xml.XmlReader> em um nó de elemento.</span><span class="sxs-lookup"><span data-stu-id="3ffa1-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="3ffa1-105">O <xref:System.Xml.XmlReader> ignorará comentários e instruções de processamento, mas se o <xref:System.Xml.XmlReader> estiver posicionado em um nó de texto, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="3ffa1-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="3ffa1-106">Para evitar esses erros, sempre posicione o <xref:System.Xml.XmlReader> em um elemento antes de criar uma árvore de XML do <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="3ffa1-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>

## <a name="example"></a><span data-ttu-id="3ffa1-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3ffa1-107">Example</span></span>

<span data-ttu-id="3ffa1-108">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: livros (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3ffa1-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>

<span data-ttu-id="3ffa1-109">O código a seguir cria um objeto `T:System.Xml.XmlReader` e depois lê os nós até encontrar o primeiro nó do elemento.</span><span class="sxs-lookup"><span data-stu-id="3ffa1-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="3ffa1-110">Ele em seguida carrega o objeto <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3ffa1-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

<span data-ttu-id="3ffa1-111">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3ffa1-111">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3ffa1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ffa1-112">See also</span></span>

- [<span data-ttu-id="3ffa1-113">Parsing XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ffa1-113">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
