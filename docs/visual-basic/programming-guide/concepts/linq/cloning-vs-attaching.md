---
title: "Clonagem contra. Anexar (Visual Basic) | Microsoft Docs"
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
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Clonagem contra. Anexar (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Ao adicionar <xref:System.Xml.Linq.XNode> \(incluindo <xref:System.Xml.Linq.XElement>\) ou <xref:System.Xml.Linq.XAttribute> objetos para uma nova árvore, se o novo conteúdo não tem nenhum pai, os objetos serão simplesmente anexados à árvore XML. Se o novo conteúdo já tiver um pai e faz parte de outra árvore XML, o novo conteúdo será clonado. O conteúdo recém\-clonado é anexado à árvore XML.  
  
## Exemplo  
 O código a seguir demonstra o comportamento quando você adiciona um elemento pai a uma árvore, e quando você adiciona um elemento sem o pai de uma árvore.  
  
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