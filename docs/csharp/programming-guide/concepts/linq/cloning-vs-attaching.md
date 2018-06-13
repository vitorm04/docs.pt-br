---
title: Clonagem contra. Anexar (C#)
ms.date: 07/20/2015
ms.assetid: 357c5efa-7b73-4f14-aa67-6bebdba4e7ea
ms.openlocfilehash: 31b5498e18e63ffba357b34780c7eb388e08b37f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315757"
---
# <a name="cloning-vs-attaching-c"></a><span data-ttu-id="43320-102">Clonagem contra. Anexar (C#)</span><span class="sxs-lookup"><span data-stu-id="43320-102">Cloning vs. Attaching (C#)</span></span>
<span data-ttu-id="43320-103">Ao adicionar <xref:System.Xml.Linq.XNode> (incluindo <xref:System.Xml.Linq.XElement>) ou objetos de <xref:System.Xml.Linq.XAttribute> para uma nova árvore, se o novo conteúdo não tem nenhum pai, os objetos estão conectados somente à árvore XML.</span><span class="sxs-lookup"><span data-stu-id="43320-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="43320-104">Se o novo conteúdo já parented, e é parte de outra árvore XML, o novo conteúdo são clonados.</span><span class="sxs-lookup"><span data-stu-id="43320-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="43320-105">O conteúdo recentemente clonado é anexado a árvore XML.</span><span class="sxs-lookup"><span data-stu-id="43320-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43320-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43320-106">Example</span></span>  
 <span data-ttu-id="43320-107">O código a seguir demonstra o comportamento quando você adiciona um elemento parented a uma árvore, e quando você adiciona um elemento sem o pai a uma árvore.</span><span class="sxs-lookup"><span data-stu-id="43320-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
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
  
 <span data-ttu-id="43320-108">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="43320-108">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="43320-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43320-109">See Also</span></span>  
 [<span data-ttu-id="43320-110">Criando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="43320-110">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
