---
title: Programando com nós-LINQ to XML
description: Saiba como codificar no nível de nó de uma árvore XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 8f9d5c8656a06a9b40a3833aaf7e190b9ba3f0a6
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551965"
---
# <a name="programming-with-nodes-linq-to-xml"></a><span data-ttu-id="553f2-103">Programando com nós (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="553f2-103">Programming with nodes (LINQ to XML)</span></span>

<span data-ttu-id="553f2-104">LINQ to XML desenvolvedores que precisam escrever programas como um editor de XML, um sistema de transformação ou um gravador de relatório muitas vezes precisam de um código que funcione em um nível mais detalhado de granularidade do que elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="553f2-104">LINQ to XML developers who need to write programs such as an XML editor, a transform system, or a report writer often need code that works at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="553f2-105">Geralmente, eles precisam trabalhar no nível do nó, manipular nós de texto, instruções de processamento e comentários de processamento.</span><span class="sxs-lookup"><span data-stu-id="553f2-105">They often need to work at the node level, manipulating text nodes, processing instructions, and processing comments.</span></span> <span data-ttu-id="553f2-106">Este artigo fornece informações sobre programação no nível do nó.</span><span class="sxs-lookup"><span data-stu-id="553f2-106">This article provides information about programming at the node level.</span></span>

## <a name="example-the-parent-property-values-of-the-child-nodes-of-xdocument-are-set-to-null"></a><span data-ttu-id="553f2-107">Exemplo: os `Parent` valores de propriedade dos nós filho de XDocument estão definidos como `null`</span><span class="sxs-lookup"><span data-stu-id="553f2-107">Example: The `Parent` property values of the child nodes of XDocument are set to `null`</span></span>

<span data-ttu-id="553f2-108">A propriedade de <xref:System.Xml.Linq.XObject.Parent%2A> contém <xref:System.Xml.Linq.XElement>pai, não o nó pai.</span><span class="sxs-lookup"><span data-stu-id="553f2-108">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="553f2-109">Os nós filho de <xref:System.Xml.Linq.XDocument> não têm nenhum <xref:System.Xml.Linq.XElement>pai.</span><span class="sxs-lookup"><span data-stu-id="553f2-109">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="553f2-110">Seu pai é o documento, portanto, a <xref:System.Xml.Linq.XObject.Parent%2A> propriedade para esses nós é definida como `null` .</span><span class="sxs-lookup"><span data-stu-id="553f2-110">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to `null`.</span></span>

<span data-ttu-id="553f2-111">O exemplo a seguir demonstra este:</span><span class="sxs-lookup"><span data-stu-id="553f2-111">The following example demonstrates this:</span></span>

```csharp
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);
Console.WriteLine(doc.Root.Parent == null);
```

```vb
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)
Console.WriteLine(doc.Root.Parent Is Nothing)
```

<span data-ttu-id="553f2-112">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="553f2-112">This example produces the following output:</span></span>

```output
True
True
```

## <a name="example-adding-text-may-or-may-not-create-a-new-text-node"></a><span data-ttu-id="553f2-113">Exemplo: adicionar texto pode ou não criar um novo nó de texto</span><span class="sxs-lookup"><span data-stu-id="553f2-113">Example: Adding text may or may not create a new text node</span></span>

<span data-ttu-id="553f2-114">Em um número XML que programa modelos, nós adjacentes de texto sempre são mesclados.</span><span class="sxs-lookup"><span data-stu-id="553f2-114">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="553f2-115">Isso é às vezes chamado normalização de nós de texto.</span><span class="sxs-lookup"><span data-stu-id="553f2-115">This is sometimes called normalization of text nodes.</span></span> <span data-ttu-id="553f2-116">LINQ to XML não normaliza os nós de texto.</span><span class="sxs-lookup"><span data-stu-id="553f2-116">LINQ to XML doesn't normalize text nodes.</span></span> <span data-ttu-id="553f2-117">Se você adicionar dois nós de texto ao mesmo elemento, resultará a nós adjacentes de texto.</span><span class="sxs-lookup"><span data-stu-id="553f2-117">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="553f2-118">No entanto, se você adicionar conteúdo especificado como uma cadeia de caracteres em vez de como um <xref:System.Xml.Linq.XText> nó, LINQ to XML poderá mesclar a cadeia de caracteres com um nó de texto adjacente.</span><span class="sxs-lookup"><span data-stu-id="553f2-118">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, LINQ to XML might merge the string with an adjacent text node.</span></span> <span data-ttu-id="553f2-119">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="553f2-119">The following example demonstrates this.</span></span>

