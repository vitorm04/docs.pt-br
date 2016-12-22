---
title: "Programa&#231;&#227;o conosco (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Programa&#231;&#227;o conosco (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] os desenvolvedores que precisam escrever programas como um editor de XML, um sistema de transformação ou um gravador de relatório geralmente precisam escrever programas que funcionam em um nível mais refinado de granularidade que elementos e atributos. Geralmente, eles precisam trabalhar no nível de nó, manipulação de nós de texto, instruções de processamento e comentários. Este tópico fornece alguns detalhes sobre programação no nível de nó.  
  
## Detalhes do nó  
 Há um número de detalhes de programação que um programador trabalhando no nível do nó deve conhecer.  
  
### Pai propriedade dos filhos nós de XDocument é definida como Null  
 O <xref:System.Xml.Linq.XObject.Parent%2A> propriedade contém o pai <xref:System.Xml.Linq.XElement>, não o nó pai. Nós filho do <xref:System.Xml.Linq.XDocument> não ter nenhum pai <xref:System.Xml.Linq.XElement>. Seu pai é o documento, para que o <xref:System.Xml.Linq.XObject.Parent%2A> propriedade para esses nós é definida como null.  
  
 O exemplo a seguir demonstra isso:  
  
```c#  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 Este exemplo produz a seguinte saída:  
  
```  
True  
True  
```  
  
### Nós adjacentes de texto são possíveis  
 Em um número de modelos de programação XML, nós adjacentes de texto sempre são mesclados. Isso é às vezes chamado normalização de nós de texto.[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] não normalizará nós de texto. Se você adicionar dois nós de texto ao mesmo elemento, resultará em nós adjacentes de texto. No entanto, se você adicionar conteúdo especificado como uma cadeia de caracteres em vez de um <xref:System.Xml.Linq.XText> nó [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] pode mesclar a cadeia de caracteres com um nó de texto adjacente.  
  
 O exemplo a seguir demonstra isso:  
  
```c#  
XElement xmlTree = new XElement("Root", "Content");  
  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does not add a new text node  
xmlTree.Add("new content");  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does add a new, adjacent text node  
xmlTree.Add(new XText("more text"));  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
```  
  
 Este exemplo produz a seguinte saída:  
  
```  
1  
1  
2  
```  
  
### Nós de texto vazia são possíveis  
 Em alguns modelos de programação XML, nós de texto são garantidos para não conter a cadeia de caracteres vazia. O motivo é que um nó de texto não tem impacto na serialização do XML. No entanto, pelo mesmo motivo que nós adjacentes de texto são possíveis, se você remover o texto de um nó de texto definindo seu valor como a cadeia de caracteres vazia, o nó de texto em si não serão excluído.  
  
```c#  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);   
```  
  
 Este exemplo produz a seguinte saída:  
  
```  
>><<  
```  
  
### Um nó de texto vazio afeta a serialização  
 Se um elemento contém apenas um nó de texto filho que está vazio, é serializado com longa sintaxe de marca: `<Child></Child>`. Se um elemento não contém nenhum nó filho, qualquer, é serializado com a sintaxe abreviada de marca: `<Child />`.  
  
```c#  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);   
```  
  
 Este exemplo produz a seguinte saída:  
  
```  
<Child1></Child1>  
<Child2 />  
```  
  
### Namespaces são atributos LINQ a árvore XML  
 Embora as declarações namespace têm sintaxe idêntica a atributos, em algumas interfaces de programação, como XSLT e XPath, declarações de namespace não são consideradas como atributos. No entanto, em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], namespaces são armazenadas como <xref:System.Xml.Linq.XAttribute> objetos na árvore XML. Se você itera através de atributos para um elemento que contém uma declaração de namespace, você verá a declaração de namespace como um dos itens na coleção retornada.  
  
 O <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> propriedade indica se um atributo é uma declaração de namespace.  
  
```c#  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 Este exemplo produz a seguinte saída:  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### Métodos do eixo XPath não retornam espaço em branco filho de XDocument  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] permite que nós de texto filho de um <xref:System.Xml.Linq.XDocument>, contanto que os nós de texto contém somente espaço em branco. No entanto, o modelo de objeto XPath não inclui o espaço em branco como nós filho de um documento, então quando você itera através de filhos de um <xref:System.Xml.Linq.XDocument> usando o <xref:System.Xml.Linq.XContainer.Nodes%2A> eixo, nós de texto de espaço em branco serão retornados. No entanto, quando você itera através de filhos de um <xref:System.Xml.Linq.XDocument> usando os métodos de eixo XPath, nós de texto de espaço em branco não serão retornados.  
  
```c#  
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
  
 Este exemplo produz a seguinte saída:  
  
```  
3  
0  
```  
  
### Objetos de XDeclaration não são nós  
 Quando você itera através de nós filhos de um <xref:System.Xml.Linq.XDocument>, você não verá o objeto de declaração XML. É uma propriedade do documento, não um nó filho deles.  
  
```c#  
XDocument doc = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root")  
);  
doc.Save("Temp.xml");  
Console.WriteLine(File.ReadAllText("Temp.xml"));  
  
// this shows that there is only one child node of the document  
Console.WriteLine(doc.Nodes().Count());  
```  
  
 Este exemplo produz a seguinte saída:  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## Consulte também  
 [Advanced LINQ to XML Programming \(C\#\)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)