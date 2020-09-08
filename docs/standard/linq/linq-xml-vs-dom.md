---
title: LINQ to XML e DOM
description: Há diferenças importantes entre LINQ to XML e DOM. O LINQ to XML dá suporte à construção funcional e a literais XML, o que mostra melhor a estrutura das árvores XML que elas criam.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 905fe1b47361e2b96c79bc56cb831b3cb298e4de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551975"
---
# <a name="linq-to-xml-vs-dom"></a><span data-ttu-id="98574-104">LINQ to XML e DOM</span><span class="sxs-lookup"><span data-stu-id="98574-104">LINQ to XML vs. DOM</span></span>

<span data-ttu-id="98574-105">Este artigo descreve algumas das principais diferenças entre LINQ to XML e a API de programação XML predominante atual, o W3C Modelo de Objeto do Documento (DOM).</span><span class="sxs-lookup"><span data-stu-id="98574-105">This article describes some key differences between LINQ to XML and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>

## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="98574-106">Novas maneiras de construir árvores XML</span><span class="sxs-lookup"><span data-stu-id="98574-106">New ways to construct XML trees</span></span>

<span data-ttu-id="98574-107">No W3C DOM, você cria uma árvore XML de baixo para cima; ou seja, você cria um documento, cria elementos e, em seguida, adiciona elementos ao documento.</span><span class="sxs-lookup"><span data-stu-id="98574-107">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>

