---
title: Adicionando elementos, atributos e nós a uma árvore XML (C#)
description: Saiba mais sobre os métodos para adicionar conteúdo como elementos, atributos, comentários, instruções de processamento e texto a uma árvore XML existente.
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 78a84401494e2d4280799632fa42dc95574e3e10
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105547"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="916cc-103">Adicionando elementos, atributos e nós a uma árvore XML (C#)</span><span class="sxs-lookup"><span data-stu-id="916cc-103">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="916cc-104">Você pode adicionar conteúdo (elementos, atributos, comentários, instruções de processamento, texto e CDATA) a uma árvore XML existente.</span><span class="sxs-lookup"><span data-stu-id="916cc-104">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="916cc-105">Métodos para adicionar conteúdo</span><span class="sxs-lookup"><span data-stu-id="916cc-105">Methods for Adding Content</span></span>  
 <span data-ttu-id="916cc-106">Os seguintes métodos adicionam conteúdo filho a um <xref:System.Xml.Linq.XElement> ou a um <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="916cc-106">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="916cc-107">Método</span><span class="sxs-lookup"><span data-stu-id="916cc-107">Method</span></span>|<span data-ttu-id="916cc-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="916cc-108">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="916cc-109">Adiciona conteúdo ao final do conteúdo filho de <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="916cc-109">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="916cc-110">Adiciona conteúdo ao início do conteúdo filho de <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="916cc-110">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="916cc-111">Os seguintes métodos adicionam o conteúdo como nós irmãos de um <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="916cc-111">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="916cc-112">O nó mais comum ao qual você adiciona conteúdo irmão é <xref:System.Xml.Linq.XElement>, embora você possa adicionar conteúdo irmão válido a outros tipos de nós como <xref:System.Xml.Linq.XText> ou <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="916cc-112">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="916cc-113">Método</span><span class="sxs-lookup"><span data-stu-id="916cc-113">Method</span></span>|<span data-ttu-id="916cc-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="916cc-114">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="916cc-115">Adiciona conteúdo depois de <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="916cc-115">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="916cc-116">Adiciona conteúdo antes de <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="916cc-116">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="916cc-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="916cc-117">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="916cc-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="916cc-118">Description</span></span>  
 <span data-ttu-id="916cc-119">O exemplo a seguir cria duas árvores XML e, em seguida, modifica uma das árvores.</span><span class="sxs-lookup"><span data-stu-id="916cc-119">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="916cc-120">Código</span><span class="sxs-lookup"><span data-stu-id="916cc-120">Code</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",
    new XElement("Element1", 1),  
    new XElement("Element2", 2),  
    new XElement("Element3", 3),  
    new XElement("Element4", 4),  
    new XElement("Element5", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child2", 2),  
    new XElement("Child3", 3),  
    new XElement("Child4", 4),  
    new XElement("Child5", 5)  
);  
xmlTree.Add(new XElement("NewChild", "new content"));  
xmlTree.Add(  
    from el in srcTree.Elements()  
    where (int)el > 3  
    select el  
);  
// Even though Child9 does not exist in srcTree, the following statement will not  
// throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"));  
Console.WriteLine(xmlTree);  
```  
  
### <a name="comments"></a><span data-ttu-id="916cc-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="916cc-121">Comments</span></span>  
 <span data-ttu-id="916cc-122">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="916cc-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  