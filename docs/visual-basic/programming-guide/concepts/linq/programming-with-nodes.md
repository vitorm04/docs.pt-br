---
title: "Programa&#231;&#227;o conosco (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Programa&#231;&#227;o conosco (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] os desenvolvedores que precisam escrever programas como um editor de XML, um sistema de transformação ou um gravador de relatório geralmente precisam escrever programas que funcionam em um nível mais refinado de granularidade que elementos e atributos. Geralmente, eles precisam trabalhar no nível de nó, manipulação de nós de texto, instruções de processamento e comentários. Este tópico fornece alguns detalhes sobre programação no nível de nó.  
  
## Detalhes do nó  
 Há um número de detalhes de programação que um programador trabalhando no nível do nó deve conhecer.  
  
### Pai propriedade dos filhos nós de XDocument é definida como Null  
 O <xref:System.Xml.Linq.XObject.Parent%2A> propriedade contém o pai <xref:System.Xml.Linq.XElement>, não o nó pai. Nós filho do <xref:System.Xml.Linq.XDocument> não ter nenhum pai <xref:System.Xml.Linq.XElement>. Seu pai é o documento, para que o <xref:System.Xml.Linq.XObject.Parent%2A> propriedade para esses nós é definida como null.  
  
 O exemplo a seguir demonstra isso:  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
  
```  
  
 Este exemplo produz a seguinte saída:  
  
```  
True  
True  
```  
  
### Nós adjacentes de texto são possíveis  
 Em um número de modelos de programação XML, nós adjacentes de texto sempre são mesclados. Isso é às vezes chamado normalização de nós de texto.[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] não normalizará nós de texto. Se você adicionar dois nós de texto ao mesmo elemento, resultará em nós adjacentes de texto. No entanto, se você adicionar conteúdo especificado como uma cadeia de caracteres em vez de um <xref:System.Xml.Linq.XText> nó [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] pode mesclar a cadeia de caracteres com um nó de texto adjacente.  
  
 O exemplo a seguir demonstra isso:  
  
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
  
 Este exemplo produz a seguinte saída:  
  
```  
1  
1  
2  
```  
  
### Nós de texto vazia são possíveis  
 Em alguns modelos de programação XML, nós de texto são garantidos para não conter a cadeia de caracteres vazia. O motivo é que um nó de texto não tem impacto na serialização do XML. No entanto, pelo mesmo motivo que nós adjacentes de texto são possíveis, se você remover o texto de um nó de texto definindo seu valor como a cadeia de caracteres vazia, o nó de texto em si não serão excluído.  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
  
```  
  
 Este exemplo produz a seguinte saída:  
  
```  
>><<  
```  
  
### Um nó de texto vazio afeta a serialização  
 Se um elemento contém apenas um nó de texto filho que está vazio, é serializado com longa sintaxe de marca: `<Child></Child>`. Se um elemento não contém nenhum nó filho, qualquer, é serializado com a sintaxe abreviada de marca: `<Child />`.  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
  
```  
  
 Este exemplo produz a seguinte saída:  
  
```  
<Child1></Child1>  
<Child2 />  
```  
  
### Namespaces são atributos LINQ a árvore XML  
 Embora as declarações namespace têm sintaxe idêntica a atributos, em algumas interfaces de programação, como XSLT e XPath, declarações de namespace não são consideradas como atributos. No entanto, em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], namespaces são armazenadas como <xref:System.Xml.Linq.XAttribute> objetos na árvore XML. Se você itera através de atributos para um elemento que contém uma declaração de namespace, você verá a declaração de namespace como um dos itens na coleção retornada.  
  
 O <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> propriedade indica se um atributo é uma declaração de namespace.  
  
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
  
 Este exemplo produz a seguinte saída:  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### Métodos do eixo XPath não retornam espaço em branco filho de XDocument  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] permite que nós de texto filho de um <xref:System.Xml.Linq.XDocument>, contanto que os nós de texto contém somente espaço em branco. No entanto, o modelo de objeto XPath não inclui o espaço em branco como nós filho de um documento, então quando você itera através de filhos de um <xref:System.Xml.Linq.XDocument> usando o <xref:System.Xml.Linq.XContainer.Nodes%2A> eixo, nós de texto de espaço em branco serão retornados. No entanto, quando você itera através de filhos de um <xref:System.Xml.Linq.XDocument> usando os métodos de eixo XPath, nós de texto de espaço em branco não serão retornados.  
  
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
  
 Este exemplo produz a seguinte saída:  
  
```  
3  
0  
```  
  
### Objetos de XDeclaration não são nós  
 Quando você itera através de nós filhos de um <xref:System.Xml.Linq.XDocument>, você não verá o objeto de declaração XML. É uma propriedade do documento, não um nó filho deles.  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
  
```  
  
 Este exemplo produz a seguinte saída:  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## Consulte também  
 [Advanced LINQ to XML Programming \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)