<span data-ttu-id="98574-108">Por exemplo, o exemplo a seguir usa uma maneira típica de criar uma árvore XML usando a implementação da Microsoft do DOM, <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="98574-108">For example, the following example uses a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>.</span></span>

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
XmlElement phone1 = doc.CreateElement("Phone");
phone1.SetAttribute("Type", "Home");
phone1.InnerText = "206-555-0144";
XmlElement phone2 = doc.CreateElement("Phone");
phone2.SetAttribute("Type", "Work");
phone2.InnerText = "425-555-0145";
XmlElement street1 = doc.CreateElement("Street1");
street1.InnerText = "123 Main St";
XmlElement city = doc.CreateElement("City");
city.InnerText = "Mercer Island";
XmlElement state = doc.CreateElement("State");
state.InnerText = "WA";
XmlElement postal = doc.CreateElement("Postal");
postal.InnerText = "68042";
XmlElement address = doc.CreateElement("Address");
address.AppendChild(street1);
address.AppendChild(city);
address.AppendChild(state);
address.AppendChild(postal);
XmlElement contact = doc.CreateElement("Contact");
contact.AppendChild(name);
contact.AppendChild(phone1);
contact.AppendChild(phone2);
contact.AppendChild(address);
XmlElement contacts = doc.CreateElement("Contacts");
contacts.AppendChild(contact);
doc.AppendChild(contacts);
```

```vb
Dim doc As XmlDocument = New XmlDocument()
Dim name As XmlElement = doc.CreateElement("Name")
name.InnerText = "Patrick Hines"
Dim phone1 As XmlElement = doc.CreateElement("Phone")
phone1.SetAttribute("Type", "Home")
phone1.InnerText = "206-555-0144"
Dim phone2 As XmlElement = doc.CreateElement("Phone")
phone2.SetAttribute("Type", "Work")
phone2.InnerText = "425-555-0145"
Dim street1 As XmlElement = doc.CreateElement("Street1")
street1.InnerText = "123 Main St"
Dim city As XmlElement = doc.CreateElement("City")
city.InnerText = "Mercer Island"
Dim state As XmlElement = doc.CreateElement("State")
state.InnerText = "WA"
Dim postal As XmlElement = doc.CreateElement("Postal")
postal.InnerText = "68042"
Dim address As XmlElement = doc.CreateElement("Address")
address.AppendChild(street1)
address.AppendChild(city)
address.AppendChild(state)
address.AppendChild(postal)
Dim contact As XmlElement = doc.CreateElement("Contact")
contact.AppendChild(name)
contact.AppendChild(phone1)
contact.AppendChild(phone2)
contact.AppendChild(address)
Dim contacts As XmlElement = doc.CreateElement("Contacts")
contacts.AppendChild(contact)
doc.AppendChild(contacts)
Console.WriteLine(doc.OuterXml)
```

<span data-ttu-id="98574-109">Esse estilo de codificação oculta a estrutura da árvore XML.</span><span class="sxs-lookup"><span data-stu-id="98574-109">This style of coding hides the structure of the XML tree.</span></span> <span data-ttu-id="98574-110">O LINQ to XML também dá suporte a uma abordagem alternativa, *construção funcional*, que mostra melhor a estrutura.</span><span class="sxs-lookup"><span data-stu-id="98574-110">LINQ to XML also supports an alternative approach, *functional construction*, that better shows the structure.</span></span> <span data-ttu-id="98574-111">Essa abordagem pode ser feita com os <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> construtores e.</span><span class="sxs-lookup"><span data-stu-id="98574-111">This approach can be done with the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors.</span></span> <span data-ttu-id="98574-112">No Visual Basic, ele também pode ser feito com literais XML.</span><span class="sxs-lookup"><span data-stu-id="98574-112">In Visual Basic, it can also be done with XML literals.</span></span> <span data-ttu-id="98574-113">Este exemplo demonstra a construção da mesma árvore XML usando a construção funcional:</span><span class="sxs-lookup"><span data-stu-id="98574-113">This example demonstrates construction of the same XML tree using functional construction:</span></span>

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
Dim contacts = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type="Home">206-555-0144</Phone>
            <Phone Type="Work">425-555-0145</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

<span data-ttu-id="98574-114">Observe que o recuo do código para construir a árvore XML mostra a estrutura do XML subjacente.</span><span class="sxs-lookup"><span data-stu-id="98574-114">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span> <span data-ttu-id="98574-115">A versão Visual Basic usa literais XML.</span><span class="sxs-lookup"><span data-stu-id="98574-115">The Visual Basic version uses XML literals.</span></span>

<span data-ttu-id="98574-116">Para obter mais informações, consulte [árvores XML](functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="98574-116">For more information, see [XML trees](functional-construction.md).</span></span>

## <a name="work-directly-with-xml-elements"></a><span data-ttu-id="98574-117">Trabalhar diretamente com elementos XML</span><span class="sxs-lookup"><span data-stu-id="98574-117">Work directly with XML elements</span></span>

<span data-ttu-id="98574-118">Quando você programa com XML, o foco principal é geralmente em elementos XML e talvez em atributos.</span><span class="sxs-lookup"><span data-stu-id="98574-118">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="98574-119">No LINQ to XML, você pode trabalhar diretamente com elementos e atributos XML.</span><span class="sxs-lookup"><span data-stu-id="98574-119">In LINQ to XML, you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="98574-120">Por exemplo, você pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="98574-120">For example, you can do the following:</span></span>

- <span data-ttu-id="98574-121">Criar elementos XML sem usar nenhum objeto de documento.</span><span class="sxs-lookup"><span data-stu-id="98574-121">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="98574-122">Isso simplifica a programação quando você tem que trabalhar com partes de árvores XML.</span><span class="sxs-lookup"><span data-stu-id="98574-122">This simplifies programming when you have to work with fragments of XML trees.</span></span>
- <span data-ttu-id="98574-123">Carregue objetos `T:System.Xml.Linq.XElement` diretamente de um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="98574-123">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>
- <span data-ttu-id="98574-124">Serialize objetos `T:System.Xml.Linq.XElement` para um arquivo ou fluxo.</span><span class="sxs-lookup"><span data-stu-id="98574-124">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>

<span data-ttu-id="98574-125">Compare isso para o W3C DOM, no qual o documento XML é usado como um contêiner lógico para a árvore XML.</span><span class="sxs-lookup"><span data-stu-id="98574-125">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="98574-126">No DOM, os nós XML, incluindo elementos e atributos, devem ser criados no contexto de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="98574-126">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="98574-127">Aqui está um fragmento de código para criar um elemento Name no DOM:</span><span class="sxs-lookup"><span data-stu-id="98574-127">Here is a fragment of code to create a name element in DOM:</span></span>

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
doc.AppendChild(name);
```

```vb
Dim doc As XmlDocument = New XmlDocument()
Dim name As XmlElement = doc.CreateElement("Name")
name.InnerText = "Patrick Hines"
doc.AppendChild(name)
```

<span data-ttu-id="98574-128">Se você quiser usar um elemento em vários documentos, deverá importar os nós nos documentos.</span><span class="sxs-lookup"><span data-stu-id="98574-128">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> <span data-ttu-id="98574-129">LINQ to XML evita essa camada de complexidade.</span><span class="sxs-lookup"><span data-stu-id="98574-129">LINQ to XML avoids this layer of complexity.</span></span>

<span data-ttu-id="98574-130">Ao usar LINQ to XML, você usará a classe <xref:System.Xml.Linq.XDocument> somente se você desejar adicionar um comentário ou uma instrução de processamento no nível raiz do documento.</span><span class="sxs-lookup"><span data-stu-id="98574-130">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>

## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="98574-131">Manipulação simplificada de nomes e namespaces</span><span class="sxs-lookup"><span data-stu-id="98574-131">Simplified handling of names and namespaces</span></span>