```csharp
XElement xmlTree = new XElement("Root", "Content");

Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());

// this doesn't add a new text node
xmlTree.Add("new content");
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());

// this does add a new, adjacent text node
xmlTree.Add(new XText("more text"));
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());
```

```vb
Dim xmlTree As XElement = <Root>Content</Root>
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())

' This doesn't add a new text node.
xmlTree.Add("new content")
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())

'// This does add a new, adjacent text node.
xmlTree.Add(New XText("more text"))
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())
```

 <span data-ttu-id="553f2-120">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="553f2-120">This example produces the following output:</span></span>

```output
1
1
2
```

## <a name="example-setting-a-text-node-value-to-the-empty-string-doesnt-delete-the-node"></a><span data-ttu-id="553f2-121">Exemplo: definir um valor de nó de texto para a cadeia de caracteres vazia não exclui o nó</span><span class="sxs-lookup"><span data-stu-id="553f2-121">Example: Setting a text node value to the empty string doesn't delete the node</span></span>

<span data-ttu-id="553f2-122">Em algum XML que programa modelos, os nós de texto são garantidos para não conter a cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="553f2-122">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="553f2-123">O raciocínio é que um nó de texto não tem impacto na serialização XML.</span><span class="sxs-lookup"><span data-stu-id="553f2-123">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="553f2-124">No entanto, pelo mesmo motivo que os nós de texto adjacentes são possíveis, se você remover o texto de um nó de texto definindo seu valor para a cadeia de caracteres vazia, o nó de texto em si não será excluído.</span><span class="sxs-lookup"><span data-stu-id="553f2-124">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself won't be deleted.</span></span>

```csharp
XElement xmlTree = new XElement("Root", "Content");
XText textNode = xmlTree.Nodes().OfType<XText>().First();

// the following line doesn't cause the removal of the text node.
textNode.Value = "";

XText textNode2 = xmlTree.Nodes().OfType<XText>().First();
Console.WriteLine(">>{0}<<", textNode2);
```

```vb
Dim xmlTree As XElement = <Root>Content</Root>
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()

' The following line doesn't cause the removal of the text node.
textNode.Value = ""

Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()
Console.WriteLine(">>{0}<<", textNode2)
```

<span data-ttu-id="553f2-125">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="553f2-125">This example produces the following output:</span></span>

```output
>><<
```

## <a name="example-an-element-with-one-empty-text-node-is-serialized-differently-from-one-with-no-text-node"></a><span data-ttu-id="553f2-126">Exemplo: um elemento com um nó de texto vazio é serializado de forma diferente de um sem nó de texto</span><span class="sxs-lookup"><span data-stu-id="553f2-126">Example: An element with one empty text node is serialized differently from one with no text node</span></span>

<span data-ttu-id="553f2-127">Se um elemento contiver apenas um nó de texto filho vazio, ele será serializado com a sintaxe de marca longa: `<Child></Child>` .</span><span class="sxs-lookup"><span data-stu-id="553f2-127">If an element contains only a child text node that's empty, it's serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="553f2-128">Se um elemento não contiver nenhum nó filho, ele será serializado com a sintaxe de marca curta: `<Child />` .</span><span class="sxs-lookup"><span data-stu-id="553f2-128">If an element contains no child nodes whatsoever, it's serialized with the short tag syntax: `<Child />`.</span></span>

```csharp
XElement child1 = new XElement("Child1",
    new XText("")
);
XElement child2 = new XElement("Child2");
Console.WriteLine(child1);
Console.WriteLine(child2);
```

```vb
Dim child1 As XElement = New XElement("Child1", _
    New XText("") _
)
Dim child2 As XElement = New XElement("Child2")
Console.WriteLine(child1)
Console.WriteLine(child2)
```

<span data-ttu-id="553f2-129">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="553f2-129">This example produces the following output:</span></span>

```xml
<Child1></Child1>
<Child2 />
```

## <a name="example-namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="553f2-130">Exemplo: namespaces são atributos na árvore de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="553f2-130">Example: Namespaces are attributes in the LINQ to XML tree</span></span>

<span data-ttu-id="553f2-131">Embora as declarações de namespace tenham sintaxe idêntica aos atributos, em algumas interfaces de programação, como XSLT e XPath, as declarações de namespace não são consideradas atributos.</span><span class="sxs-lookup"><span data-stu-id="553f2-131">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations aren't considered to be attributes.</span></span> <span data-ttu-id="553f2-132">No entanto, no LINQ to XML, os namespaces são armazenados como <xref:System.Xml.Linq.XAttribute> objetos na árvore XML.</span><span class="sxs-lookup"><span data-stu-id="553f2-132">However, in LINQ to XML, namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="553f2-133">Se você iterar pelos atributos de um elemento que contém uma declaração de namespace, a declaração de namespace será um dos itens na coleção retornada.</span><span class="sxs-lookup"><span data-stu-id="553f2-133">If you iterate through the attributes of an element that contains a namespace declaration, the namespace declaration is one of the items in the returned collection.</span></span> <span data-ttu-id="553f2-134">A propriedade de <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> indica se um atributo é uma declaração de namespace.</span><span class="sxs-lookup"><span data-stu-id="553f2-134">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root
    xmlns='http://www.adventure-works.com'
    xmlns:fc='www.fourthcoffee.com'
    AnAttribute='abc'/>");
