---
title: Visão geral da classe XElement
description: A classe XElement representa elementos XML. Você pode usá-lo para criar e alterar elementos, adicionar atributos e filhos e serializar.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 325afd09661532fe44aecf89fe9784520274638e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551921"
---
# <a name="xelement-class-overview"></a><span data-ttu-id="1a027-104">Visão geral da classe XElement</span><span class="sxs-lookup"><span data-stu-id="1a027-104">XElement class overview</span></span>

<span data-ttu-id="1a027-105">A <xref:System.Xml.Linq.XElement> classe é uma das classes fundamentais em LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="1a027-105">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in LINQ to XML.</span></span> <span data-ttu-id="1a027-106">Representa um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="1a027-106">It represents an XML element.</span></span> <span data-ttu-id="1a027-107">A lista a seguir mostra como você pode usar essa classe para:</span><span class="sxs-lookup"><span data-stu-id="1a027-107">The following list shows what you can use this class for:</span></span>

- <span data-ttu-id="1a027-108">Criar elementos.</span><span class="sxs-lookup"><span data-stu-id="1a027-108">Create elements.</span></span>
- <span data-ttu-id="1a027-109">Altere o conteúdo do elemento.</span><span class="sxs-lookup"><span data-stu-id="1a027-109">Change the content of the element.</span></span>
- <span data-ttu-id="1a027-110">Adicionar, alterar ou excluir elementos filho.</span><span class="sxs-lookup"><span data-stu-id="1a027-110">Add, change, or delete child elements.</span></span>
- <span data-ttu-id="1a027-111">Adicionar atributos a um elemento.</span><span class="sxs-lookup"><span data-stu-id="1a027-111">Add attributes to an element.</span></span>
- <span data-ttu-id="1a027-112">Serialize o conteúdo de um elemento na forma de texto.</span><span class="sxs-lookup"><span data-stu-id="1a027-112">Serialize the contents of an element in text form.</span></span>

<span data-ttu-id="1a027-113">Você também pode interoperar com outras classes no <xref:System.Xml?displayProperty=nameWithType>, como <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> e <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="1a027-113">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

<span data-ttu-id="1a027-114">Este artigo descreve a funcionalidade fornecida pela <xref:System.Xml.Linq.XElement> classe.</span><span class="sxs-lookup"><span data-stu-id="1a027-114">This article describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>

## <a name="construct-xml-trees"></a><span data-ttu-id="1a027-115">Construir árvores XML</span><span class="sxs-lookup"><span data-stu-id="1a027-115">Construct XML trees</span></span>

<span data-ttu-id="1a027-116">Você pode construir árvores XML de maneiras diferentes, incluindo as seguintes:</span><span class="sxs-lookup"><span data-stu-id="1a027-116">You can construct XML trees in different ways, including the following:</span></span>

