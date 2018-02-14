---
title: "Selecionar nós usando a navegação XPath"
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
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 836702a3200a21c6a9830bdcd1f74a78129b5a6c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="fedb0-102">Selecionar nós usando a navegação XPath</span><span class="sxs-lookup"><span data-stu-id="fedb0-102">Select Nodes Using XPath Navigation</span></span>
<span data-ttu-id="fedb0-103">O DOM (Document Object Model) XML contém métodos que permitem que você use a navegação da linguagem XPath para consultar informações no DOM.</span><span class="sxs-lookup"><span data-stu-id="fedb0-103">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="fedb0-104">Você pode usar a linguagem XPath para localizar um único nó específico ou todos os nós que correspondam a alguns critérios.</span><span class="sxs-lookup"><span data-stu-id="fedb0-104">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="fedb0-105">Métodos de seleção XPath</span><span class="sxs-lookup"><span data-stu-id="fedb0-105">XPath Select Methods</span></span>  
 <span data-ttu-id="fedb0-106">As classes DOM fornecem dois métodos de seleção XPath: o método <xref:System.Xml.XmlNode.SelectSingleNode%2A> e o método <xref:System.Xml.XmlNode.SelectNodes%2A>.</span><span class="sxs-lookup"><span data-stu-id="fedb0-106">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="fedb0-107">O método <xref:System.Xml.XmlNode.SelectSingleNode%2A> retorna o primeiro nó que corresponde aos critérios de seleção.</span><span class="sxs-lookup"><span data-stu-id="fedb0-107">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="fedb0-108">O método <xref:System.Xml.XmlNode.SelectNodes%2A> retorna um <xref:System.Xml.XmlNodeList> que contém os nós correspondentes.</span><span class="sxs-lookup"><span data-stu-id="fedb0-108">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="fedb0-109">O exemplo a seguir usa o método <xref:System.Xml.XmlNode.SelectSingleNode%2A> para selecionar o primeiro nó `book`, no qual o sobrenome do autor atende a critérios específicos.</span><span class="sxs-lookup"><span data-stu-id="fedb0-109">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="fedb0-110">O arquivo bookstore.xml (que é fornecido no final deste tópico) é usado como o arquivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="fedb0-110">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's   
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's   
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 <span data-ttu-id="fedb0-111">O exemplo a seguir usa o método <xref:System.Xml.XmlNode.SelectNodes%2A> para selecionar todos os nós de livros em que o preço é maior do que um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="fedb0-111">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="fedb0-112">O preço de cada livro na lista selecionada é reduzido programaticamente em dez por cento.</span><span class="sxs-lookup"><span data-stu-id="fedb0-112">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="fedb0-113">Finalmente, o arquivo atualizado é gravado no console.</span><span class="sxs-lookup"><span data-stu-id="fedb0-113">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="fedb0-114">O arquivo bookstore.xml (que é fornecido no final deste tópico) é usado como o arquivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="fedb0-114">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 <span data-ttu-id="fedb0-115">Os exemplos acima iniciam a consulta XPath no elemento de documento.</span><span class="sxs-lookup"><span data-stu-id="fedb0-115">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="fedb0-116">A definição do ponto de partida para a consulta XPath define o nó de contexto, que é o ponto de partida para a consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="fedb0-116">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="fedb0-117">Se você não deseja começar no elemento de documento, mas a partir do primeiro elemento filho do documento, você pode codificar a instrução de seleção da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="fedb0-117">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="fedb0-118">Todos os objetos <xref:System.Xml.XmlNodeList> são sincronizados com o documento subjacente.</span><span class="sxs-lookup"><span data-stu-id="fedb0-118">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="fedb0-119">Portanto, se você iterar pela lista de nós e modificar o valor de um nó, esse nó também será atualizado no documento de origem.</span><span class="sxs-lookup"><span data-stu-id="fedb0-119">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="fedb0-120">Observe no exemplo anterior que, quando um nó é modificado no <xref:System.Xml.XmlNodeList> selecionado, o documento subjacente também é modificado.</span><span class="sxs-lookup"><span data-stu-id="fedb0-120">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fedb0-121">Quando o documento subjacente é modificado, é aconselhável executar novamente a seleção.</span><span class="sxs-lookup"><span data-stu-id="fedb0-121">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="fedb0-122">Se o nó modificado for um que possa fazer com que o nó seja adicionado à lista de nós quando não tiver sido anteriormente, ou que agora faça com que ele seja removido da lista, não haverá nenhuma garantia de que a lista de nós agora esteja exata.</span><span class="sxs-lookup"><span data-stu-id="fedb0-122">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="fedb0-123">Namespaces em expressões XPath</span><span class="sxs-lookup"><span data-stu-id="fedb0-123">Namespaces in XPath Expressions</span></span>  
 <span data-ttu-id="fedb0-124">As expressões XPath podem incluir namespaces</span><span class="sxs-lookup"><span data-stu-id="fedb0-124">XPath expressions can include namespaces.</span></span> <span data-ttu-id="fedb0-125">A resolução de namespace tem suporte com o uso do <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="fedb0-125">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="fedb0-126">Se a expressão XPath incluir um prefixo, o par de prefixo e URI de namespace deverá ser adicionado a <xref:System.Xml.XmlNamespaceManager>, e <xref:System.Xml.XmlNamespaceManager> será passado ao método <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> ou <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29>.</span><span class="sxs-lookup"><span data-stu-id="fedb0-126">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="fedb0-127">Observe que os exemplos de código acima usam <xref:System.Xml.XmlNamespaceManager> para resolver o namespace do documento bookstore.xml.</span><span class="sxs-lookup"><span data-stu-id="fedb0-127">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fedb0-128">Se a expressão XPath não incluir um prefixo, presume-se que o URI do namespace seja o namespace vazio.</span><span class="sxs-lookup"><span data-stu-id="fedb0-128">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="fedb0-129">Se o XML incluir um namespace padrão, você ainda deverá adicionar um prefixo e um URI de namespace a <xref:System.Xml.XmlNamespaceManager>; caso contrário, nenhum nó será selecionado.</span><span class="sxs-lookup"><span data-stu-id="fedb0-129">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="fedb0-130">Arquivo de entrada</span><span class="sxs-lookup"><span data-stu-id="fedb0-130">Input File</span></span>  
 <span data-ttu-id="fedb0-131">A seguir está o arquivo bookstore.xml que é usado como o arquivo de entrada nos exemplos deste tópico:</span><span class="sxs-lookup"><span data-stu-id="fedb0-131">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fedb0-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fedb0-132">See Also</span></span>  
 [<span data-ttu-id="fedb0-133">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="fedb0-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