foreach (XAttribute att in root.Attributes())
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);
```

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

<span data-ttu-id="553f2-135">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="553f2-135">This example produces the following output:</span></span>

```output
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True
AnAttribute="abc"  IsNamespaceDeclaration:False
```

## <a name="example-xpath-axis-methods-dont-return-the-child-text-nodes-of-xdocument"></a><span data-ttu-id="553f2-136">Exemplo: os métodos do eixo XPath não retornam os nós de texto filho de XDocument</span><span class="sxs-lookup"><span data-stu-id="553f2-136">Example: XPath axis methods don't return the child text nodes of XDocument</span></span>

<span data-ttu-id="553f2-137">LINQ to XML permite nós de texto filho de um <xref:System.Xml.Linq.XDocument> , desde que os nós de texto contenham apenas espaços em branco.</span><span class="sxs-lookup"><span data-stu-id="553f2-137">LINQ to XML allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="553f2-138">No entanto, o modelo de objeto XPath não inclui o espaço em branco como nós filho de um documento, portanto, quando você itera pelos filhos de um <xref:System.Xml.Linq.XDocument> usando o <xref:System.Xml.Linq.XContainer.Nodes%2A> eixo, nós de texto de espaço em branco serão retornados.</span><span class="sxs-lookup"><span data-stu-id="553f2-138">However, the XPath object model doesn't include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="553f2-139">No entanto, quando você itera através dos filhos de um <xref:System.Xml.Linq.XDocument> usando os métodos do eixo XPath, os nós de texto de espaço em branco não serão retornados.</span><span class="sxs-lookup"><span data-stu-id="553f2-139">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes won't be returned.</span></span>

```csharp
// Create a document with some white space child nodes of the document.
XDocument root = XDocument.Parse(
@"<?xml version='1.0' encoding='utf-8' standalone='yes'?>

<Root/>

<!--a comment-->
", LoadOptions.PreserveWhitespace);

// count the white space child nodes using LINQ to XML
Console.WriteLine(root.Nodes().OfType<XText>().Count());

// count the white space child nodes using XPathEvaluate
Console.WriteLine(((IEnumerable)root.XPathEvaluate("text()")).OfType<XText>().Count());
```

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

<span data-ttu-id="553f2-140">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="553f2-140">This example produces the following output:</span></span>

```output
3
0
```

### <a name="the-xml-declaration-node-of-an-xdocument-is-a-property-not-a-child-node"></a><span data-ttu-id="553f2-141">O nó de declaração XML de um XDocument é uma propriedade, não um nó filho</span><span class="sxs-lookup"><span data-stu-id="553f2-141">The XML declaration node of an XDocument is a property, not a child node</span></span>

<span data-ttu-id="553f2-142">Ao percorrer os nós filho de um <xref:System.Xml.Linq.XDocument> , você não verá o objeto de declaração XML.</span><span class="sxs-lookup"><span data-stu-id="553f2-142">When you iterate through the child nodes of an <xref:System.Xml.Linq.XDocument>, you won't see the XML declaration object.</span></span> <span data-ttu-id="553f2-143">É uma propriedade do documento, não um nó filho dele.</span><span class="sxs-lookup"><span data-stu-id="553f2-143">It's a property of the document, not a child node of it.</span></span>

```csharp
XDocument doc = new XDocument(
    new XDeclaration("1.0", "utf-8", "yes"),
    new XElement("Root")
);
doc.Save("Temp.xml");
Console.WriteLine(File.ReadAllText("Temp.xml"));

// this shows that there is only one child node of the document
Console.WriteLine(doc.Nodes().Count());
```

```vb
Dim doc As XDocument = _
<?xml version='1.0' encoding='utf-8' standalone='yes'?>
<Root/>

doc.Save("Temp.xml")
Console.WriteLine(File.ReadAllText("Temp.xml"))

' This shows that there is only one child node of the document.
Console.WriteLine(doc.Nodes().Count())
```

<span data-ttu-id="553f2-144">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="553f2-144">This example produces the following output:</span></span>

```output
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Root />
1
```
