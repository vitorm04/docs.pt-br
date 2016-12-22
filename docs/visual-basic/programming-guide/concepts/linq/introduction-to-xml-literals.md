---
title: "Introdu&#231;&#227;o a literais XML no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Introdu&#231;&#227;o a literais XML no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Esta seção fornece informações sobre como criar árvores XML em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 Para obter informações sobre como usar os resultados de consultas LINQ como o conteúdo de uma árvore XML, consulte [Construção funcional \(LINQ to XML\) \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 Para obter mais informações sobre literais XML em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], consulte [Visão geral de LINQ to XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).  
  
## Criando árvores XML  
 O exemplo a seguir mostra como criar um <xref:System.Xml.Linq.XElement>, neste caso `contacts`:  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
### Criando um XElement com conteúdo simples  
 Você pode criar um <xref:System.Xml.Linq.XElement> que contém o conteúdo simples, como segue:  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### Criando um elemento vazio  
 Você pode criar um vazio <xref:System.Xml.Linq.XElement>, da seguinte maneira:  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Customer />  
```  
  
### Usando expressões inseridas  
 Um recurso importante de literais XML é que eles permitem expressões inseridas. Expressões inseridas permite avaliar uma expressão e inserir os resultados da expressão na árvore XML. Se a expressão for avaliada como um tipo de <xref:System.Xml.Linq.XElement>, um elemento é inserido na árvore. Se a expressão for avaliada como um tipo de <xref:System.Xml.Linq.XAttribute>, um atributo é inserido na árvore. Você pode inserir elementos e atributos na árvore apenas onde eles são válidos.  
  
 É importante observar que apenas uma única expressão pode entrar em uma expressão inserida. É possível inserir várias instruções. Se uma expressão ultrapassa de uma única linha, você deve usar o caractere de continuação de linha.  
  
 Se você usar uma expressão inserida para adicionar nós existentes \(incluindo elementos\) e atributos para uma nova árvore XML e se os nós existentes já parented, os nós são clonados. Os nós recentemente clonados são anexados a nova árvore XML. Se os nós existentes não parented, os nós são conectados somente para a nova árvore XML. O último exemplo neste tópico demonstra isso.  
  
 O exemplo a seguir usa uma expressão inserida para inserir um elemento na árvore:  
  
```vb  
xmlTree1 As XElement = _  
    <Root>  
        <Child>Contents</Child>  
    </Root>  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child> %>  
    </Root>  
Console.WriteLine(xmlTree2)  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### Usando expressões inseridas para conteúdo  
 Você pode usar uma expressão inserida para fornecer o conteúdo de um elemento:  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root>Some content</Root>  
```  
  
### Usando uma consulta LINQ em uma expressão inserida  
 Você pode usar os resultados de uma consulta LINQ para o conteúdo de um elemento:  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### Usando expressões inseridas para nomes de nó  
 Você também pode usar expressões inseridas para calcular valores de atributo, nomes de atributo, nomes de elementos e valores de elemento:  
  
```vb  
Dim eleName As String = "ele"  
Dim attName As String = "att"  
Dim attValue As String = "aValue"  
Dim eleValue As String = "eValue"  
Dim n As XElement = _  
    <Root <%= attName %>=<%= attValue %>>  
        <<%= eleName %>>  
            <%= eleValue %>  
        </>  
    </Root>  
Console.WriteLine(n)  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### Clonagem contra. Anexar  
 Como mencionado anteriormente, se você usar uma expressão inserida para adicionar nós existentes \(incluindo elementos\) e os atributos para uma nova árvore XML, se os nós existentes já parented, os nós são clonados e os nós recentemente clonados são anexados a nova árvore XML. Se os nós existentes não parented, eles estão conectados somente para a nova árvore XML.  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 Este exemplo produz a seguinte saída:  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## Consulte também  
 [Criando árvores XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)