---
title: Visão geral-LINQ to XML
description: O LINQ to XML fornece uma interface de programação XML na memória que é baseada em recursos do .NET e comparável a uma API DOM atualizada.
ms.date: 10/30/2018
dev_langs:
- csharp
- vb
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: f805d757c9059a07988c6cb16e41ffed017fe853
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551983"
---
# <a name="linq-to-xml-overview"></a><span data-ttu-id="be771-103">Visão geral de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="be771-103">LINQ to XML overview</span></span>

<span data-ttu-id="be771-104">O LINQ to XML fornece uma interface de programação XML na memória que aproveita a .NET LINQ (Consulta Integrada à Linguagem) Framework.</span><span class="sxs-lookup"><span data-stu-id="be771-104">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="be771-105">O LINQ to XML usa os recursos do .NET e pode ser comparado a uma interface de programação XML de Modelo de Objeto do Documento (DOM) atualizada e reprojetada.</span><span class="sxs-lookup"><span data-stu-id="be771-105">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span>

<span data-ttu-id="be771-106">O XML tem sido amplamente adotado como um modo de formatar dados em muitos contextos.</span><span class="sxs-lookup"><span data-stu-id="be771-106">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="be771-107">Por exemplo, você pode encontrar XML na Web, em arquivos de configuração, em arquivos do Microsoft Office Word e em bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="be771-107">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

<span data-ttu-id="be771-108">LINQ to XML é uma abordagem atualizada e reprojetada para programação com XML.</span><span class="sxs-lookup"><span data-stu-id="be771-108">LINQ to XML is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="be771-109">Ele fornece os recursos de modificação de documentos na memória do Modelo de Objeto do Documento (DOM) e oferece suporte a expressões de consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="be771-109">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span> <span data-ttu-id="be771-110">Embora essas expressões de consulta sejam sintaticamente diferentes de XPath, elas oferecem uma funcionalidade semelhante.</span><span class="sxs-lookup"><span data-stu-id="be771-110">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="be771-111">Desenvolvedores de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="be771-111">LINQ to XML developers</span></span>

<span data-ttu-id="be771-112">LINQ to XML tem como alvo uma variedade de desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="be771-112">LINQ to XML targets a variety of developers.</span></span> <span data-ttu-id="be771-113">Para um desenvolvedor médio que quer apenas fazer algo, LINQ to XML torna o XML mais fácil fornecendo uma experiência de consulta semelhante ao SQL.</span><span class="sxs-lookup"><span data-stu-id="be771-113">For an average developer who just wants to get something done, LINQ to XML makes XML easier by providing a query experience that's similar to SQL.</span></span> <span data-ttu-id="be771-114">Com apenas um pouco de estudo, os programadores podem aprender a escrever consultas sucintas e eficientes na linguagem de programação de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="be771-114">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="be771-115">Os desenvolvedores profissionais podem usar LINQ to XML para aumentar muito sua produtividade.</span><span class="sxs-lookup"><span data-stu-id="be771-115">Professional developers can use LINQ to XML to greatly increase their productivity.</span></span> <span data-ttu-id="be771-116">Com LINQ to XML, eles podem escrever menos código que seja mais expressivo, mais compacto e mais poderoso.</span><span class="sxs-lookup"><span data-stu-id="be771-116">With LINQ to XML, they can write less code that's more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="be771-117">Eles podem usar expressões de consulta de vários domínios de dados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="be771-117">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="linq-to-xml-is-an-xml-programming-interface"></a><span data-ttu-id="be771-118">LINQ to XML é uma interface de programação XML</span><span class="sxs-lookup"><span data-stu-id="be771-118">LINQ to XML is an XML programming interface</span></span>

<span data-ttu-id="be771-119">O LINQ to XML é uma interface de programação XML na memória, habilitada para LINQ, que permite trabalhar com XML de dentro das linguagens de programação .NET.</span><span class="sxs-lookup"><span data-stu-id="be771-119">LINQ to XML is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET programming languages.</span></span>

