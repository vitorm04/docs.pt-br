---
title: "Removendo elementos, atributos e nós de uma árvore XML (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8842858080ce1f27d997e6af61a8dd2301cdc2bc
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017


---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="40e33-102">Removendo elementos, atributos e nós de uma árvore XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40e33-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="40e33-103">Você pode modificar uma árvore XML, remover elementos, atributos e outros tipos de nós.</span><span class="sxs-lookup"><span data-stu-id="40e33-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="40e33-104">Remover um único elemento ou um único atributo de um documento XML é simples.</span><span class="sxs-lookup"><span data-stu-id="40e33-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="40e33-105">No entanto, ao remover coleções de elementos ou atributos, você deve primeiro materializar uma coleção em uma lista e depois excluir os elementos ou os atributos da lista.</span><span class="sxs-lookup"><span data-stu-id="40e33-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="40e33-106">A melhor abordagem é usar o <xref:System.Xml.Linq.Extensions.Remove%2A>método de extensão, o que fará isso para você.</xref:System.Xml.Linq.Extensions.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="40e33-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="40e33-107">O principal motivo para fazer isso é que a maioria das coleções que você recupera de uma árvore XML é gerada usando a execução adiada.</span><span class="sxs-lookup"><span data-stu-id="40e33-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="40e33-108">Se você não materializar essas coleções primeiro em uma lista, ou não usar os métodos de extensão, poderá encontrar uma determinada classe de bugs.</span><span class="sxs-lookup"><span data-stu-id="40e33-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="40e33-109">Para obter mais informações, consulte [misto declarativa código/código obrigatório apresenta erros (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="40e33-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="40e33-110">Os métodos a seguir removem nós e atributos de uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="40e33-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="40e33-111">Método</span><span class="sxs-lookup"><span data-stu-id="40e33-111">Method</span></span>|<span data-ttu-id="40e33-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="40e33-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="40e33-113">[XAttribute.Remove](https://msdn.microsoft.com/library/system.xml.linq.xattribute.remove\(v=vs.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="40e33-113">[XAttribute.Remove](https://msdn.microsoft.com/library/system.xml.linq.xattribute.remove\(v=vs.110\).aspx)</span></span>|<span data-ttu-id="40e33-114">Remove um <xref:System.Xml.Linq.XAttribute>de seu pai.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="40e33-114">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<span data-ttu-id="40e33-115">[XContainer.RemoveNodes](https://msdn.microsoft.com/library/system.xml.linq.xcontainer.removenodes\(v=vs.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="40e33-115">[XContainer.RemoveNodes](https://msdn.microsoft.com/library/system.xml.linq.xcontainer.removenodes\(v=vs.110\).aspx)</span></span>|<span data-ttu-id="40e33-116">Remove os nós filho de <xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="40e33-116">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<span data-ttu-id="40e33-117"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="40e33-117"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="40e33-118">Remove o conteúdo e os atributos de <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="40e33-118">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="40e33-119"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="40e33-119"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="40e33-120">Remove os atributos de <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="40e33-120">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="40e33-121"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="40e33-121"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="40e33-122">Se você passar `null` para o valor, esse método removerá o atributo.</span><span class="sxs-lookup"><span data-stu-id="40e33-122">If you pass `null` for value, then removes the attribute.</span></span>|  
|<span data-ttu-id="40e33-123"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="40e33-123"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="40e33-124">Se você passar `null` para o valor, esse método removerá o elemento filho.</span><span class="sxs-lookup"><span data-stu-id="40e33-124">If you pass `null` for value, then removes the child element.</span></span>|  
|<span data-ttu-id="40e33-125"><xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="40e33-125"><xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></span></span>|<span data-ttu-id="40e33-126">Remove um <xref:System.Xml.Linq.XNode>de seu pai.</xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="40e33-126">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<span data-ttu-id="40e33-127"><xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="40e33-127"><xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></span></span>|<span data-ttu-id="40e33-128">Remove cada atributo ou elemento na coleção de origem do respectivo elemento pai.</span><span class="sxs-lookup"><span data-stu-id="40e33-128">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="40e33-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="40e33-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="40e33-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="40e33-130">Description</span></span>  
 <span data-ttu-id="40e33-131">Este exemplo demonstra três abordagens para remover elementos.</span><span class="sxs-lookup"><span data-stu-id="40e33-131">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="40e33-132">Primeiro, ele remove um único elemento.</span><span class="sxs-lookup"><span data-stu-id="40e33-132">First, it removes a single element.</span></span> <span data-ttu-id="40e33-133">Segundo, ele recupera uma coleção de elementos, materializa-los usando o <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>operador e remove a coleção.</xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="40e33-133">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> operator, and removes the collection.</span></span> <span data-ttu-id="40e33-134">Por fim, ele recupera uma coleção de elementos e removê-los usando o <xref:System.Xml.Linq.Extensions.Remove%2A>método de extensão.</xref:System.Xml.Linq.Extensions.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="40e33-134">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="40e33-135">Para obter mais informações sobre o <xref:System.Linq.Enumerable.ToList%2A>operador, consulte [converter tipos de dados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</xref:System.Linq.Enumerable.ToList%2A></span><span class="sxs-lookup"><span data-stu-id="40e33-135">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="40e33-136">Código</span><span class="sxs-lookup"><span data-stu-id="40e33-136">Code</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1/>  
            <GrandChild2/>  
            <GrandChild3/>  
        </Child1>  
        <Child2>  
            <GrandChild4/>  
            <GrandChild5/>  
            <GrandChild6/>  
        </Child2>  
        <Child3>  
            <GrandChild7/>  
            <GrandChild8/>  
            <GrandChild9/>  
        </Child3>  
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
  
```  
  
### <a name="comments"></a><span data-ttu-id="40e33-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="40e33-137">Comments</span></span>  
 <span data-ttu-id="40e33-138">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="40e33-138">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 <span data-ttu-id="40e33-139">Observe que o primeiro elemento neto foi removido de `Child1`.</span><span class="sxs-lookup"><span data-stu-id="40e33-139">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="40e33-140">Todos os elementos neto foram removidos de `Child2` e de `Child3`.</span><span class="sxs-lookup"><span data-stu-id="40e33-140">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e33-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40e33-141">See Also</span></span>  
 [<span data-ttu-id="40e33-142">Modificando árvores XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40e33-142">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
