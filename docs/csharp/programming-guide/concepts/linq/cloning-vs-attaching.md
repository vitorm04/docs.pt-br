---
title: Clonagem contra. Anexar (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 357c5efa-7b73-4f14-aa67-6bebdba4e7ea
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e58e9538c319c20f9e820ff1de1fb6f973a18bdc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cloning-vs-attaching-c"></a>Clonagem contra. Anexar (C#)
Ao adicionar <xref:System.Xml.Linq.XNode> (incluindo <xref:System.Xml.Linq.XElement>) ou objetos de <xref:System.Xml.Linq.XAttribute> para uma nova árvore, se o novo conteúdo não tem nenhum pai, os objetos estão conectados somente à árvore XML. Se o novo conteúdo já parented, e é parte de outra árvore XML, o novo conteúdo são clonados. O conteúdo recentemente clonado é anexado a árvore XML.  
  
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
