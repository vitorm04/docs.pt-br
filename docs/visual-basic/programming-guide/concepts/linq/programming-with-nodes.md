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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 52fb60b95b869a79900f84c2a1a7a6151bb5b58f
ms.lasthandoff: 03/13/2017

---
# <a name="programming-with-nodes-visual-basic"></a>Programação conosco (Visual Basic)
desenvolvedores de[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] que precisam geralmente escrever programas como um editor XML, um sistema uma transformação, ou uma necessidade o gravador de relatório escrever programas que funcionam no nível mais fino de granularidade dos elementos e atributos. Freqüentemente necessitam de trabalhar no nível de nó, em nós de manipulação de texto, as instruções de processamento, e os comentários. Este tópico fornece alguns detalhes sobre programação no nível do nó.  
  
## <a name="node-details"></a>Detalhes do nó  
 Há um número de detalhes de programação que um programador que funciona a nível do nó deve conhecer.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>A propriedade pai de nós de filhos de XDocument é definida como nula  
 O <xref:System.Xml.Linq.XObject.Parent%2A>propriedade contém o pai <xref:System.Xml.Linq.XElement>, não o nó pai.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XObject.Parent%2A> Nós filhos de <xref:System.Xml.Linq.XDocument>não ter nenhum pai <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> Seu pai é o documento, para que o <xref:System.Xml.Linq.XObject.Parent%2A>propriedade para esses nós é definida como null.</xref:System.Xml.Linq.XObject.Parent%2A>  
  
 O exemplo a seguir demonstra este:  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Nós adjacentes de texto são possíveis  
 Em um número XML que programa modelos, nós adjacentes de texto sempre são mesclados. Isso é às vezes chamado normalização de nós de texto. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] não normalizará nós de texto. Se você adicionar dois nós de texto ao mesmo elemento, resultará a nós adjacentes de texto. No entanto, se você adicionar conteúdo especificado como uma cadeia de caracteres em vez de um <xref:System.Xml.Linq.XText>nó [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] pode mesclar a cadeia de caracteres com um nó de texto adjacente.</xref:System.Xml.Linq.XText>  
  
 O exemplo a seguir demonstra este:  
  
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
  
 Este exemplo gera a seguinte saída:  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Os nós vazios de texto são possíveis  
 Em algum XML que programa modelos, os nós de texto são garantidos para não conter a cadeia de caracteres vazia. O raciocínio é que um nó de texto não tem impacto na serialização XML. No entanto, pela mesma razão nós adjacentes do texto são possíveis, se você remover o texto de um nó de texto definindo seu valor para a cadeia de caracteres vazia, o nó de texto em si não serão excluídos.  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Um nó de texto vazio afeta a serialização  
 Se um elemento contém apenas um nó filho do texto que está vazio, é serializado com longa sintaxe de marca: `<Child></Child>`. Se um elemento não contém nenhum nó filho, qualquer é serializado pela sintaxe abreviada de marca: `<Child />`.  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Namespaces são atributos na árvore LINQ to XML  
 Mesmo que as declarações namespace tenham a sintaxe idêntica a atributos, em algumas interfaces de programação, como XSLT e o XPath, as declarações namespace não são consideradas como atributos. No entanto, em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], namespaces são armazenadas como <xref:System.Xml.Linq.XAttribute>objetos na árvore XML.</xref:System.Xml.Linq.XAttribute> Se você itera através de atributos para um elemento que contém uma declaração de namespace, você verá a declaração de namespace como um dos itens na coleção retornada.  
  
 O <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A>propriedade indica se um atributo é uma declaração de namespace.</xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A>  
  
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
  
 Este exemplo gera a seguinte saída:  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Os métodos do eixo XPath retornam espaço em branco filho de XDocument  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]permite que nós de texto filho de um <xref:System.Xml.Linq.XDocument>, contanto que os nós de texto contém somente espaço em branco.</xref:System.Xml.Linq.XDocument> No entanto, o modelo de objeto XPath não inclui o espaço em branco como nós filho de um documento, então quando você itera através de filhos de um <xref:System.Xml.Linq.XDocument>usando o <xref:System.Xml.Linq.XContainer.Nodes%2A>eixo, nós de texto de espaço em branco serão retornados.</xref:System.Xml.Linq.XContainer.Nodes%2A> </xref:System.Xml.Linq.XDocument> No entanto, quando você itera através de filhos de um <xref:System.Xml.Linq.XDocument>usando os métodos de eixo XPath, nós de texto de espaço em branco não serão retornados.</xref:System.Xml.Linq.XDocument>  
  
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
  
 Este exemplo gera a seguinte saída:  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>Os objetos de XDeclaration não são nós  
 Quando você itera através de nós filhos de um <xref:System.Xml.Linq.XDocument>, você não verá o objeto de declaração XML.</xref:System.Xml.Linq.XDocument> É uma propriedade do documento, não um nó filho deles.  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a>Consulte também  
 [Avançada LINQ to XML programação (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
