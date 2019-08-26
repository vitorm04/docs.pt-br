---
title: 'Como: Criar uma árvore com base em um XmlReader (C#)'
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: f632bbdad7d52ea37e2587516792dfd13178d702
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593879"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="609fd-102">Como: Criar uma árvore com base em um XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="609fd-102">How to: Create a Tree from an XmlReader (C#)</span></span>
<span data-ttu-id="609fd-103">Este tópico mostra como criar uma árvore de XML diretamente de <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="609fd-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="609fd-104">Para criar um <xref:System.Xml.Linq.XElement> de um <xref:System.Xml.XmlReader>, você deverá posicionar o <xref:System.Xml.XmlReader> em um nó de elemento.</span><span class="sxs-lookup"><span data-stu-id="609fd-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="609fd-105">O <xref:System.Xml.XmlReader> ignorará comentários e instruções de processamento, mas se o <xref:System.Xml.XmlReader> estiver posicionado em um nó de texto, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="609fd-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="609fd-106">Para evitar esses erros, sempre posicione o <xref:System.Xml.XmlReader> em um elemento antes de criar uma árvore de XML do <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="609fd-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="609fd-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="609fd-107">Example</span></span>  
 <span data-ttu-id="609fd-108">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Livros (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="609fd-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="609fd-109">O código a seguir cria um objeto `T:System.Xml.XmlReader` e depois lê os nós até encontrar o primeiro nó do elemento.</span><span class="sxs-lookup"><span data-stu-id="609fd-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="609fd-110">Ele em seguida carrega o objeto <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="609fd-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="609fd-111">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="609fd-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="609fd-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="609fd-112">See also</span></span>

- [<span data-ttu-id="609fd-113">Analisando XML (C#)</span><span class="sxs-lookup"><span data-stu-id="609fd-113">Parsing XML (C#)</span></span>](./parsing-xml.md)
