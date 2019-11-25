---
title: Como criar uma árvore a partir de um XmlReaderC#()
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 196779a10678bdd3aa5399cf883af8c4b074e5df
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141317"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="e761c-102">Como criar uma árvore a partir de um XmlReaderC#()</span><span class="sxs-lookup"><span data-stu-id="e761c-102">How to create a tree from an XmlReader (C#)</span></span>
<span data-ttu-id="e761c-103">Este tópico mostra como criar uma árvore de XML diretamente de <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="e761c-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="e761c-104">Para criar um <xref:System.Xml.Linq.XElement> de um <xref:System.Xml.XmlReader>, você deverá posicionar o <xref:System.Xml.XmlReader> em um nó de elemento.</span><span class="sxs-lookup"><span data-stu-id="e761c-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="e761c-105">O <xref:System.Xml.XmlReader> ignorará comentários e instruções de processamento, mas se o <xref:System.Xml.XmlReader> estiver posicionado em um nó de texto, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="e761c-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="e761c-106">Para evitar esses erros, sempre posicione o <xref:System.Xml.XmlReader> em um elemento antes de criar uma árvore de XML do <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="e761c-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e761c-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e761c-107">Example</span></span>  
 <span data-ttu-id="e761c-108">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: livros (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e761c-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="e761c-109">O código a seguir cria um objeto `T:System.Xml.XmlReader` e depois lê os nós até encontrar o primeiro nó do elemento.</span><span class="sxs-lookup"><span data-stu-id="e761c-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="e761c-110">Ele em seguida carrega o objeto <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e761c-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="e761c-111">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e761c-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e761c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e761c-112">See also</span></span>

- [<span data-ttu-id="e761c-113">Analisando XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e761c-113">Parsing XML (C#)</span></span>](how-to-parse-a-string.md)
