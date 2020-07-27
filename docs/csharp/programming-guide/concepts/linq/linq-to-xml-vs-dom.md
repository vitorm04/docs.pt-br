---
title: LINQ to XML vs. DOM (C#)
description: Saiba mais sobre as principais diferenças entre LINQ to XML e a API de programação XML do W3C Modelo de Objeto do Documento (DOM).
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: f5fc3fd7869079d47d7c9031e3668afeed7a117b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165341"
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="f6de2-103">LINQ to XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="f6de2-103">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="f6de2-104">Esta seção descreve algumas das principais diferenças entre o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] e a atual API de programação de XML predominante, o W3C DOM (Modelo de Objeto do Documento).</span><span class="sxs-lookup"><span data-stu-id="f6de2-104">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="f6de2-105">Novas maneiras de criar árvores XML</span><span class="sxs-lookup"><span data-stu-id="f6de2-105">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="f6de2-106">No W3C DOM, você cria uma árvore XML de baixo para cima; ou seja, você cria um documento, cria elementos e, em seguida, adiciona elementos ao documento.</span><span class="sxs-lookup"><span data-stu-id="f6de2-106">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="f6de2-107">Por exemplo, veja a seguir uma maneira comum de criar uma árvore XML usando a implementação da Microsoft do DOM, <xref:System.Xml.XmlDocument>:</span><span class="sxs-lookup"><span data-stu-id="f6de2-107">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="f6de2-108">Este estilo de codificação não fornece visualmente muitas informações sobre a estrutura da árvore XML.</span><span class="sxs-lookup"><span data-stu-id="f6de2-108">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> <span data-ttu-id="f6de2-109">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dá suporte a esta abordagem para construir uma árvore XML, mas também dá suporte a uma abordagem alternativa, a *construção funcional*.</span><span class="sxs-lookup"><span data-stu-id="f6de2-109">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="f6de2-110">A construção funcional usa os construtores <xref:System.Xml.Linq.XElement> e de <xref:System.Xml.Linq.XAttribute> para criar uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="f6de2-110">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="f6de2-111">Veja como você construiria a mesma árvore XML usando a construção funcional [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="f6de2-111">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="f6de2-112">Observe que o recuo do código para construir a árvore XML mostra a estrutura do XML subjacente.</span><span class="sxs-lookup"><span data-stu-id="f6de2-112">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="f6de2-113">Para obter mais informações, consulte [Criando árvores XML (C#)](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f6de2-113">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="f6de2-114">Trabalhando diretamente com Elementos XML</span><span class="sxs-lookup"><span data-stu-id="f6de2-114">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="f6de2-115">Quando você programa com XML, o foco principal é geralmente em elementos XML e talvez em atributos.</span><span class="sxs-lookup"><span data-stu-id="f6de2-115">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="f6de2-116">No [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você pode trabalhar diretamente com elementos e atributos XML.</span><span class="sxs-lookup"><span data-stu-id="f6de2-116">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="f6de2-117">Por exemplo, você pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f6de2-117">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="f6de2-118">Criar elementos XML sem usar nenhum objeto de documento.</span><span class="sxs-lookup"><span data-stu-id="f6de2-118">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="f6de2-119">Isso simplifica a programação quando você tem que trabalhar com partes de árvores XML.</span><span class="sxs-lookup"><span data-stu-id="f6de2-119">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="f6de2-120">Carregue objetos `T:System.Xml.Linq.XElement` diretamente de um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="f6de2-120">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="f6de2-121">Serialize objetos `T:System.Xml.Linq.XElement` para um arquivo ou fluxo.</span><span class="sxs-lookup"><span data-stu-id="f6de2-121">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="f6de2-122">Compare isso para o W3C DOM, no qual o documento XML é usado como um contêiner lógico para a árvore XML.</span><span class="sxs-lookup"><span data-stu-id="f6de2-122">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="f6de2-123">No DOM, os nós XML, incluindo elementos e atributos, devem ser criados no contexto de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="f6de2-123">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="f6de2-124">Aqui está um fragmento de código para criar um elemento de nome DOM:</span><span class="sxs-lookup"><span data-stu-id="f6de2-124">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="f6de2-125">Se você quiser usar um elemento em vários documentos, deverá importar os nós nos documentos.</span><span class="sxs-lookup"><span data-stu-id="f6de2-125">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f6de2-126">evita essa camada de complexidade.</span><span class="sxs-lookup"><span data-stu-id="f6de2-126">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="f6de2-127">Ao usar LINQ to XML, você usará a classe <xref:System.Xml.Linq.XDocument> somente se você desejar adicionar um comentário ou uma instrução de processamento no nível raiz do documento.</span><span class="sxs-lookup"><span data-stu-id="f6de2-127">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="f6de2-128">Tratamento simplificado de nomes e namespaces</span><span class="sxs-lookup"><span data-stu-id="f6de2-128">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="f6de2-129">Tratar nomes, namespaces e prefixos de namespace é geralmente uma parte complexa da programação de XML.</span><span class="sxs-lookup"><span data-stu-id="f6de2-129">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> <span data-ttu-id="f6de2-130">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] simplifica nomes e namespaces eliminando a necessidade de lidar com prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="f6de2-130">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="f6de2-131">Se quiser, você pode controlar prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="f6de2-131">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="f6de2-132">Mas se você optar por não controlar explicitamente os prefixos de namespace, o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] atribuirá prefixos de namespace durante a serialização se forem necessários ou os serializará usando namespaces padrão se não forem.</span><span class="sxs-lookup"><span data-stu-id="f6de2-132">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="f6de2-133">Se namespaces padrão forem usados, não haverá prefixos de namespace no documento resultante.</span><span class="sxs-lookup"><span data-stu-id="f6de2-133">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="f6de2-134">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f6de2-134">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="f6de2-135">Outro problema com os DOM é que ele não permite que você altere o nome de um nó.</span><span class="sxs-lookup"><span data-stu-id="f6de2-135">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="f6de2-136">Em vez disso, você precisa criar um novo nó e copiar todos os nós filhos para ele, perdendo a identidade do nó original.</span><span class="sxs-lookup"><span data-stu-id="f6de2-136">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f6de2-137">evita esse problema permitindo que você defina a propriedade <xref:System.Xml.Linq.XName> em um nó.</span><span class="sxs-lookup"><span data-stu-id="f6de2-137">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="f6de2-138">Suporte de método estático para carregar XML</span><span class="sxs-lookup"><span data-stu-id="f6de2-138">Static Method Support for Loading XML</span></span>  
 <span data-ttu-id="f6de2-139">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] permite que você carregue XML usando métodos estáticos em vez de métodos de instância.</span><span class="sxs-lookup"><span data-stu-id="f6de2-139">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="f6de2-140">Isso simplifica o carregamento e a análise.</span><span class="sxs-lookup"><span data-stu-id="f6de2-140">This simplifies loading and parsing.</span></span> <span data-ttu-id="f6de2-141">Para obter mais informações, consulte [como carregar XML de um arquivo (C#)](./how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="f6de2-141">For more information, see [How to load XML from a file (C#)](./how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="f6de2-142">Remoção de suporte para construções de DTD</span><span class="sxs-lookup"><span data-stu-id="f6de2-142">Removal of Support for DTD Constructs</span></span>  
 <span data-ttu-id="f6de2-143">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] simplifica ainda mais a programação de XML removendo o suporte para entidades e referências a entidades.</span><span class="sxs-lookup"><span data-stu-id="f6de2-143">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="f6de2-144">O gerenciamento de entidades é complexo e raramente é usado.</span><span class="sxs-lookup"><span data-stu-id="f6de2-144">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="f6de2-145">Remover o suporte aumenta o desempenho e simplifica a interface de programação.</span><span class="sxs-lookup"><span data-stu-id="f6de2-145">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="f6de2-146">Quando uma árvore [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é populada, todas as entidades de DTD são expandidas.</span><span class="sxs-lookup"><span data-stu-id="f6de2-146">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="f6de2-147">Suporte para fragmentos</span><span class="sxs-lookup"><span data-stu-id="f6de2-147">Support for Fragments</span></span>  
 <span data-ttu-id="f6de2-148">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] não fornece um equivalente para a classe `XmlDocumentFragment`.</span><span class="sxs-lookup"><span data-stu-id="f6de2-148">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="f6de2-149">Em muitos casos, no entanto, o conceito de `XmlDocumentFragment` pode ser tratado pelo resultado de uma consulta que é digitada como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XNode> ou <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="f6de2-149">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="f6de2-150">Suporte para XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f6de2-150">Support for XPathNavigator</span></span>  
 <span data-ttu-id="f6de2-151">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dá suporte a <xref:System.Xml.XPath.XPathNavigator> por meio de métodos de extensão no namespace <xref:System.Xml.XPath?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f6de2-151">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f6de2-152">Para obter mais informações, consulte <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f6de2-152">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="f6de2-153">Suporte para espaço em branco e recuo</span><span class="sxs-lookup"><span data-stu-id="f6de2-153">Support for White Space and Indentation</span></span>  
 <span data-ttu-id="f6de2-154">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] trata espaços em branco de maneira mais simples que o DOM.</span><span class="sxs-lookup"><span data-stu-id="f6de2-154">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="f6de2-155">Um cenário comum é ler o XML recuado, criar uma árvore XML na memória sem nenhum nó de texto de espaço em branco (isto é, não preservar espaço em branco), executar algumas operações no XML e, em seguida, salvar o XML com recuo.</span><span class="sxs-lookup"><span data-stu-id="f6de2-155">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="f6de2-156">Quando você serializa o XML com formatação, somente os espaços em branco significativos na árvore XML são preservados.</span><span class="sxs-lookup"><span data-stu-id="f6de2-156">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="f6de2-157">Este é o comportamento padrão para [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f6de2-157">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="f6de2-158">Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente.</span><span class="sxs-lookup"><span data-stu-id="f6de2-158">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="f6de2-159">Você pode não querer modificar este recuo de nenhuma forma.</span><span class="sxs-lookup"><span data-stu-id="f6de2-159">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="f6de2-160">No [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você pode fazer isso preservando o espaço em branco ao carregar ou analisar o XML e desabilitando a formatação ao serializar o XML.</span><span class="sxs-lookup"><span data-stu-id="f6de2-160">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 <span data-ttu-id="f6de2-161">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] armazena o espaço em branco como um nó de <xref:System.Xml.Linq.XText>, em vez de ter um tipo de nó especializado do <xref:System.Xml.XmlNodeType.Whitespace>, assim como o DOM.</span><span class="sxs-lookup"><span data-stu-id="f6de2-161">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="f6de2-162">Suporte para anotações</span><span class="sxs-lookup"><span data-stu-id="f6de2-162">Support for Annotations</span></span>  
 <span data-ttu-id="f6de2-163">Elementos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dão suporte a um conjunto extensível de anotações.</span><span class="sxs-lookup"><span data-stu-id="f6de2-163">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] elements support an extensible set of annotations.</span></span> <span data-ttu-id="f6de2-164">Isso é útil para acompanhar informações variadas sobre um elemento, como informações de esquema, informações sobre se o elemento está associado a uma interface do usuário ou qualquer outro tipo de informações específicas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f6de2-164">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="f6de2-165">Para obter mais informações, consulte [Anotações LINQ to XML (C#)](./linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="f6de2-165">For more information, see [LINQ to XML Annotations](./linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="f6de2-166">Suporte para informações do esquema</span><span class="sxs-lookup"><span data-stu-id="f6de2-166">Support for Schema Information</span></span>  
<span data-ttu-id="f6de2-167">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dá suporte para validação de XSD por meio de métodos de extensão no namespace <xref:System.Xml.Schema?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f6de2-167">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f6de2-168">Você pode validar que uma árvore XML está em conformidade com XSD.</span><span class="sxs-lookup"><span data-stu-id="f6de2-168">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="f6de2-169">Você pode preencher a árvore XML com o PSVI (post-schema-validation infoset).</span><span class="sxs-lookup"><span data-stu-id="f6de2-169">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="f6de2-170">Para obter mais informações, consulte [como validar usando xsd](./how-to-validate-using-xsd-linq-to-xml.md) e <xref:System.Xml.Schema.Extensions> .</span><span class="sxs-lookup"><span data-stu-id="f6de2-170">For more information, see [How to validate using XSD](./how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f6de2-171">Confira também</span><span class="sxs-lookup"><span data-stu-id="f6de2-171">See also</span></span>

- [<span data-ttu-id="f6de2-172">Guia de introdução (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f6de2-172">Getting Started (LINQ to XML)</span></span>](./linq-to-xml-overview.md)
