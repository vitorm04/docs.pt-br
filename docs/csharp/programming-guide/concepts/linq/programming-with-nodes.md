---
title: "Programando com nós (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6afa5c9ca5fdf4a8c64be826ead86e96aa94a446
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="programming-with-nodes-c"></a><span data-ttu-id="31410-102">Programando com nós (C#)</span><span class="sxs-lookup"><span data-stu-id="31410-102">Programming with Nodes (C#)</span></span>
<span data-ttu-id="31410-103">desenvolvedores de[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] que precisam geralmente escrever programas como um editor XML, um sistema uma transformação, ou uma necessidade o gravador de relatório escrever programas que funcionam no nível mais fino de granularidade dos elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="31410-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="31410-104">Freqüentemente necessitam de trabalhar no nível de nó, em nós de manipulação de texto, as instruções de processamento, e os comentários.</span><span class="sxs-lookup"><span data-stu-id="31410-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="31410-105">Este tópico fornece alguns detalhes sobre programação no nível do nó.</span><span class="sxs-lookup"><span data-stu-id="31410-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="31410-106">Detalhes do nó</span><span class="sxs-lookup"><span data-stu-id="31410-106">Node Details</span></span>  
 <span data-ttu-id="31410-107">Há um número de detalhes de programação que um programador que funciona a nível do nó deve conhecer.</span><span class="sxs-lookup"><span data-stu-id="31410-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="31410-108">A propriedade pai de nós de filhos de XDocument é definida como nula</span><span class="sxs-lookup"><span data-stu-id="31410-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="31410-109">A propriedade de <xref:System.Xml.Linq.XObject.Parent%2A> contém <xref:System.Xml.Linq.XElement>pai, não o nó pai.</span><span class="sxs-lookup"><span data-stu-id="31410-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="31410-110">Os nós filho de <xref:System.Xml.Linq.XDocument> não têm nenhum <xref:System.Xml.Linq.XElement>pai.</span><span class="sxs-lookup"><span data-stu-id="31410-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="31410-111">Seu pai é o documento, assim que a propriedade de <xref:System.Xml.Linq.XObject.Parent%2A> para os nós é definida como nula.</span><span class="sxs-lookup"><span data-stu-id="31410-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="31410-112">O exemplo a seguir demonstra este:</span><span class="sxs-lookup"><span data-stu-id="31410-112">The following example demonstrates this:</span></span>  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 <span data-ttu-id="31410-113">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="31410-113">This example produces the following output:</span></span>  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="31410-114">Nós adjacentes de texto são possíveis</span><span class="sxs-lookup"><span data-stu-id="31410-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="31410-115">Em um número XML que programa modelos, nós adjacentes de texto sempre são mesclados.</span><span class="sxs-lookup"><span data-stu-id="31410-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="31410-116">Isso é às vezes chamado normalização de nós de texto.</span><span class="sxs-lookup"><span data-stu-id="31410-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="31410-117"> não normalizará nós de texto.</span><span class="sxs-lookup"><span data-stu-id="31410-117"> does not normalize text nodes.</span></span> <span data-ttu-id="31410-118">Se você adicionar dois nós de texto ao mesmo elemento, resultará a nós adjacentes de texto.</span><span class="sxs-lookup"><span data-stu-id="31410-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="31410-119">Entretanto, se você adicionar o conteúdo especificado como uma cadeia de caracteres em vez de como um nó de <xref:System.Xml.Linq.XText>, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poderá mesclar a cadeia de caracteres com um nó de texto adjacente.</span><span class="sxs-lookup"><span data-stu-id="31410-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="31410-120">O exemplo a seguir demonstra este:</span><span class="sxs-lookup"><span data-stu-id="31410-120">The following example demonstrates this:</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does not add a new text node  
xmlTree.Add("new content");  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does add a new, adjacent text node  
xmlTree.Add(new XText("more text"));  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
```  
  
 <span data-ttu-id="31410-121">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="31410-121">This example produces the following output:</span></span>  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="31410-122">Os nós vazios de texto são possíveis</span><span class="sxs-lookup"><span data-stu-id="31410-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="31410-123">Em algum XML que programa modelos, os nós de texto são garantidos para não conter a cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="31410-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="31410-124">O raciocínio é que um nó de texto não tem impacto na serialização XML.</span><span class="sxs-lookup"><span data-stu-id="31410-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="31410-125">No entanto, pela mesma razão nós adjacentes do texto são possíveis, se você remover o texto de um nó de texto definindo seu valor para a cadeia de caracteres vazia, o nó de texto em si não serão excluídos.</span><span class="sxs-lookup"><span data-stu-id="31410-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);   
```  
  
 <span data-ttu-id="31410-126">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="31410-126">This example produces the following output:</span></span>  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="31410-127">Um nó de texto vazio afeta a serialização</span><span class="sxs-lookup"><span data-stu-id="31410-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="31410-128">Se um elemento contém apenas um nó filho do texto que está vazio, é serializado com longa sintaxe de marca: `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="31410-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="31410-129">Se um elemento não contém nenhum nó filho, qualquer é serializado pela sintaxe abreviada de marca: `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="31410-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);   
```  
  
 <span data-ttu-id="31410-130">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="31410-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="31410-131">Namespaces são atributos na árvore LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="31410-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="31410-132">Mesmo que as declarações namespace tenham a sintaxe idêntica a atributos, em algumas interfaces de programação, como XSLT e o XPath, as declarações namespace não são consideradas como atributos.</span><span class="sxs-lookup"><span data-stu-id="31410-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="31410-133">No entanto, em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces são armazenadas como objetos de <xref:System.Xml.Linq.XAttribute> na árvore XML.</span><span class="sxs-lookup"><span data-stu-id="31410-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="31410-134">Se você itera através de atributos para um elemento que contém uma declaração de namespace, você verá a declaração de namespace como um dos itens na coleção retornada.</span><span class="sxs-lookup"><span data-stu-id="31410-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="31410-135">A propriedade de <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> indica se um atributo é uma declaração de namespace.</span><span class="sxs-lookup"><span data-stu-id="31410-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 <span data-ttu-id="31410-136">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="31410-136">This example produces the following output:</span></span>  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="31410-137">Os métodos do eixo XPath retornam espaço em branco filho de XDocument</span><span class="sxs-lookup"><span data-stu-id="31410-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="31410-138"> permite nós filhos de texto de <xref:System.Xml.Linq.XDocument>, desde que os nós de texto contém somente espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="31410-138"> allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="31410-139">No entanto, o modelo de objeto XPath não inclui espaço em branco como nós filho de um documento, para que quando você itera através de filhos de <xref:System.Xml.Linq.XDocument> usando o eixo de <xref:System.Xml.Linq.XContainer.Nodes%2A> , os nós de texto de espaço em branco serão retornados.</span><span class="sxs-lookup"><span data-stu-id="31410-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="31410-140">No entanto, quando você itera através de filhos de <xref:System.Xml.Linq.XDocument> usando os métodos do eixo XPath, os nós de texto de espaço em branco não serão retornados.</span><span class="sxs-lookup"><span data-stu-id="31410-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes will not be returned.</span></span>  
  
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
  
 <span data-ttu-id="31410-141">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="31410-141">This example produces the following output:</span></span>  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="31410-142">Os objetos de XDeclaration não são nós</span><span class="sxs-lookup"><span data-stu-id="31410-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="31410-143">Quando você itera através de nós de filhos de <xref:System.Xml.Linq.XDocument>, você não verá o objeto da declaração XML.</span><span class="sxs-lookup"><span data-stu-id="31410-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="31410-144">É uma propriedade do documento, não um nó filho deles.</span><span class="sxs-lookup"><span data-stu-id="31410-144">It is a property of the document, not a child node of it.</span></span>  
  
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
  
 <span data-ttu-id="31410-145">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="31410-145">This example produces the following output:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a><span data-ttu-id="31410-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31410-146">See Also</span></span>  
 [<span data-ttu-id="31410-147">Programação LINQ to XML avançada (C#)</span><span class="sxs-lookup"><span data-stu-id="31410-147">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

