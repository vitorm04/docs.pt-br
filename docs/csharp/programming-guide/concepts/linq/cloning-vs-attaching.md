---
title: Clonagem contra. Anexar (C#) | Microsoft Docs
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
ms.assetid: 357c5efa-7b73-4f14-aa67-6bebdba4e7ea
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 784c3b92ce10878b244ae5d965f5033a6ee6f9ae
ms.lasthandoff: 03/13/2017

---
# <a name="cloning-vs-attaching-c"></a>Clonagem contra. Anexar (C#)
Ao adicionar objetos <xref:System.Xml.Linq.XNode> (incluindo <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute> a uma nova árvore, se o novo conteúdo não tiver pai, os objetos serão simplesmente anexados à árvore XML. Se o novo conteúdo já parented, e é parte de outra árvore XML, o novo conteúdo são clonados. O conteúdo recentemente clonado é anexado a árvore XML.  
  
## <a name="example"></a>Exemplo  
 O código a seguir demonstra o comportamento quando você adiciona um elemento parented a uma árvore, e quando você adiciona um elemento sem o pai a uma árvore.  
  
```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Consulte também  
 [Criando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
