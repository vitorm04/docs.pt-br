---
title: Remover elementos, atributos e nós de uma árvore XML-LINQ to XML
description: Saiba como remover elementos, atributos e outros tipos de nós de uma árvore XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 1a7c10892ccf1baaab7dde700266a134abe727de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552071"
---
# <a name="remove-elements-attributes-and-nodes-from-an-xml-tree-linq-to-xml"></a><span data-ttu-id="ea7af-103">Remover elementos, atributos e nós de uma árvore XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ea7af-103">Remove elements, attributes, and nodes from an XML tree (LINQ to XML)</span></span>

<span data-ttu-id="ea7af-104">Você pode modificar uma árvore XML, remover elementos, atributos e outros tipos de nós.</span><span class="sxs-lookup"><span data-stu-id="ea7af-104">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="ea7af-105">Remover um único elemento ou um único atributo de um documento XML é simples.</span><span class="sxs-lookup"><span data-stu-id="ea7af-105">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="ea7af-106">No entanto, ao remover coleções de elementos ou atributos, você deve primeiro materializar uma coleção em uma lista e depois excluir os elementos ou os atributos da lista.</span><span class="sxs-lookup"><span data-stu-id="ea7af-106">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="ea7af-107">A melhor abordagem é usar o <xref:System.Xml.Linq.Extensions.Remove%2A> método de extensão para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="ea7af-107">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method to do this.</span></span>

<span data-ttu-id="ea7af-108">O principal motivo para usar essa abordagem é que a maioria das coleções recuperadas de uma árvore XML são geradas usando a execução adiada.</span><span class="sxs-lookup"><span data-stu-id="ea7af-108">The main reason to use this approach is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="ea7af-109">Se você não os materializar primeiro em uma lista ou se não usar os métodos de extensão, poderá encontrar uma determinada classe de bugs.</span><span class="sxs-lookup"><span data-stu-id="ea7af-109">If you don't first materialize them into a list, or if you don't use the extension methods, you may encounter a certain class of bugs.</span></span> <span data-ttu-id="ea7af-110">Para obter mais informações, consulte [bugs de código declarativo/imperativo misto](mixed-declarative-imperative-code-bugs.md).</span><span class="sxs-lookup"><span data-stu-id="ea7af-110">For more information, see [Mixed declarative/imperative code bugs](mixed-declarative-imperative-code-bugs.md).</span></span>

<span data-ttu-id="ea7af-111">Os métodos a seguir removem nós e atributos de uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="ea7af-111">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="ea7af-112">Método</span><span class="sxs-lookup"><span data-stu-id="ea7af-112">Method</span></span>|<span data-ttu-id="ea7af-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea7af-113">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="ea7af-114">Remova um <xref:System.Xml.Linq.XAttribute> de seu pai.</span><span class="sxs-lookup"><span data-stu-id="ea7af-114">Remove an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="ea7af-115">Remova os nós filho de um <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="ea7af-115">Remove the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="ea7af-116">Remova o conteúdo e os atributos de um <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="ea7af-116">Remove content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="ea7af-117">Remova os atributos de um <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="ea7af-117">Remove the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="ea7af-118">Remova o atributo se você passar o valor `null` .</span><span class="sxs-lookup"><span data-stu-id="ea7af-118">Remove the attribute if you pass the value `null`.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="ea7af-119">Remova o elemento filho se você passar o valor `null` .</span><span class="sxs-lookup"><span data-stu-id="ea7af-119">Remove the child element if you pass the value `null`.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="ea7af-120">Remova um <xref:System.Xml.Linq.XNode> de seu pai.</span><span class="sxs-lookup"><span data-stu-id="ea7af-120">Remove an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="ea7af-121">Remova todos os atributos ou elementos na coleção de origem do elemento pai.</span><span class="sxs-lookup"><span data-stu-id="ea7af-121">Remove every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example-remove-a-single-element-and-remove-a-collection-of-elements-in-two-ways"></a><span data-ttu-id="ea7af-122">Exemplo: remover um único elemento e remover uma coleção de elementos de duas maneiras</span><span class="sxs-lookup"><span data-stu-id="ea7af-122">Example: Remove a single element, and remove a collection of elements in two ways</span></span>

<span data-ttu-id="ea7af-123">Este exemplo demonstra três abordagens para remover elementos.</span><span class="sxs-lookup"><span data-stu-id="ea7af-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="ea7af-124">Primeiro, ele remove um único elemento.</span><span class="sxs-lookup"><span data-stu-id="ea7af-124">First, it removes a single element.</span></span> <span data-ttu-id="ea7af-125">Em segundo lugar, ele recupera uma coleção de elementos, materializa-os usando o <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operador e, em seguida, remove a coleção.</span><span class="sxs-lookup"><span data-stu-id="ea7af-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and then removes the collection.</span></span> <span data-ttu-id="ea7af-126">Por último, recupera uma coleção de elementos e remove-a usando o método de extensão <xref:System.Xml.Linq.Extensions.Remove%2A>.</span><span class="sxs-lookup"><span data-stu-id="ea7af-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="ea7af-127">Para obter mais informações sobre o <xref:System.Linq.Enumerable.ToList%2A> operador, consulte [convertendo tipos de dados (C#)](../../csharp/programming-guide/concepts/linq/converting-data-types.md) e [convertendo tipos de dados (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="ea7af-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](../../csharp/programming-guide/concepts/linq/converting-data-types.md) and [Converting Data Types (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>

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

<span data-ttu-id="ea7af-128">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="ea7af-128">This example produces the following output:</span></span>

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

<span data-ttu-id="ea7af-129">O primeiro elemento neto foi removido de `Child1` e todos os elementos netos foram removidos de `Child2` e de `Child3` .</span><span class="sxs-lookup"><span data-stu-id="ea7af-129">The first grandchild element was removed from `Child1`, and all grandchildren elements were removed from `Child2` and from `Child3`.</span></span>