<span data-ttu-id="be771-120">LINQ to XML é como o Modelo de Objeto do Documento (DOM), no qual ele coloca o documento XML na memória.</span><span class="sxs-lookup"><span data-stu-id="be771-120">LINQ to XML is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="be771-121">Você pode consultar e modificar o documento e, depois de modificá-lo, pode salvá-lo em um arquivo ou serializá-lo e enviá-lo pela Internet.</span><span class="sxs-lookup"><span data-stu-id="be771-121">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="be771-122">No entanto, LINQ to XML difere do DOM:</span><span class="sxs-lookup"><span data-stu-id="be771-122">However, LINQ to XML differs from DOM:</span></span>

- <span data-ttu-id="be771-123">Ele fornece um novo modelo de objeto que é mais leve e mais fácil de trabalhar.</span><span class="sxs-lookup"><span data-stu-id="be771-123">It provides a new object model that's lighter weight and easier to work with.</span></span>
- <span data-ttu-id="be771-124">Ele aproveita os recursos de linguagem em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="be771-124">It takes advantage of language features in C# and Visual Basic.</span></span>

<span data-ttu-id="be771-125">A vantagem mais importante do LINQ to XML é sua integração com LINQ (consulta integrada à linguagem).</span><span class="sxs-lookup"><span data-stu-id="be771-125">The most important advantage of LINQ to XML is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="be771-126">Essa integração permite que você escreva consultas no documento XML na memória para recuperar coleções de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="be771-126">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="be771-127">O recurso de consulta do LINQ to XML é comparável na funcionalidade (embora não na sintaxe) para XPath e XQuery.</span><span class="sxs-lookup"><span data-stu-id="be771-127">The query capability of LINQ to XML is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="be771-128">A integração do LINQ em C# e Visual Basic fornece digitação mais forte, verificação de tempo de compilação e suporte a depurador aprimorado.</span><span class="sxs-lookup"><span data-stu-id="be771-128">The integration of LINQ in C# and Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="be771-129">Outra vantagem do LINQ to XML é a capacidade de usar os resultados da consulta como parâmetros para <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XAttribute> construtores de objeto permite uma abordagem poderosa para a criação de árvores XML.</span><span class="sxs-lookup"><span data-stu-id="be771-129">Another advantage of LINQ to XML is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="be771-130">Essa abordagem, chamada de *construção funcional*, permite que os desenvolvedores transformem com facilidade árvores XML de uma forma em outra.</span><span class="sxs-lookup"><span data-stu-id="be771-130">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="be771-131">Por exemplo, você pode ter uma ordem de compra XML típica, conforme descrito em [arquivo XML de exemplo: ordem de compra típica](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="be771-131">For example, you might have a typical XML purchase order as described in [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span> <span data-ttu-id="be771-132">Usando LINQ to XML, você pode executar a consulta a seguir para obter o valor do atributo de número de parte para cada elemento de item na ordem de compra:</span><span class="sxs-lookup"><span data-stu-id="be771-132">By using LINQ to XML, you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
    From item In purchaseOrder...<Item> _
    Select item.@PartNumber
```

<span data-ttu-id="be771-133">Em C#, isso pode ser reescrito no formulário sintaxe de método:</span><span class="sxs-lookup"><span data-stu-id="be771-133">In C# this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="be771-134">Como outro exemplo, você poderia querer uma lista, classificada por número de peça, dos itens com um valor maior que $ 100.</span><span class="sxs-lookup"><span data-stu-id="be771-134">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="be771-135">Para obter essas informações, você poderia executar a seguinte consulta:</span><span class="sxs-lookup"><span data-stu-id="be771-135">To obtain this information, you could run the following query:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
From item In purchaseOrder...<Item> _
Where (item.<Quantity>.Value * _
       item.<USPrice>.Value) > 100 _
Order By item.<PartNumber>.Value _
Select item
```

<span data-ttu-id="be771-136">Novamente, em C#, isso pode ser reescrito no formulário sintaxe de método:</span><span class="sxs-lookup"><span data-stu-id="be771-136">Again, in C# this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="be771-137">Além desses recursos do LINQ, o LINQ to XML fornece uma interface de programação XML aprimorada.</span><span class="sxs-lookup"><span data-stu-id="be771-137">In addition to these LINQ capabilities, LINQ to XML provides an improved XML programming interface.</span></span> <span data-ttu-id="be771-138">Usando LINQ to XML, você pode:</span><span class="sxs-lookup"><span data-stu-id="be771-138">Using LINQ to XML, you can:</span></span>

