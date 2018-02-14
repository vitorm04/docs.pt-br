---
title: Extrair dados XML usando XPathNavigator
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f80c21e7809e5b088582a51d9085a187bccae444
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="extract-xml-data-using-xpathnavigator"></a><span data-ttu-id="6601b-102">Extrair dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6601b-102">Extract XML Data Using XPathNavigator</span></span>
<span data-ttu-id="6601b-103">Há várias maneiras diferentes de representar um documento XML no Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6601b-103">There are several different ways to represent an XML document in the Microsoft .NET Framework.</span></span> <span data-ttu-id="6601b-104">Isso inclui usar um <xref:System.String> ou usar as classes <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument> ou <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="6601b-104">This includes using a <xref:System.String>, or by using the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, or <xref:System.Xml.XPath.XPathDocument> classes.</span></span> <span data-ttu-id="6601b-105">Para facilitar a movimentação entre essas diferentes representações de um documento XML, a classe <xref:System.Xml.XPath.XPathNavigator> fornece alguns métodos e propriedades para extrair XML como um objeto <xref:System.String>, <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="6601b-105">To facilitate moving between these different representations of an XML document, the <xref:System.Xml.XPath.XPathNavigator> class provides a number of methods and properties for extracting the XML as a <xref:System.String>, <xref:System.Xml.XmlReader> object or <xref:System.Xml.XmlWriter> object.</span></span>  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a><span data-ttu-id="6601b-106">Converter um XPathNavigator em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6601b-106">Convert an XPathNavigator to a String</span></span>  
 <span data-ttu-id="6601b-107">A propriedade <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> da classe <xref:System.Xml.XPath.XPathNavigator> é usada para obter a marcação do documento XML inteiro ou apenas a marcação de um único nó e seus nós filho.</span><span class="sxs-lookup"><span data-stu-id="6601b-107">The <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class is used to get the markup of the entire XML document or just the markup of a single node and its child nodes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6601b-108">A propriedade <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> obtém a marcação de apenas os nós filho de um nó.</span><span class="sxs-lookup"><span data-stu-id="6601b-108">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property gets the markup of just the child nodes of a node.</span></span>  
  
 <span data-ttu-id="6601b-109">O exemplo de código a seguir mostra como salvar um documento XML inteiro contido em um objeto <xref:System.Xml.XPath.XPathNavigator> como um <xref:System.String>, bem como um único nó e seus nós filho.</span><span class="sxs-lookup"><span data-stu-id="6601b-109">The following code example shows how to save an entire XML document contained in an <xref:System.Xml.XPath.XPathNavigator> object as a <xref:System.String>, as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("input.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Save the entire input.xml document to a string.  
Dim xml As String = navigator.OuterXml  
  
' Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element)  
Dim root As String = navigator.OuterXml  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Save the entire input.xml document to a string.  
string xml = navigator.OuterXml;  
  
// Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element);  
string root = navigator.OuterXml;  
```  
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a><span data-ttu-id="6601b-110">Converter um XPathNavigator em um XmlReader</span><span class="sxs-lookup"><span data-stu-id="6601b-110">Convert an XPathNavigator to an XmlReader</span></span>  
 <span data-ttu-id="6601b-111">O método <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> é usado para transmitir o conteúdo inteiro de um documento XML ou apenas um único nó e seus nós filho para um objeto <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="6601b-111">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlReader> object.</span></span>  
  
 <span data-ttu-id="6601b-112">Quando o objeto <xref:System.Xml.XmlReader> é criado com o nó atual e seus nós filho, a propriedade <xref:System.Xml.XmlReader> do objeto <xref:System.Xml.XmlReader.ReadState%2A> é definida como <xref:System.Xml.ReadState.Initial>.</span><span class="sxs-lookup"><span data-stu-id="6601b-112">When the <xref:System.Xml.XmlReader> object is created with the current node and its child nodes, the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.Initial>.</span></span> <span data-ttu-id="6601b-113">Quando o método <xref:System.Xml.XmlReader> do objeto <xref:System.Xml.XmlReader.Read%2A> é chamado pela primeira vez, o <xref:System.Xml.XmlReader> é movido para o nó atual <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="6601b-113">When the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.Read%2A> method is called for the first time, the <xref:System.Xml.XmlReader> is moved to the current node of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="6601b-114">O novo objeto <xref:System.Xml.XmlReader> continua a leitura até o final da árvore XML.</span><span class="sxs-lookup"><span data-stu-id="6601b-114">The new <xref:System.Xml.XmlReader> object continues to read until the end of the XML tree is reached.</span></span> <span data-ttu-id="6601b-115">Neste ponto, o método <xref:System.Xml.XmlReader.Read%2A> retorna `false` e a propriedade <xref:System.Xml.XmlReader> do objeto <xref:System.Xml.XmlReader.ReadState%2A> é definida como <xref:System.Xml.ReadState.EndOfFile>.</span><span class="sxs-lookup"><span data-stu-id="6601b-115">At this point, the <xref:System.Xml.XmlReader.Read%2A> method returns `false` and the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.EndOfFile>.</span></span>  
  
 <span data-ttu-id="6601b-116">A posição do objeto <xref:System.Xml.XPath.XPathNavigator> é inalterada pela criação ou movimento do objeto <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="6601b-116">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation or movement of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="6601b-117">O método <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> é válido somente quando posicionado em um elemento ou um nó raiz.</span><span class="sxs-lookup"><span data-stu-id="6601b-117">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is only valid when positioned on an element or root node.</span></span>  
  
 <span data-ttu-id="6601b-118">O exemplo a seguir mostra como obter um objeto <xref:System.Xml.XmlReader> que contém o documento XML inteiro em um objeto <xref:System.Xml.XPath.XPathDocument> assim como um único nó e seus nós filho.</span><span class="sxs-lookup"><span data-stu-id="6601b-118">The following example shows how to get an <xref:System.Xml.XmlReader> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlReader.  
Dim xml As XmlReader = navigator.ReadSubtree()  
  
While xml.Read()  
    Console.WriteLine(xml.ReadInnerXml())  
End While  
  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlReader = navigator.ReadSubtree()  
  
While book.Read()  
    Console.WriteLine(book.ReadInnerXml())  
End While  
  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlReader.  
XmlReader xml = navigator.ReadSubtree();  
  
while (xml.Read())  
{  
    Console.WriteLine(xml.ReadInnerXml());  
}  
  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlReader book = navigator.ReadSubtree();  
  
while (book.Read())  
{  
    Console.WriteLine(book.ReadInnerXml());  
}  
  
book.Close();  
```  
  
 <span data-ttu-id="6601b-119">O exemplo usa o arquivo `books.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="6601b-119">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a><span data-ttu-id="6601b-120">Convertendo um XPathNavigator em um XmlWriter</span><span class="sxs-lookup"><span data-stu-id="6601b-120">Converting an XPathNavigator to an XmlWriter</span></span>  
 <span data-ttu-id="6601b-121">O método <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> é usado para transmitir o conteúdo inteiro de um documento XML ou apenas um único nó e seus nós filho para um objeto <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="6601b-121">The <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="6601b-122">A posição do objeto <xref:System.Xml.XPath.XPathNavigator> é inalterada pela criação do objeto <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="6601b-122">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation of the <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="6601b-123">O exemplo a seguir mostra como obter um objeto <xref:System.Xml.XmlWriter> que contém o documento XML inteiro em um objeto <xref:System.Xml.XPath.XPathDocument> assim como um único nó e seus nós filho.</span><span class="sxs-lookup"><span data-stu-id="6601b-123">The following example shows how to get an <xref:System.Xml.XmlWriter> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlWriter.  
Dim xml As XmlWriter = XmlWriter.Create("newbooks.xml")  
navigator.WriteSubtree(xml)  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlWriter = XmlWriter.Create("book.xml")  
navigator.WriteSubtree(book)  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlWriter.  
XmlWriter xml = XmlWriter.Create("newbooks.xml");  
navigator.WriteSubtree(xml);  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlWriter book = XmlWriter.Create("book.xml");  
navigator.WriteSubtree(book);  
book.Close();  
```  
  
 <span data-ttu-id="6601b-124">O exemplo usa o arquivo `books.xml` localizado anteriormente neste tópico como entrada.</span><span class="sxs-lookup"><span data-stu-id="6601b-124">The example takes the `books.xml` file found earlier in this topic as input.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6601b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6601b-125">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="6601b-126">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="6601b-126">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="6601b-127">Navegação do nó usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6601b-127">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="6601b-128">Navegação do nó de atributo e de namespace usando o XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6601b-128">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="6601b-129">Acessando dados XML fortemente tipados usando o XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6601b-129">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
