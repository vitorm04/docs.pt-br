---
title: "Adicionando elementos, atributos e nós em uma árvore XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 710397e2a2a200dc5129ed42ca34f25617a071c5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a><span data-ttu-id="95c2e-102">Adicionando elementos, atributos e nós em uma árvore XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95c2e-102">Adding Elements, Attributes, and Nodes to an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="95c2e-103">Você pode adicionar conteúdo (elementos, atributos, comentários, instruções de processamento, texto e CDATA) a uma árvore XML existente.</span><span class="sxs-lookup"><span data-stu-id="95c2e-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="95c2e-104">Métodos para adicionar conteúdo</span><span class="sxs-lookup"><span data-stu-id="95c2e-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="95c2e-105">Os seguintes métodos adicionam conteúdo filho a um <xref:System.Xml.Linq.XElement> ou a um <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="95c2e-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="95c2e-106">Método</span><span class="sxs-lookup"><span data-stu-id="95c2e-106">Method</span></span>|<span data-ttu-id="95c2e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="95c2e-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="95c2e-108">Adiciona conteúdo ao final do conteúdo filho de <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="95c2e-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="95c2e-109">Adiciona conteúdo ao início do conteúdo filho de <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="95c2e-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="95c2e-110">Os seguintes métodos adicionam o conteúdo como nós irmãos de um <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="95c2e-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="95c2e-111">O nó mais comum ao qual você adiciona conteúdo irmão é <xref:System.Xml.Linq.XElement>, embora você possa adicionar conteúdo irmão válido a outros tipos de nós como <xref:System.Xml.Linq.XText> ou <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="95c2e-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="95c2e-112">Método</span><span class="sxs-lookup"><span data-stu-id="95c2e-112">Method</span></span>|<span data-ttu-id="95c2e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="95c2e-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="95c2e-114">Adiciona conteúdo depois de <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="95c2e-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="95c2e-115">Adiciona conteúdo antes de <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="95c2e-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="95c2e-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95c2e-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="95c2e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="95c2e-117">Description</span></span>  
 <span data-ttu-id="95c2e-118">O exemplo a seguir cria duas árvores XML e, em seguida, modifica uma das árvores.</span><span class="sxs-lookup"><span data-stu-id="95c2e-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="95c2e-119">Código</span><span class="sxs-lookup"><span data-stu-id="95c2e-119">Code</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element1>1</Element1>  
        <Element2>2</Element2>  
        <Element3>3</Element3>  
        <Element4>4</Element4>  
        <Element5>5</Element5>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child2>2</Child2>  
        <Child3>3</Child3>  
        <Child4>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
xmlTree.Add(<NewChild>new content</NewChild>)  
xmlTree.Add( _  
    From el In srcTree.Elements() _  
    Where CInt(el) > 3 _  
    Select el)  
  
' Even though Child9 does not exist in srcTree, the following statement  
' will not throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"))  
Console.WriteLine(xmlTree)  
```  
  
### <a name="comments"></a><span data-ttu-id="95c2e-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="95c2e-120">Comments</span></span>  
 <span data-ttu-id="95c2e-121">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="95c2e-121">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="95c2e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95c2e-122">See Also</span></span>  
 [<span data-ttu-id="95c2e-123">Modificando árvores XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95c2e-123">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