- <span data-ttu-id="1a027-117">Você pode construir uma árvore XML em código.</span><span class="sxs-lookup"><span data-stu-id="1a027-117">You can construct an XML tree in code.</span></span> <span data-ttu-id="1a027-118">Para obter mais informações, consulte [árvores XML](functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="1a027-118">For more information, see [XML trees](functional-construction.md).</span></span>
- <span data-ttu-id="1a027-119">Você pode analisar XML de várias fontes, incluindo <xref:System.IO.TextReader>, arquivos de texto ou um endereço Web (URL).</span><span class="sxs-lookup"><span data-stu-id="1a027-119">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="1a027-120">Para obter mais informações, consulte [Parse XML](parse-string.md).</span><span class="sxs-lookup"><span data-stu-id="1a027-120">For more information, see [Parse XML](parse-string.md).</span></span>
- <span data-ttu-id="1a027-121">Você pode usar um <xref:System.Xml.XmlReader> para popular a árvore.</span><span class="sxs-lookup"><span data-stu-id="1a027-121">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="1a027-122">Para obter mais informações, consulte <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="1a027-122">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>
- <span data-ttu-id="1a027-123">Se você tiver um módulo que possa gravar conteúdo em um <xref:System.Xml.XmlWriter> , poderá usar o <xref:System.Xml.Linq.XContainer.CreateWriter%2A> método para criar um gravador, passar o gravador para o módulo e, em seguida, usar o conteúdo que é gravado no <xref:System.Xml.XmlWriter> para popular a árvore XML.</span><span class="sxs-lookup"><span data-stu-id="1a027-123">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that's written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>

<span data-ttu-id="1a027-124">O exemplo a seguir cria uma árvore.</span><span class="sxs-lookup"><span data-stu-id="1a027-124">The following example creates a tree.</span></span> <span data-ttu-id="1a027-125">A versão C# usa criações de elemento aninhado.</span><span class="sxs-lookup"><span data-stu-id="1a027-125">The C# version uses nested element creations.</span></span> <span data-ttu-id="1a027-126">Você pode usar a mesma técnica em Visual Basic, mas este exemplo usa literais XML.</span><span class="sxs-lookup"><span data-stu-id="1a027-126">You can use the same technique in Visual Basic, but this example uses XML literals.</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

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

<span data-ttu-id="1a027-127">Você também pode usar uma consulta LINQ to XML para popular uma árvore XML, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1a027-127">You can also use a LINQ to XML query to populate an XML tree, as shown in the following example:</span></span>

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where el.Value > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

<span data-ttu-id="1a027-128">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="1a027-128">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="serialize-xml-trees"></a><span data-ttu-id="1a027-129">Serializar árvores XML</span><span class="sxs-lookup"><span data-stu-id="1a027-129">Serialize XML trees</span></span>

<span data-ttu-id="1a027-130">Você pode serializar a árvore XML para um <xref:System.IO.File>, um <xref:System.IO.TextWriter> ou um <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="1a027-130">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="1a027-131">Para obter mais informações, consulte [Serialize árvores XML](preserve-white-space-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="1a027-131">For more information, see [Serialize XML trees](preserve-white-space-serializing.md).</span></span>

## <a name="retrieve-xml-data-via-axis-methods"></a><span data-ttu-id="1a027-132">Recuperar dados XML por meio de métodos de eixo</span><span class="sxs-lookup"><span data-stu-id="1a027-132">Retrieve XML data via axis methods</span></span>

<span data-ttu-id="1a027-133">Você pode usar métodos de eixo para recuperar atributos, elementos filho, elementos descendentes e elementos ancestrais.</span><span class="sxs-lookup"><span data-stu-id="1a027-133">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="1a027-134">LINQ to XML consultas operam em métodos de eixo e fornecem várias maneiras flexíveis e poderosas de navegar e processar uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="1a027-134">LINQ to XML queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>

<span data-ttu-id="1a027-135">Para obter mais informações, consulte [visão geral dos eixos de LINQ to XML](linq-xml-axes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1a027-135">For more information, see [LINQ to XML axes overview](linq-xml-axes-overview.md).</span></span>

## <a name="query-xml-trees"></a><span data-ttu-id="1a027-136">Consultar árvores XML</span><span class="sxs-lookup"><span data-stu-id="1a027-136">Query XML trees</span></span>

<span data-ttu-id="1a027-137">Você pode escrever LINQ to XML consultas que extraem dados de uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="1a027-137">You can write LINQ to XML queries that extract data from an XML tree.</span></span>

<span data-ttu-id="1a027-138">Para obter mais informações, consulte [visão geral das árvores XML de consulta](query-xml-trees-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1a027-138">For more information, see [Query XML trees overview](query-xml-trees-overview.md).</span></span>

## <a name="modify-xml-trees"></a><span data-ttu-id="1a027-139">Modificar árvores XML</span><span class="sxs-lookup"><span data-stu-id="1a027-139">Modify XML trees</span></span>

<span data-ttu-id="1a027-140">Você pode modificar um elemento de diferentes maneiras, incluindo a alteração de seu conteúdo ou atributos.</span><span class="sxs-lookup"><span data-stu-id="1a027-140">You can modify an element in different ways, including changing its content or attributes.</span></span> <span data-ttu-id="1a027-141">Você também pode remover um elemento de seu pai.</span><span class="sxs-lookup"><span data-stu-id="1a027-141">You can also remove an element from its parent.</span></span>

<span data-ttu-id="1a027-142">Para obter mais informações, consulte [Modify XML Trees](in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="1a027-142">For more information, see [Modify XML trees](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a027-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="1a027-143">See also</span></span>

- [<span data-ttu-id="1a027-144">Visão geral da programação de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="1a027-144">LINQ to XML programming overview</span></span>](functional-vs-procedural-programming.md)
