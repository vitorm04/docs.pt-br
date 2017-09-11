---
title: Programando conosco (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 967e207aa4d1a4afb21f82b7b1767a5c6dc088c6
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="programming-with-nodes-visual-basic"></a><span data-ttu-id="9042e-102">Programação conosco (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9042e-102">Programming with Nodes (Visual Basic)</span></span>
<span data-ttu-id="9042e-103">desenvolvedores de[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] que precisam geralmente escrever programas como um editor XML, um sistema uma transformação, ou uma necessidade o gravador de relatório escrever programas que funcionam no nível mais fino de granularidade dos elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="9042e-103">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="9042e-104">Freqüentemente necessitam de trabalhar no nível de nó, em nós de manipulação de texto, as instruções de processamento, e os comentários.</span><span class="sxs-lookup"><span data-stu-id="9042e-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="9042e-105">Este tópico fornece alguns detalhes sobre programação no nível do nó.</span><span class="sxs-lookup"><span data-stu-id="9042e-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="9042e-106">Detalhes do nó</span><span class="sxs-lookup"><span data-stu-id="9042e-106">Node Details</span></span>  
 <span data-ttu-id="9042e-107">Há um número de detalhes de programação que um programador que funciona a nível do nó deve conhecer.</span><span class="sxs-lookup"><span data-stu-id="9042e-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="9042e-108">A propriedade pai de nós de filhos de XDocument é definida como nula</span><span class="sxs-lookup"><span data-stu-id="9042e-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="9042e-109">O <xref:System.Xml.Linq.XObject.Parent%2A>propriedade contém o pai <xref:System.Xml.Linq.XElement>, não o nó pai.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XObject.Parent%2A></span><span class="sxs-lookup"><span data-stu-id="9042e-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="9042e-110">Nós filhos de <xref:System.Xml.Linq.XDocument>não ter nenhum pai <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="9042e-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="9042e-111">Seu pai é o documento, para que o <xref:System.Xml.Linq.XObject.Parent%2A>propriedade para esses nós é definida como null.</xref:System.Xml.Linq.XObject.Parent%2A></span><span class="sxs-lookup"><span data-stu-id="9042e-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="9042e-112">O exemplo a seguir demonstra este:</span><span class="sxs-lookup"><span data-stu-id="9042e-112">The following example demonstrates this:</span></span>  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 <span data-ttu-id="9042e-113">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9042e-113">This example produces the following output:</span></span>  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="9042e-114">Nós adjacentes de texto são possíveis</span><span class="sxs-lookup"><span data-stu-id="9042e-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="9042e-115">Em um número XML que programa modelos, nós adjacentes de texto sempre são mesclados.</span><span class="sxs-lookup"><span data-stu-id="9042e-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="9042e-116">Isso é às vezes chamado normalização de nós de texto.</span><span class="sxs-lookup"><span data-stu-id="9042e-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="9042e-117"> não normalizará nós de texto.</span><span class="sxs-lookup"><span data-stu-id="9042e-117"> does not normalize text nodes.</span></span> <span data-ttu-id="9042e-118">Se você adicionar dois nós de texto ao mesmo elemento, resultará a nós adjacentes de texto.</span><span class="sxs-lookup"><span data-stu-id="9042e-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="9042e-119">No entanto, se você adicionar conteúdo especificado como uma cadeia de caracteres em vez de um <xref:System.Xml.Linq.XText>nó [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] pode mesclar a cadeia de caracteres com um nó de texto adjacente.</xref:System.Xml.Linq.XText></span><span class="sxs-lookup"><span data-stu-id="9042e-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="9042e-120">O exemplo a seguir demonstra este:</span><span class="sxs-lookup"><span data-stu-id="9042e-120">The following example demonstrates this:</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
' This does not add a new text node.  
xmlTree.Add("new content")  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
'// This does add a new, adjacent text node.  
xmlTree.Add(New XText("more text"))  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
```  
  
 <span data-ttu-id="9042e-121">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9042e-121">This example produces the following output:</span></span>  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="9042e-122">Os nós vazios de texto são possíveis</span><span class="sxs-lookup"><span data-stu-id="9042e-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="9042e-123">Em algum XML que programa modelos, os nós de texto são garantidos para não conter a cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="9042e-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="9042e-124">O raciocínio é que um nó de texto não tem impacto na serialização XML.</span><span class="sxs-lookup"><span data-stu-id="9042e-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="9042e-125">No entanto, pela mesma razão nós adjacentes do texto são possíveis, se você remover o texto de um nó de texto definindo seu valor para a cadeia de caracteres vazia, o nó de texto em si não serão excluídos.</span><span class="sxs-lookup"><span data-stu-id="9042e-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 <span data-ttu-id="9042e-126">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9042e-126">This example produces the following output:</span></span>  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="9042e-127">Um nó de texto vazio afeta a serialização</span><span class="sxs-lookup"><span data-stu-id="9042e-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="9042e-128">Se um elemento contém apenas um nó filho do texto que está vazio, é serializado com longa sintaxe de marca: `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="9042e-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="9042e-129">Se um elemento não contém nenhum nó filho, qualquer é serializado pela sintaxe abreviada de marca: `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="9042e-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 <span data-ttu-id="9042e-130">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9042e-130">This example produces the following output:</span></span>  
  
```  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="9042e-131">Namespaces são atributos na árvore LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="9042e-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="9042e-132">Mesmo que as declarações namespace tenham a sintaxe idêntica a atributos, em algumas interfaces de programação, como XSLT e o XPath, as declarações namespace não são consideradas como atributos.</span><span class="sxs-lookup"><span data-stu-id="9042e-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="9042e-133">No entanto, em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], namespaces são armazenadas como <xref:System.Xml.Linq.XAttribute>objetos na árvore XML.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="9042e-133">However, in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="9042e-134">Se você itera através de atributos para um elemento que contém uma declaração de namespace, você verá a declaração de namespace como um dos itens na coleção retornada.</span><span class="sxs-lookup"><span data-stu-id="9042e-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="9042e-135">O <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A>propriedade indica se um atributo é uma declaração de namespace.</xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A></span><span class="sxs-lookup"><span data-stu-id="9042e-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```vb  
Dim root As XElement = _   
<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>  
For Each att As XAttribute In root.Attributes()  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, _  
                      att.IsNamespaceDeclaration)  
Next  
```  
  
 <span data-ttu-id="9042e-136">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9042e-136">This example produces the following output:</span></span>  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="9042e-137">Os métodos do eixo XPath retornam espaço em branco filho de XDocument</span><span class="sxs-lookup"><span data-stu-id="9042e-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="9042e-138">permite que nós de texto filho de um <xref:System.Xml.Linq.XDocument>, contanto que os nós de texto contém somente espaço em branco.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="9042e-138"> allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="9042e-139">No entanto, o modelo de objeto XPath não inclui o espaço em branco como nós filho de um documento, então quando você itera através de filhos de um <xref:System.Xml.Linq.XDocument>usando o <xref:System.Xml.Linq.XContainer.Nodes%2A>eixo, nós de texto de espaço em branco serão retornados.</xref:System.Xml.Linq.XContainer.Nodes%2A> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="9042e-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="9042e-140">No entanto, quando você itera através de filhos de um <xref:System.Xml.Linq.XDocument>usando os métodos de eixo XPath, nós de texto de espaço em branco não serão retornados.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="9042e-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes will not be returned.</span></span>  
  
```vb  
' Create a document with some white space child nodes of the document.  
Dim root As XDocument = XDocument.Parse( _  
"<?xml version='1.0' encoding='utf-8' standalone='yes'?>" & _  
vbNewLine & "<Root/>" & vbNewLine & "<!--a comment-->" & vbNewLine, _  
LoadOptions.PreserveWhitespace)  
  
' Count the white space child nodes using LINQ to XML.  
Console.WriteLine(root.Nodes().OfType(Of XText)().Count())  
  
' Count the white space child nodes using XPathEvaluate.  
Dim nodes As IEnumerable = CType(root.XPathEvaluate("text()"), IEnumerable)  
Console.WriteLine(nodes.OfType(Of XText)().Count())  
```  
  
 <span data-ttu-id="9042e-141">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9042e-141">This example produces the following output:</span></span>  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="9042e-142">Os objetos de XDeclaration não são nós</span><span class="sxs-lookup"><span data-stu-id="9042e-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="9042e-143">Quando você itera através de nós filhos de um <xref:System.Xml.Linq.XDocument>, você não verá o objeto de declaração XML.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="9042e-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="9042e-144">É uma propriedade do documento, não um nó filho deles.</span><span class="sxs-lookup"><span data-stu-id="9042e-144">It is a property of the document, not a child node of it.</span></span>  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 <span data-ttu-id="9042e-145">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9042e-145">This example produces the following output:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a><span data-ttu-id="9042e-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9042e-146">See Also</span></span>  
 [<span data-ttu-id="9042e-147">Avançada LINQ to XML programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9042e-147">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

