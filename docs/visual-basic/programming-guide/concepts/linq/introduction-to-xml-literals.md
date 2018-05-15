---
title: Introdução a literais XML no Visual Basic2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: bac0a4a297dcecce5465e5a1a1c02e4cbc9848a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a><span data-ttu-id="1a44e-102">Introdução a literais XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1a44e-102">Introduction to XML Literals in Visual Basic</span></span>
<span data-ttu-id="1a44e-103">Esta seção fornece informações sobre como criar árvores XML no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1a44e-103">This section provides information about creating XML trees in Visual Basic.</span></span>  
  
 <span data-ttu-id="1a44e-104">Para obter informações sobre como usar os resultados de consultas LINQ como o conteúdo de uma árvore XML, consulte [construção funcional (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1a44e-104">For information about using the results of LINQ queries as the content for an XML tree, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="1a44e-105">Para obter mais informações sobre literais XML no Visual Basic, consulte [visão geral de LINQ to XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1a44e-105">For more information on XML literals in Visual Basic, see [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="1a44e-106">Criando árvores XML</span><span class="sxs-lookup"><span data-stu-id="1a44e-106">Creating XML Trees</span></span>  
 <span data-ttu-id="1a44e-107">O exemplo a seguir mostra como criar <xref:System.Xml.Linq.XElement>, nesse caso `contacts`:</span><span class="sxs-lookup"><span data-stu-id="1a44e-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`:</span></span>  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a><span data-ttu-id="1a44e-108">Criando um XElement com conteúdo simples</span><span class="sxs-lookup"><span data-stu-id="1a44e-108">Creating an XElement with Simple Content</span></span>  
 <span data-ttu-id="1a44e-109">Você pode criar <xref:System.Xml.Linq.XElement> que contém o conteúdo simples, como segue:</span><span class="sxs-lookup"><span data-stu-id="1a44e-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 <span data-ttu-id="1a44e-110">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="1a44e-110">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="1a44e-111">Criando um elemento vazio</span><span class="sxs-lookup"><span data-stu-id="1a44e-111">Creating an Empty Element</span></span>  
 <span data-ttu-id="1a44e-112">Você pode criar <xref:System.Xml.Linq.XElement>vazia, como segue:</span><span class="sxs-lookup"><span data-stu-id="1a44e-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="1a44e-113">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="1a44e-113">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a><span data-ttu-id="1a44e-114">Usando expressões inseridas</span><span class="sxs-lookup"><span data-stu-id="1a44e-114">Using Embedded Expressions</span></span>  
 <span data-ttu-id="1a44e-115">Um recurso importante de literais XML é que permitem expressões inseridas.</span><span class="sxs-lookup"><span data-stu-id="1a44e-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="1a44e-116">Expressões inseridas permite avaliar uma expressão e para inserir os resultados da expressão na árvore XML.</span><span class="sxs-lookup"><span data-stu-id="1a44e-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="1a44e-117">Se a expressão avaliada como um tipo de <xref:System.Xml.Linq.XElement>, um elemento é inserido na árvore.</span><span class="sxs-lookup"><span data-stu-id="1a44e-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="1a44e-118">Se a expressão avaliada como um tipo de <xref:System.Xml.Linq.XAttribute>, um atributo é inserido na árvore.</span><span class="sxs-lookup"><span data-stu-id="1a44e-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="1a44e-119">Você pode inserir os elementos e atributos na árvore apenas onde são válidos.</span><span class="sxs-lookup"><span data-stu-id="1a44e-119">You can insert elements and attributes into the tree only where they are valid.</span></span>  
  
 <span data-ttu-id="1a44e-120">É importante observar que apenas uma única expressão pode inserir em uma expressão inserida.</span><span class="sxs-lookup"><span data-stu-id="1a44e-120">It is important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="1a44e-121">Você não pode inserir várias instruções.</span><span class="sxs-lookup"><span data-stu-id="1a44e-121">You cannot embed multiple statements.</span></span> <span data-ttu-id="1a44e-122">Se uma expressão ultrapassa de uma única linha, você deve usar o caractere de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="1a44e-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>  
  
 <span data-ttu-id="1a44e-123">Se você usar uma expressão inserida para adicionar nós existentes (incluindo elementos) e atributos para uma nova árvore XML e os nós existentes já parented, os nós são clonados.</span><span class="sxs-lookup"><span data-stu-id="1a44e-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="1a44e-124">Os nós recentemente clonados são anexados a nova árvore XML.</span><span class="sxs-lookup"><span data-stu-id="1a44e-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="1a44e-125">Se os nós existentes não parented, os nós estão conectados somente para a nova árvore XML.</span><span class="sxs-lookup"><span data-stu-id="1a44e-125">If the existing nodes are not parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="1a44e-126">O último exemplo deste tópico demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="1a44e-126">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="1a44e-127">O exemplo a seguir usa uma expressão inserida para inserir um elemento na árvore:</span><span class="sxs-lookup"><span data-stu-id="1a44e-127">The following example uses an embedded expression to insert an element into the tree:</span></span>  
  
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
  
 <span data-ttu-id="1a44e-128">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="1a44e-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a><span data-ttu-id="1a44e-129">Usando expressões inseridas para o conteúdo</span><span class="sxs-lookup"><span data-stu-id="1a44e-129">Using Embedded Expressions for Content</span></span>  
 <span data-ttu-id="1a44e-130">Você pode usar uma expressão inserida para fornecer o conteúdo de um elemento:</span><span class="sxs-lookup"><span data-stu-id="1a44e-130">You can use an embedded expression to supply the content of an element:</span></span>  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="1a44e-131">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="1a44e-131">This example produces the following output:</span></span>  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="1a44e-132">Usando uma consulta LINQ em uma expressão inserida</span><span class="sxs-lookup"><span data-stu-id="1a44e-132">Using a LINQ Query in an Embedded Expression</span></span>  
 <span data-ttu-id="1a44e-133">Você pode usar os resultados de uma consulta LINQ para o conteúdo de um elemento:</span><span class="sxs-lookup"><span data-stu-id="1a44e-133">You can use the results of a LINQ query for the content of an element:</span></span>  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="1a44e-134">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="1a44e-134">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a><span data-ttu-id="1a44e-135">Usando expressões inseridas para nomes de nó</span><span class="sxs-lookup"><span data-stu-id="1a44e-135">Using Embedded Expressions for Node Names</span></span>  
 <span data-ttu-id="1a44e-136">Você também pode usar expressões inseridas para calcular nomes de atributo, valores de atributo, nomes de elemento, e valores de elemento:</span><span class="sxs-lookup"><span data-stu-id="1a44e-136">You can also use embedded expressions to calculate attribute names, attribute values, element names, and element values:</span></span>  
  
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
  
 <span data-ttu-id="1a44e-137">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="1a44e-137">This example produces the following output:</span></span>  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a><span data-ttu-id="1a44e-138">Clonagem contra. Anexar</span><span class="sxs-lookup"><span data-stu-id="1a44e-138">Cloning vs. Attaching</span></span>  
 <span data-ttu-id="1a44e-139">Como mencionado anteriormente, se você usar uma expressão inserida para adicionar nós existentes (incluindo elementos) e atributos para uma nova árvore XML, se os nós existentes já parented, os nós é clonados e os nós recentemente clonados são anexados a nova árvore XML.</span><span class="sxs-lookup"><span data-stu-id="1a44e-139">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, if the existing nodes are already parented, the nodes are cloned and the newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="1a44e-140">Se os nós existentes não parented, eles estão conectados somente para a nova árvore XML.</span><span class="sxs-lookup"><span data-stu-id="1a44e-140">If the existing nodes are not parented, they are simply attached to the new XML tree.</span></span>  
  
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
  
 <span data-ttu-id="1a44e-141">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="1a44e-141">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a44e-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a44e-142">See Also</span></span>  
 [<span data-ttu-id="1a44e-143">Criando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a44e-143">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
