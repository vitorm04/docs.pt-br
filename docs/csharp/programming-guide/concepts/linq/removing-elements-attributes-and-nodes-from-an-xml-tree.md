---
title: Removendo elementos, atributos e nós de uma árvore XML (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 9ce63ce6a4ef75dedc788efca11e8dd2bdb471eb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45610146"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="4d04a-102">Removendo elementos, atributos e nós de uma árvore XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4d04a-102">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>
<span data-ttu-id="4d04a-103">Você pode modificar uma árvore XML, remover elementos, atributos e outros tipos de nós.</span><span class="sxs-lookup"><span data-stu-id="4d04a-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="4d04a-104">Remover um único elemento ou um único atributo de um documento XML é simples.</span><span class="sxs-lookup"><span data-stu-id="4d04a-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="4d04a-105">No entanto, ao remover coleções de elementos ou atributos, você deve primeiro materializar uma coleção em uma lista e depois excluir os elementos ou os atributos da lista.</span><span class="sxs-lookup"><span data-stu-id="4d04a-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="4d04a-106">A melhor abordagem é usar o método de extensão <xref:System.Xml.Linq.Extensions.Remove%2A>, que fará isso para você.</span><span class="sxs-lookup"><span data-stu-id="4d04a-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="4d04a-107">O principal motivo para fazer isso é que a maioria das coleções que você recupera de uma árvore XML é gerada usando a execução adiada.</span><span class="sxs-lookup"><span data-stu-id="4d04a-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="4d04a-108">Se você não materializar essas coleções primeiro em uma lista, ou não usar os métodos de extensão, poderá encontrar uma determinada classe de bugs.</span><span class="sxs-lookup"><span data-stu-id="4d04a-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="4d04a-109">Para obter mais informações, consulte [Bugs misturados de código declarativo/código imperativo (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4d04a-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="4d04a-110">Os métodos a seguir removem nós e atributos de uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="4d04a-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="4d04a-111">Método</span><span class="sxs-lookup"><span data-stu-id="4d04a-111">Method</span></span>|<span data-ttu-id="4d04a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d04a-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="4d04a-113">Remove uma classe <xref:System.Xml.Linq.XAttribute> de seu pai.</span><span class="sxs-lookup"><span data-stu-id="4d04a-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="4d04a-114">Remove os nós filho de uma classe <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="4d04a-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="4d04a-115">Remove o conteúdo e os atributos de uma classe <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="4d04a-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="4d04a-116">Remove os atributos de uma classe <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="4d04a-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="4d04a-117">Se você passar `null` para o valor, esse método removerá o atributo.</span><span class="sxs-lookup"><span data-stu-id="4d04a-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="4d04a-118">Se você passar `null` para o valor, esse método removerá o elemento filho.</span><span class="sxs-lookup"><span data-stu-id="4d04a-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="4d04a-119">Remove uma classe <xref:System.Xml.Linq.XNode> de seu pai.</span><span class="sxs-lookup"><span data-stu-id="4d04a-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="4d04a-120">Remove cada atributo ou elemento na coleção de origem do respectivo elemento pai.</span><span class="sxs-lookup"><span data-stu-id="4d04a-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4d04a-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d04a-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4d04a-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d04a-122">Description</span></span>  
 <span data-ttu-id="4d04a-123">Este exemplo demonstra três abordagens para remover elementos.</span><span class="sxs-lookup"><span data-stu-id="4d04a-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="4d04a-124">Primeiro, ele remove um único elemento.</span><span class="sxs-lookup"><span data-stu-id="4d04a-124">First, it removes a single element.</span></span> <span data-ttu-id="4d04a-125">Segundo, ele recupera uma coleção de elementos, materializa essa coleção usando o operador <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> e remove a coleção.</span><span class="sxs-lookup"><span data-stu-id="4d04a-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="4d04a-126">Por último, recupera uma coleção de elementos e remove-a usando o método de extensão <xref:System.Xml.Linq.Extensions.Remove%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d04a-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="4d04a-127">Para obter mais informações sobre o operador <xref:System.Linq.Enumerable.ToList%2A>, consulte [Convertendo Tipos de Dados (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="4d04a-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="4d04a-128">Código</span><span class="sxs-lookup"><span data-stu-id="4d04a-128">Code</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
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
</Root>");  
root.Element("Child1").Element("GrandChild1").Remove();  
root.Element("Child2").Elements().ToList().Remove();  
root.Element("Child3").Elements().Remove();  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a><span data-ttu-id="4d04a-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d04a-129">Comments</span></span>  
 <span data-ttu-id="4d04a-130">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="4d04a-130">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="4d04a-131">Observe que o primeiro elemento neto foi removido de `Child1`.</span><span class="sxs-lookup"><span data-stu-id="4d04a-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="4d04a-132">Todos os elementos neto foram removidos de `Child2` e de `Child3`.</span><span class="sxs-lookup"><span data-stu-id="4d04a-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d04a-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d04a-133">See Also</span></span>

- [<span data-ttu-id="4d04a-134">Modificando árvores XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4d04a-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
