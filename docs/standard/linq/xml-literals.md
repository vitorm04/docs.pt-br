---
title: Literais XML em Visual Basic-LINQ to XML
description: Você pode criar uma árvore XML em Visual Basic usando literais XML e expressões inseridas. Expressões inseridas permite avaliar uma expressão e para inserir os resultados da expressão na árvore XML.
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: e3b1213672a6a7ddd71fcc38b4502108a6f49881
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551946"
---
# <a name="xml-literals-in-visual-basic-linq-to-xml"></a><span data-ttu-id="3355c-104">Literais XML em Visual Basic (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="3355c-104">XML Literals in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="3355c-105">Este artigo fornece informações sobre como criar árvores XML em Visual Basic usando literais XML e expressões inseridas.</span><span class="sxs-lookup"><span data-stu-id="3355c-105">This article provides information about creating XML trees in Visual Basic using XML literals and embedded expressions.</span></span>

## <a name="example-use-xml-literals-to-create-an-xml-tree"></a><span data-ttu-id="3355c-106">Exemplo: usar literais XML para criar uma árvore XML</span><span class="sxs-lookup"><span data-stu-id="3355c-106">Example: Use XML literals to create an XML tree</span></span>

<span data-ttu-id="3355c-107">O exemplo a seguir mostra como criar um <xref:System.Xml.Linq.XElement> , nesse caso `contacts` , com literais XML:</span><span class="sxs-lookup"><span data-stu-id="3355c-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`, with XML literals:</span></span>

```vb
Dim contacts As XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone>206-555-0144</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

## <a name="example-use-xml-literals-to-create-an-xelement-with-simple-content"></a><span data-ttu-id="3355c-108">Exemplo: usar literais XML para criar um XElement com conteúdo simples</span><span class="sxs-lookup"><span data-stu-id="3355c-108">Example: Use XML literals to create an XElement with simple content</span></span>

<span data-ttu-id="3355c-109">Você pode criar <xref:System.Xml.Linq.XElement> que contém o conteúdo simples, como segue:</span><span class="sxs-lookup"><span data-stu-id="3355c-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>

```vb
Dim n as XElement = <Customer>Adventure Works</Customer>
Console.WriteLine(n)
```

<span data-ttu-id="3355c-110">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="3355c-110">This example produces the following output:</span></span>

```xml
<Customer>Adventure Works</Customer>
```

## <a name="example-use-an-xml-literal-to-create-an-empty-element"></a><span data-ttu-id="3355c-111">Exemplo: usar um literal XML para criar um elemento vazio</span><span class="sxs-lookup"><span data-stu-id="3355c-111">Example: Use an XML literal to create an empty element</span></span>

<span data-ttu-id="3355c-112">Você pode criar <xref:System.Xml.Linq.XElement>vazia, como segue:</span><span class="sxs-lookup"><span data-stu-id="3355c-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>

```vb
Dim n As XElement = <Customer/>
Console.WriteLine(n)
```

<span data-ttu-id="3355c-113">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="3355c-113">This example produces the following output:</span></span>

```xml
<Customer />
```

## <a name="use-embedded-expressions-to-create-content"></a><span data-ttu-id="3355c-114">Usar expressões inseridas para criar conteúdo</span><span class="sxs-lookup"><span data-stu-id="3355c-114">Use embedded expressions to create content</span></span>

<span data-ttu-id="3355c-115">Um recurso importante de literais XML é que permitem expressões inseridas.</span><span class="sxs-lookup"><span data-stu-id="3355c-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="3355c-116">Expressões inseridas permite avaliar uma expressão e para inserir os resultados da expressão na árvore XML.</span><span class="sxs-lookup"><span data-stu-id="3355c-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="3355c-117">Se a expressão avaliada como um tipo de <xref:System.Xml.Linq.XElement>, um elemento é inserido na árvore.</span><span class="sxs-lookup"><span data-stu-id="3355c-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="3355c-118">Se a expressão avaliada como um tipo de <xref:System.Xml.Linq.XAttribute>, um atributo é inserido na árvore.</span><span class="sxs-lookup"><span data-stu-id="3355c-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="3355c-119">Você pode inserir elementos e atributos na árvore somente quando eles forem válidos.</span><span class="sxs-lookup"><span data-stu-id="3355c-119">You can insert elements and attributes into the tree only where they're valid.</span></span>

<span data-ttu-id="3355c-120">é importante observar que apenas uma única expressão pode entrar em uma expressão inserida.</span><span class="sxs-lookup"><span data-stu-id="3355c-120">it's important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="3355c-121">Não é possível inserir várias instruções.</span><span class="sxs-lookup"><span data-stu-id="3355c-121">You can't embed multiple statements.</span></span> <span data-ttu-id="3355c-122">Se uma expressão ultrapassa de uma única linha, você deve usar o caractere de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="3355c-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>

<span data-ttu-id="3355c-123">Se você usar uma expressão inserida para adicionar nós existentes (incluindo elementos) e atributos para uma nova árvore XML e os nós existentes já parented, os nós são clonados.</span><span class="sxs-lookup"><span data-stu-id="3355c-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="3355c-124">Os nós recentemente clonados são anexados a nova árvore XML.</span><span class="sxs-lookup"><span data-stu-id="3355c-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="3355c-125">Se os nós existentes não forem pais, os nós serão simplesmente anexados à nova árvore XML.</span><span class="sxs-lookup"><span data-stu-id="3355c-125">If the existing nodes aren't parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="3355c-126">O último exemplo neste artigo demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="3355c-126">The last example in this article demonstrates this.</span></span>

## <a name="example-use-an-embedded-expression-to-insert-an-element"></a><span data-ttu-id="3355c-127">Exemplo: usar uma expressão inserida para inserir um elemento</span><span class="sxs-lookup"><span data-stu-id="3355c-127">Example: Use an embedded expression to insert an element</span></span>

<span data-ttu-id="3355c-128">O exemplo a seguir usa uma expressão inserida para inserir um elemento na árvore:</span><span class="sxs-lookup"><span data-stu-id="3355c-128">The following example uses an embedded expression to insert an element into the tree:</span></span>

```vb
xmlTree1 As XElement = _
    <Root>
        <Child>Contents</Child>
    </Root>
