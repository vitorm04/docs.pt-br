---
title: LINQ to XML e DOM (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: 4feb0df2e4d3ffe5c79ce61d7b94142833a312c7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213865"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a><span data-ttu-id="de437-102">LINQ to XML e DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de437-102">LINQ to XML vs. DOM (Visual Basic)</span></span>
<span data-ttu-id="de437-103">Esta seção descreve algumas das principais diferenças entre o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] e a atual API de programação de XML predominante, o W3C DOM (Modelo de Objeto do Documento).</span><span class="sxs-lookup"><span data-stu-id="de437-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="de437-104">Novas maneiras de criar árvores XML</span><span class="sxs-lookup"><span data-stu-id="de437-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="de437-105">No W3C DOM, você cria uma árvore XML de baixo para cima; ou seja, você cria um documento, cria elementos e, em seguida, adiciona elementos ao documento.</span><span class="sxs-lookup"><span data-stu-id="de437-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="de437-106">Por exemplo, veja a seguir uma maneira comum de criar uma árvore XML usando a implementação da Microsoft do DOM, <xref:System.Xml.XmlDocument>:</span><span class="sxs-lookup"><span data-stu-id="de437-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="de437-107">Este estilo de codificação não fornece visualmente muitas informações sobre a estrutura da árvore XML.</span><span class="sxs-lookup"><span data-stu-id="de437-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> <span data-ttu-id="de437-108">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dá suporte a esta abordagem para construir uma árvore XML, mas também dá suporte a uma abordagem alternativa, a *construção funcional*.</span><span class="sxs-lookup"><span data-stu-id="de437-108">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="de437-109">No Visual Basic, a construção funcional usa literais XML para criar uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="de437-109">In Visual Basic, functional construction uses XML literals to build an XML tree.</span></span>  
  
 <span data-ttu-id="de437-110">Veja como você construiria a mesma árvore XML usando a construção funcional [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="de437-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="de437-111">Observe que o recuo do código para construir a árvore XML mostra a estrutura do XML subjacente.</span><span class="sxs-lookup"><span data-stu-id="de437-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="de437-112">Para obter mais informações, consulte [criando árvores XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="de437-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="de437-113">Trabalhando diretamente com Elementos XML</span><span class="sxs-lookup"><span data-stu-id="de437-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="de437-114">Quando você programa com XML, o foco principal é geralmente em elementos XML e talvez em atributos.</span><span class="sxs-lookup"><span data-stu-id="de437-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="de437-115">No [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você pode trabalhar diretamente com elementos e atributos XML.</span><span class="sxs-lookup"><span data-stu-id="de437-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="de437-116">Por exemplo, você pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="de437-116">For example, you can do the following:</span></span>  
  
-   <span data-ttu-id="de437-117">Criar elementos XML sem usar nenhum objeto de documento.</span><span class="sxs-lookup"><span data-stu-id="de437-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="de437-118">Isso simplifica a programação quando você tem que trabalhar com partes de árvores XML.</span><span class="sxs-lookup"><span data-stu-id="de437-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
-   <span data-ttu-id="de437-119">Carregue objetos `T:System.Xml.Linq.XElement` diretamente de um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="de437-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
-   <span data-ttu-id="de437-120">Serialize objetos `T:System.Xml.Linq.XElement` para um arquivo ou fluxo.</span><span class="sxs-lookup"><span data-stu-id="de437-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="de437-121">Compare isso para o W3C DOM, no qual o documento XML é usado como um contêiner lógico para a árvore XML.</span><span class="sxs-lookup"><span data-stu-id="de437-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="de437-122">No DOM, os nós XML, incluindo elementos e atributos, devem ser criados no contexto de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="de437-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="de437-123">Aqui está um fragmento de código para criar um elemento de nome DOM:</span><span class="sxs-lookup"><span data-stu-id="de437-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 <span data-ttu-id="de437-124">Se você quiser usar um elemento em vários documentos, deverá importar os nós nos documentos.</span><span class="sxs-lookup"><span data-stu-id="de437-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="de437-125"> evita essa camada de complexidade.</span><span class="sxs-lookup"><span data-stu-id="de437-125"> avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="de437-126">Ao usar LINQ to XML, você usará a classe <xref:System.Xml.Linq.XDocument> somente se você desejar adicionar um comentário ou uma instrução de processamento no nível raiz do documento.</span><span class="sxs-lookup"><span data-stu-id="de437-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="de437-127">Tratamento simplificado de nomes e namespaces</span><span class="sxs-lookup"><span data-stu-id="de437-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="de437-128">Tratar nomes, namespaces e prefixos de namespace é geralmente uma parte complexa da programação de XML.</span><span class="sxs-lookup"><span data-stu-id="de437-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> <span data-ttu-id="de437-129">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] simplifica nomes e namespaces eliminando a necessidade de lidar com prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="de437-129">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="de437-130">Se quiser, você pode controlar prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="de437-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="de437-131">Mas se você optar por não controlar explicitamente os prefixos de namespace, o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] atribuirá prefixos de namespace durante a serialização se forem necessários ou os serializará usando namespaces padrão se não forem.</span><span class="sxs-lookup"><span data-stu-id="de437-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="de437-132">Se namespaces padrão forem usados, não haverá prefixos de namespace no documento resultante.</span><span class="sxs-lookup"><span data-stu-id="de437-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="de437-133">Para obter mais informações, consulte [trabalhando com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="de437-133">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="de437-134">Outro problema com os DOM é que ele não permite que você altere o nome de um nó.</span><span class="sxs-lookup"><span data-stu-id="de437-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="de437-135">Em vez disso, você precisa criar um novo nó e copiar todos os nós filhos para ele, perdendo a identidade do nó original.</span><span class="sxs-lookup"><span data-stu-id="de437-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="de437-136"> evita esse problema permitindo que você defina a propriedade <xref:System.Xml.Linq.XName> em um nó.</span><span class="sxs-lookup"><span data-stu-id="de437-136"> avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="de437-137">Suporte de método estático para carregar XML</span><span class="sxs-lookup"><span data-stu-id="de437-137">Static Method Support for Loading XML</span></span>  
 <span data-ttu-id="de437-138">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] permite que você carregue XML usando métodos estáticos em vez de métodos de instância.</span><span class="sxs-lookup"><span data-stu-id="de437-138">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="de437-139">Isso simplifica o carregamento e a análise.</span><span class="sxs-lookup"><span data-stu-id="de437-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="de437-140">Para obter mais informações, consulte [como: carregar XML de um arquivo (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="de437-140">For more information, see [How to: Load XML from a File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="de437-141">Remoção de suporte para construções de DTD</span><span class="sxs-lookup"><span data-stu-id="de437-141">Removal of Support for DTD Constructs</span></span>  
 <span data-ttu-id="de437-142">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] simplifica ainda mais a programação de XML removendo o suporte para entidades e referências a entidades.</span><span class="sxs-lookup"><span data-stu-id="de437-142">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="de437-143">O gerenciamento de entidades é complexo e raramente é usado.</span><span class="sxs-lookup"><span data-stu-id="de437-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="de437-144">Remover o suporte aumenta o desempenho e simplifica a interface de programação.</span><span class="sxs-lookup"><span data-stu-id="de437-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="de437-145">Quando uma árvore [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é populada, todas as entidades de DTD são expandidas.</span><span class="sxs-lookup"><span data-stu-id="de437-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="de437-146">Suporte para fragmentos</span><span class="sxs-lookup"><span data-stu-id="de437-146">Support for Fragments</span></span>  
 <span data-ttu-id="de437-147">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] não fornece um equivalente para a classe `XmlDocumentFragment`.</span><span class="sxs-lookup"><span data-stu-id="de437-147">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="de437-148">Em muitos casos, no entanto, o conceito de `XmlDocumentFragment` pode ser tratado pelo resultado de uma consulta que é digitada como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XNode> ou <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="de437-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="de437-149">Suporte para XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="de437-149">Support for XPathNavigator</span></span>  
 <span data-ttu-id="de437-150">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dá suporte a <xref:System.Xml.XPath.XPathNavigator> por meio de métodos de extensão no namespace <xref:System.Xml.XPath?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de437-150">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="de437-151">Para obter mais informações, consulte <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de437-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="de437-152">Suporte para espaço em branco e recuo</span><span class="sxs-lookup"><span data-stu-id="de437-152">Support for White Space and Indentation</span></span>  
 <span data-ttu-id="de437-153">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] trata espaços em branco de maneira mais simples que o DOM.</span><span class="sxs-lookup"><span data-stu-id="de437-153">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="de437-154">Um cenário comum é ler o XML recuado, criar uma árvore XML na memória sem nenhum nó de texto de espaço em branco (isto é, não preservar espaço em branco), executar algumas operações no XML e, em seguida, salvar o XML com recuo.</span><span class="sxs-lookup"><span data-stu-id="de437-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="de437-155">Quando você serializa o XML com formatação, somente os espaços em branco significativos na árvore XML são preservados.</span><span class="sxs-lookup"><span data-stu-id="de437-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="de437-156">Este é o comportamento padrão para [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de437-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="de437-157">Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente.</span><span class="sxs-lookup"><span data-stu-id="de437-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="de437-158">Você pode não querer modificar este recuo de nenhuma forma.</span><span class="sxs-lookup"><span data-stu-id="de437-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="de437-159">No [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você pode fazer isso preservando o espaço em branco ao carregar ou analisar o XML e desabilitando a formatação ao serializar o XML.</span><span class="sxs-lookup"><span data-stu-id="de437-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 <span data-ttu-id="de437-160">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] armazena o espaço em branco como um nó de <xref:System.Xml.Linq.XText>, em vez de ter um tipo de nó especializado do <xref:System.Xml.XmlNodeType.Whitespace>, assim como o DOM.</span><span class="sxs-lookup"><span data-stu-id="de437-160">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="de437-161">Suporte para anotações</span><span class="sxs-lookup"><span data-stu-id="de437-161">Support for Annotations</span></span>  
 <span data-ttu-id="de437-162">Elementos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dão suporte a um conjunto extensível de anotações.</span><span class="sxs-lookup"><span data-stu-id="de437-162">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] elements support an extensible set of annotations.</span></span> <span data-ttu-id="de437-163">Isso é útil para acompanhar informações variadas sobre um elemento, como informações de esquema, informações sobre se o elemento está associado a uma interface do usuário ou qualquer outro tipo de informações específicas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="de437-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="de437-164">Para obter mais informações, consulte [Anotações LINQ to XML (C#)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="de437-164">For more information, see [LINQ to XML Annotations](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="de437-165">Suporte para informações do esquema</span><span class="sxs-lookup"><span data-stu-id="de437-165">Support for Schema Information</span></span>  
 <span data-ttu-id="de437-166">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dá suporte para validação de XSD por meio de métodos de extensão no namespace <xref:System.Xml.Schema?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de437-166">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="de437-167">Você pode validar que uma árvore XML está em conformidade com XSD.</span><span class="sxs-lookup"><span data-stu-id="de437-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="de437-168">Você pode preencher a árvore XML com o PSVI (post-schema-validation infoset).</span><span class="sxs-lookup"><span data-stu-id="de437-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="de437-169">Para obter mais informações, consulte [Como validar usando XSD](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) e <xref:System.Xml.Schema.Extensions>.</span><span class="sxs-lookup"><span data-stu-id="de437-169">For more information, see [How to: Validate Using XSD](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de437-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de437-170">See Also</span></span>  
 [<span data-ttu-id="de437-171">Introdução (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="de437-171">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