- <span data-ttu-id="be771-139">Carregar XML de [arquivos](load-xml-file.md) ou [fluxos](stream-xml-fragments-xmlreader.md).</span><span class="sxs-lookup"><span data-stu-id="be771-139">Load XML from [files](load-xml-file.md) or [streams](stream-xml-fragments-xmlreader.md).</span></span>
- <span data-ttu-id="be771-140">Serializar o XML em arquivos ou fluxos.</span><span class="sxs-lookup"><span data-stu-id="be771-140">Serialize XML to files or streams.</span></span>
- <span data-ttu-id="be771-141">Crie XML a partir do zero usando a construção funcional.</span><span class="sxs-lookup"><span data-stu-id="be771-141">Create XML from scratch by using functional construction.</span></span>
- <span data-ttu-id="be771-142">Consultar o XML usando eixos do tipo XPath.</span><span class="sxs-lookup"><span data-stu-id="be771-142">Query XML using XPath-like axes.</span></span>
- <span data-ttu-id="be771-143">Manipular a árvore XML na memória usando métodos como <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A> e <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="be771-143">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>
- <span data-ttu-id="be771-144">Validar árvores XML usando XSD.</span><span class="sxs-lookup"><span data-stu-id="be771-144">Validate XML trees using XSD.</span></span>
- <span data-ttu-id="be771-145">Usar uma combinação desses recursos para transformar árvores XML de uma forma em outra.</span><span class="sxs-lookup"><span data-stu-id="be771-145">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="create-xml-trees"></a><span data-ttu-id="be771-146">Criar árvores XML</span><span class="sxs-lookup"><span data-stu-id="be771-146">Create XML trees</span></span>

<span data-ttu-id="be771-147">Uma das vantagens mais significativas de programação com o LINQ to XML é que é fácil criar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="be771-147">One of the most significant advantages of programming with LINQ to XML is that it's easy to create XML trees.</span></span> <span data-ttu-id="be771-148">Por exemplo, para criar uma árvore XML pequena, você pode escrever código da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="be771-148">For example, to create a small XML tree, you can write code as follows:</span></span>

```csharp
XElement contacts =
new XElement("Contacts",
    new XElement("Contact",
        new XElement("Name", "Patrick Hines"),
        new XElement("Phone", "206-555-0144",
            new XAttribute("Type", "Home")),
        new XElement("phone", "425-555-0145",
            new XAttribute("Type", "Work")),
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

> [!NOTE]
> <span data-ttu-id="be771-149">A versão Visual Basic do exemplo usa literais XML.</span><span class="sxs-lookup"><span data-stu-id="be771-149">The Visual Basic version of the example uses XML literals.</span></span> <span data-ttu-id="be771-150">Você também pode usar <xref:System.Xml.Linq.XElement> o no Visual Basic, como na versão C#.</span><span class="sxs-lookup"><span data-stu-id="be771-150">You can also use <xref:System.Xml.Linq.XElement> in Visual Basic, as in the C# version.</span></span>

<span data-ttu-id="be771-151">Para obter mais informações, consulte [árvores XML](functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="be771-151">For more information, see [XML trees](functional-construction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="be771-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="be771-152">See also</span></span>

- [<span data-ttu-id="be771-153">Referência</span><span class="sxs-lookup"><span data-stu-id="be771-153">Reference</span></span>](reference.md)
- [<span data-ttu-id="be771-154">LINQ to XML e DOM</span><span class="sxs-lookup"><span data-stu-id="be771-154">LINQ to XML vs. DOM</span></span>](linq-xml-vs-dom.md)
- [<span data-ttu-id="be771-155">LINQ to XML vs. outras tecnologias XML</span><span class="sxs-lookup"><span data-stu-id="be771-155">LINQ to XML vs. other XML technologies</span></span>](linq-xml-vs-xml-technologies.md)
- <xref:System.Xml.Linq>