Dim xmlTree2 As XElement = _
    <Root>
        <%= xmlTree1.<Child> %>
    </Root>
Console.WriteLine(xmlTree2)
```

<span data-ttu-id="3355c-129">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="3355c-129">This example produces the following output:</span></span>

```xml
<Root>
  <Child>Contents</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-for-content"></a><span data-ttu-id="3355c-130">Exemplo: usar uma expressão inserida para conteúdo</span><span class="sxs-lookup"><span data-stu-id="3355c-130">Example: Use an embedded expression for content</span></span>

<span data-ttu-id="3355c-131">Você pode usar uma expressão inserida para fornecer o conteúdo de um elemento:</span><span class="sxs-lookup"><span data-stu-id="3355c-131">You can use an embedded expression to supply the content of an element:</span></span>

```vb
Dim str As String
str = "Some content"
Dim root As XElement = <Root><%= str %></Root>
Console.WriteLine(root)
```

<span data-ttu-id="3355c-132">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="3355c-132">This example produces the following output:</span></span>

```xml
<Root>Some content</Root>
```

## <a name="example-use-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="3355c-133">Exemplo: usar uma consulta LINQ em uma expressão inserida</span><span class="sxs-lookup"><span data-stu-id="3355c-133">Example: Use a LINQ query in an embedded expression</span></span>

<span data-ttu-id="3355c-134">Você pode usar os resultados de uma consulta LINQ para fornecer o conteúdo de um elemento:</span><span class="sxs-lookup"><span data-stu-id="3355c-134">You can use the results of a LINQ query to provide the content of an element:</span></span>

```vb
Dim arr As Integer() = {1, 2, 3}

Dim n As XElement = _
    <Root>
        <%= From i In arr Select <Child><%= i %></Child> %>
    </Root>

Console.WriteLine(n)
```

<span data-ttu-id="3355c-135">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="3355c-135">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Child>3</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-to-provide-node-names"></a><span data-ttu-id="3355c-136">Exemplo: usar uma expressão inserida para fornecer nomes de nós</span><span class="sxs-lookup"><span data-stu-id="3355c-136">Example: Use an embedded expression to provide node names</span></span>

<span data-ttu-id="3355c-137">Você também pode usar uma expressão inserida para calcular nomes de atributo, valores de atributo, nomes de elementos e valores de elementos:</span><span class="sxs-lookup"><span data-stu-id="3355c-137">You can also use an embedded expression to calculate attribute names, attribute values, element names, and element values:</span></span>

```vb
Dim eleName As String = "ele"
Dim attName As String = "att"
Dim attValue As String = "aValue"
Dim eleValue As String = "eValue"
Dim n As XElement = _
    <Root <%= attName %>=<%= attValue %>>
        <<%= eleName %>>
            <%= eleValue %>
        </>
    </Root>
Console.WriteLine(n)
```

<span data-ttu-id="3355c-138">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="3355c-138">This example produces the following output:</span></span>

```xml
<Root att="aValue">
  <ele>eValue</ele>
</Root>
```

## <a name="example-use-an-embedded-expression-to-clone-and-attach-nodes"></a><span data-ttu-id="3355c-139">Exemplo: usar uma expressão inserida para clonar e anexar nós</span><span class="sxs-lookup"><span data-stu-id="3355c-139">Example: Use an embedded expression to clone and attach nodes</span></span>

<span data-ttu-id="3355c-140">Como mencionado anteriormente, se você usar uma expressão inserida para adicionar nós existentes (incluindo elementos) e atributos a uma nova árvore XML, e se os nós que estão sendo adicionados a nós já estiverem pais, os nós serão clonados e os clones serão anexados à nova árvore XML.</span><span class="sxs-lookup"><span data-stu-id="3355c-140">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, and if the nodes being added nodes are already parented, the nodes are cloned and the clones are attached to the new XML tree.</span></span> <span data-ttu-id="3355c-141">Se os nós existentes não forem pais, eles serão simplesmente anexados à nova árvore XML.</span><span class="sxs-lookup"><span data-stu-id="3355c-141">If the existing nodes aren't parented, they're simply attached to the new XML tree.</span></span>

<span data-ttu-id="3355c-142">O código a seguir demonstra o comportamento quando você adiciona um elemento parented a uma árvore, e quando você adiciona um elemento sem o pai a uma árvore.</span><span class="sxs-lookup"><span data-stu-id="3355c-142">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

```vb
' Create a tree with a child element.
Dim xmlTree1 As XElement = _
    <Root>
        <Child1>1</Child1>
    </Root>

' Create an element that's not parented.
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

<span data-ttu-id="3355c-143">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="3355c-143">This example produces the following output:</span></span>

```output
Child1 was cloned
Child2 was attached
```

## <a name="see-also"></a><span data-ttu-id="3355c-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="3355c-144">See also</span></span>

- [<span data-ttu-id="3355c-145">Construção funcional</span><span class="sxs-lookup"><span data-stu-id="3355c-145">Functional construction</span></span>](functional-construction.md)