<span data-ttu-id="98574-132">Tratar nomes, namespaces e prefixos de namespace é geralmente uma parte complexa da programação de XML.</span><span class="sxs-lookup"><span data-stu-id="98574-132">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> <span data-ttu-id="98574-133">O LINQ to XML simplifica nomes e namespaces eliminando a necessidade de lidar com prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="98574-133">LINQ to XML simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="98574-134">Se quiser, você pode controlar prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="98574-134">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="98574-135">Mas se você decidir não controlar explicitamente os prefixos de namespace, LINQ to XML atribuirá prefixos de namespace durante a serialização, se eles forem necessários, ou serializarão usando namespaces padrão, se não forem.</span><span class="sxs-lookup"><span data-stu-id="98574-135">But if you decide to not explicitly control namespace prefixes, LINQ to XML will assign namespace prefixes during serialization if they're required, or will serialize using default namespaces if they're not.</span></span> <span data-ttu-id="98574-136">Se namespaces padrão forem usados, não haverá prefixos de namespace no documento resultante.</span><span class="sxs-lookup"><span data-stu-id="98574-136">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="98574-137">Para obter mais informações, consulte [visão geral de namespaces](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="98574-137">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="98574-138">Outro problema com o DOM é que ele não permite que você altere o nome de um nó.</span><span class="sxs-lookup"><span data-stu-id="98574-138">Another problem with the DOM is that it doesn't let you change the name of a node.</span></span> <span data-ttu-id="98574-139">Em vez disso, você precisa criar um novo nó e copiar todos os nós filhos para ele, perdendo a identidade do nó original.</span><span class="sxs-lookup"><span data-stu-id="98574-139">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> <span data-ttu-id="98574-140">LINQ to XML evita esse problema permitindo que você defina a <xref:System.Xml.Linq.XName> propriedade em um nó.</span><span class="sxs-lookup"><span data-stu-id="98574-140">LINQ to XML avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>

## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="98574-141">Suporte de método estático para carregar XML</span><span class="sxs-lookup"><span data-stu-id="98574-141">Static method support for loading XML</span></span>

<span data-ttu-id="98574-142">LINQ to XML permite carregar XML usando métodos estáticos, em vez de métodos de instância.</span><span class="sxs-lookup"><span data-stu-id="98574-142">LINQ to XML lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="98574-143">Isso simplifica o carregamento e a análise.</span><span class="sxs-lookup"><span data-stu-id="98574-143">This simplifies loading and parsing.</span></span> <span data-ttu-id="98574-144">Para obter mais informações, consulte [como carregar XML de um arquivo](load-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="98574-144">For more information, see [How to load XML from a file](load-xml-file.md).</span></span>

## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="98574-145">Remoção de suporte para construções de DTD</span><span class="sxs-lookup"><span data-stu-id="98574-145">Removal of support for DTD constructs</span></span>

<span data-ttu-id="98574-146">LINQ to XML simplifica ainda mais a programação XML removendo o suporte para entidades e referências de entidade.</span><span class="sxs-lookup"><span data-stu-id="98574-146">LINQ to XML further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="98574-147">O gerenciamento de entidades é complexo e raramente é usado.</span><span class="sxs-lookup"><span data-stu-id="98574-147">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="98574-148">Remover o suporte aumenta o desempenho e simplifica a interface de programação.</span><span class="sxs-lookup"><span data-stu-id="98574-148">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="98574-149">Quando uma árvore de LINQ to XML é populada, todas as entidades DTD são expandidas.</span><span class="sxs-lookup"><span data-stu-id="98574-149">When a LINQ to XML tree is populated, all DTD entities are expanded.</span></span>

## <a name="support-for-fragments"></a><span data-ttu-id="98574-150">Suporte para fragmentos</span><span class="sxs-lookup"><span data-stu-id="98574-150">Support for fragments</span></span>

<span data-ttu-id="98574-151">LINQ to XML não fornece um equivalente para a `XmlDocumentFragment` classe.</span><span class="sxs-lookup"><span data-stu-id="98574-151">LINQ to XML doesn't provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="98574-152">Em muitos casos, no entanto, o `XmlDocumentFragment` conceito pode ser tratado pelo resultado de uma consulta que é digitada a partir <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XNode> , ou <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="98574-152">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that's typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>

## <a name="support-for-xpathnavigator"></a><span data-ttu-id="98574-153">Suporte para XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="98574-153">Support for XPathNavigator</span></span>

<span data-ttu-id="98574-154">LINQ to XML fornece suporte para por <xref:System.Xml.XPath.XPathNavigator> meio de métodos de extensão no <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="98574-154">LINQ to XML provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="98574-155">Para obter mais informações, consulte <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="98574-155">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>

## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="98574-156">Suporte para espaço em branco e recuo</span><span class="sxs-lookup"><span data-stu-id="98574-156">Support for white space and indentation</span></span>

<span data-ttu-id="98574-157">LINQ to XML lida com o espaço em branco mais simples do que o DOM.</span><span class="sxs-lookup"><span data-stu-id="98574-157">LINQ to XML handles white space more simply than the DOM.</span></span>

<span data-ttu-id="98574-158">Um cenário comum é ler XML recuado, criar uma árvore XML na memória sem nenhum nó de texto de espaço em branco (ou seja, não preservar espaço em branco), executar algumas operações no XML e, em seguida, salvar o XML com recuo.</span><span class="sxs-lookup"><span data-stu-id="98574-158">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), do some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="98574-159">Quando você serializa o XML com formatação, somente os espaços em branco significativos na árvore XML são preservados.</span><span class="sxs-lookup"><span data-stu-id="98574-159">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="98574-160">Esse é o comportamento padrão para LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="98574-160">This is the default behavior for LINQ to XML.</span></span>

<span data-ttu-id="98574-161">Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente.</span><span class="sxs-lookup"><span data-stu-id="98574-161">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="98574-162">Você pode não querer modificar este recuo de nenhuma forma.</span><span class="sxs-lookup"><span data-stu-id="98574-162">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="98574-163">No LINQ to XML, você pode fazer isso da seguinte:</span><span class="sxs-lookup"><span data-stu-id="98574-163">In LINQ to XML, you can do this by:</span></span>

- <span data-ttu-id="98574-164">Preservando o espaço em branco quando você carrega ou analisa o XML.</span><span class="sxs-lookup"><span data-stu-id="98574-164">Preserving white space when you load or parse the XML.</span></span>
- <span data-ttu-id="98574-165">Desabilitar a formatação ao serializar o XML.</span><span class="sxs-lookup"><span data-stu-id="98574-165">Disabling formatting when you serialize the XML.</span></span>

<span data-ttu-id="98574-166">O LINQ to XML armazena espaço em branco como um <xref:System.Xml.Linq.XText> nó, em vez de ter um <xref:System.Xml.XmlNodeType.Whitespace> tipo de nó especializado, como o dom faz.</span><span class="sxs-lookup"><span data-stu-id="98574-166">LINQ to XML stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>

## <a name="support-for-annotations"></a><span data-ttu-id="98574-167">Suporte para anotações</span><span class="sxs-lookup"><span data-stu-id="98574-167">Support for annotations</span></span>

<span data-ttu-id="98574-168">LINQ to XML elementos dão suporte a um conjunto extensível de anotações.</span><span class="sxs-lookup"><span data-stu-id="98574-168">LINQ to XML elements support an extensible set of annotations.</span></span> <span data-ttu-id="98574-169">Isso é útil para acompanhar informações variadas sobre um elemento, como informações de esquema, informações sobre se o elemento está associado a uma interface do usuário ou qualquer outro tipo de informações específicas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98574-169">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="98574-170">Para obter mais informações, consulte [LINQ to XML anotações](linq-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="98574-170">For more information, see [LINQ to XML annotations](linq-xml-annotations.md).</span></span>

## <a name="support-for-schema-information"></a><span data-ttu-id="98574-171">Suporte para informações de esquema</span><span class="sxs-lookup"><span data-stu-id="98574-171">Support for schema information</span></span>

<span data-ttu-id="98574-172">LINQ to XML fornece suporte para validação XSD por meio de métodos de extensão no <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="98574-172">LINQ to XML provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="98574-173">Você pode validar que uma árvore XML está em conformidade com XSD.</span><span class="sxs-lookup"><span data-stu-id="98574-173">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="98574-174">Você pode preencher a árvore XML com o PSVI (post-schema-validation infoset).</span><span class="sxs-lookup"><span data-stu-id="98574-174">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="98574-175">Para obter mais informações, consulte [como validar usando xsd](validate-xsd.md) e <xref:System.Xml.Schema.Extensions> .</span><span class="sxs-lookup"><span data-stu-id="98574-175">For more information, see [How to validate using XSD](validate-xsd.md) and <xref:System.Xml.Schema.Extensions>.</span></span>

## <a name="see-also"></a><span data-ttu-id="98574-176">Confira também</span><span class="sxs-lookup"><span data-stu-id="98574-176">See also</span></span>

- [<span data-ttu-id="98574-177">Visão geral de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="98574-177">LINQ to XML overview</span></span>](linq-xml-overview.md)
