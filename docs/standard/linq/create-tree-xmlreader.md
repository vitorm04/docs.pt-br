---
title: Como criar uma árvore a partir de um XmlReader-LINQ to XML
description: Você pode usar um XmlReader em C# ou Visual Basic para ler XML e criar uma árvore XML. Você deve posicionar corretamente o XmlReader em um nó de elemento.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 659135ae9930d4ba63b13e436ebd278807e4256b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551944"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-linq-to-xml"></a><span data-ttu-id="30347-104">Como criar uma árvore a partir de um XmlReader (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="30347-104">How to create a tree from an XmlReader (LINQ to XML)</span></span>

<span data-ttu-id="30347-105">Este artigo mostra como criar uma árvore XML diretamente de um <xref:System.Xml.XmlReader> em C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="30347-105">This article shows how to create an XML tree directly from an <xref:System.Xml.XmlReader> in C# or Visual Basic.</span></span> <span data-ttu-id="30347-106">Para criar um <xref:System.Xml.Linq.XElement> de um <xref:System.Xml.XmlReader> , você posiciona o <xref:System.Xml.XmlReader> em um nó de elemento.</span><span class="sxs-lookup"><span data-stu-id="30347-106">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="30347-107">O <xref:System.Xml.XmlReader> ignorará comentários e instruções de processamento, mas se o <xref:System.Xml.XmlReader> estiver posicionado em um nó de texto, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="30347-107">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="30347-108">Para evitar esses erros, posicione o <xref:System.Xml.XmlReader> em um elemento antes de criar uma árvore XML a partir do <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="30347-108">To avoid such errors, position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>

## <a name="example-load-xelement-object-from-an-xmlreader-object"></a><span data-ttu-id="30347-109">Exemplo: carregar objeto XElement a partir de um objeto XmlReader</span><span class="sxs-lookup"><span data-stu-id="30347-109">Example: Load XElement object from an XmlReader object</span></span>

<span data-ttu-id="30347-110">Este exemplo usa o [arquivo XML de exemplo](sample-xml-file-books.md)de documento XML: livros.</span><span class="sxs-lookup"><span data-stu-id="30347-110">This example uses the XML document [Sample XML file: Books](sample-xml-file-books.md).</span></span>

<span data-ttu-id="30347-111">O código a seguir cria um <xref:System.Xml.XmlReader> objeto, lê nós até encontrar o primeiro nó de elemento e carrega o <xref:System.Xml.Linq.XElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="30347-111">The following code creates a <xref:System.Xml.XmlReader> object, reads nodes until it finds the first element node, and loads the <xref:System.Xml.Linq.XElement> object.</span></span>

```csharp
XmlReader r = XmlReader.Create("books.xml");
while (r.NodeType != XmlNodeType.Element)
    r.Read();
XElement e = XElement.Load(r);
Console.WriteLine(e);
```

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

<span data-ttu-id="30347-112">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="30347-112">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="30347-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="30347-113">See also</span></span>

- [<span data-ttu-id="30347-114">Análise XML</span><span class="sxs-lookup"><span data-stu-id="30347-114">Parse XML</span></span>](parse-string.md)
