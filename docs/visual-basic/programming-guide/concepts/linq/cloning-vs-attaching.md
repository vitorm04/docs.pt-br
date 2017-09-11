---
title: Clonagem contra. Anexando (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9c86a75b1c9b4dc25e29d8323d23f89232b8de80
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="cloning-vs-attaching-visual-basic"></a><span data-ttu-id="99d95-102">Clonagem contra. Anexando (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99d95-102">Cloning vs. Attaching (Visual Basic)</span></span>
<span data-ttu-id="99d95-103">Ao adicionar <xref:System.Xml.Linq.XNode>(incluindo <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>objetos para uma nova árvore, se o novo conteúdo não tem nenhum pai, os objetos serão simplesmente anexados à árvore XML.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="99d95-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="99d95-104">Se o novo conteúdo já parented, e é parte de outra árvore XML, o novo conteúdo são clonados.</span><span class="sxs-lookup"><span data-stu-id="99d95-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="99d95-105">O conteúdo recentemente clonado é anexado a árvore XML.</span><span class="sxs-lookup"><span data-stu-id="99d95-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99d95-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99d95-106">Example</span></span>  
 <span data-ttu-id="99d95-107">O código a seguir demonstra o comportamento quando você adiciona um elemento parented a uma árvore, e quando você adiciona um elemento sem o pai a uma árvore.</span><span class="sxs-lookup"><span data-stu-id="99d95-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
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
  
 <span data-ttu-id="99d95-108">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="99d95-108">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="99d95-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99d95-109">See Also</span></span>  
 [<span data-ttu-id="99d95-110">Criando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99d95-110">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
