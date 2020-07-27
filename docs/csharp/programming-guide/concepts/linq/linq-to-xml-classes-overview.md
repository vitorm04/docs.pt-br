---
title: Visão geral de classes LINQ to XML (C#)
description: Este artigo resume as classes de LINQ to XML em C# na System.Xml. Namespace LINQ, com uma breve descrição de cada um.
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 34508f86792cdc7589569b8f12584ffc4379a5fb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165426"
---
# <a name="linq-to-xml-classes-overview-c"></a><span data-ttu-id="95b2b-103">Visão geral de classes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="95b2b-103">LINQ to XML Classes Overview (C#)</span></span>
<span data-ttu-id="95b2b-104">Este tópico fornece uma lista das classes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] no namespace <xref:System.Xml.Linq> e uma breve descrição de cada.</span><span class="sxs-lookup"><span data-stu-id="95b2b-104">This topic provides a list of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="95b2b-105">Classes LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="95b2b-105">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="95b2b-106">Classe XAttribute</span><span class="sxs-lookup"><span data-stu-id="95b2b-106">XAttribute Class</span></span>  
 <span data-ttu-id="95b2b-107"><xref:System.Xml.Linq.XAttribute> representa um atributo XML.</span><span class="sxs-lookup"><span data-stu-id="95b2b-107"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="95b2b-108">Para obter informações detalhadas e exemplos, consulte [Visão geral da classe XAttribute (C#)](./xattribute-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="95b2b-108">For detailed information and examples, see [XAttribute Class Overview (C#)](./xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="95b2b-109">Classe XCData</span><span class="sxs-lookup"><span data-stu-id="95b2b-109">XCData Class</span></span>  
 <span data-ttu-id="95b2b-110"><xref:System.Xml.Linq.XCData> representa um nó de texto CDATA.</span><span class="sxs-lookup"><span data-stu-id="95b2b-110"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="95b2b-111">Classe XComment</span><span class="sxs-lookup"><span data-stu-id="95b2b-111">XComment Class</span></span>  
 <span data-ttu-id="95b2b-112"><xref:System.Xml.Linq.XComment> representa um comentário XML.</span><span class="sxs-lookup"><span data-stu-id="95b2b-112"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="95b2b-113">Classe XContainer</span><span class="sxs-lookup"><span data-stu-id="95b2b-113">XContainer Class</span></span>  
 <span data-ttu-id="95b2b-114"><xref:System.Xml.Linq.XContainer> é uma classe base abstrata para todos os nós que podem ter nós filho.</span><span class="sxs-lookup"><span data-stu-id="95b2b-114"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="95b2b-115">As seguintes classes derivam da classe <xref:System.Xml.Linq.XContainer>:</span><span class="sxs-lookup"><span data-stu-id="95b2b-115">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="95b2b-116">Classe XDeclaration</span><span class="sxs-lookup"><span data-stu-id="95b2b-116">XDeclaration Class</span></span>  
 <span data-ttu-id="95b2b-117"><xref:System.Xml.Linq.XDeclaration> representa uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="95b2b-117"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="95b2b-118">Uma declaração XML é usada para declarar a versão XML e a codificação de um documento.</span><span class="sxs-lookup"><span data-stu-id="95b2b-118">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="95b2b-119">Além disso, uma declaração XML especifica se o documento XML é autônomo.</span><span class="sxs-lookup"><span data-stu-id="95b2b-119">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="95b2b-120">Se um documento é autônomo, não há nenhuma declaração de marcação externa, em um DTD externo, ou uma entidade de parâmetro externo referenciada do subconjunto interno.</span><span class="sxs-lookup"><span data-stu-id="95b2b-120">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="95b2b-121">Classe XDocument</span><span class="sxs-lookup"><span data-stu-id="95b2b-121">XDocument Class</span></span>  
 <span data-ttu-id="95b2b-122"><xref:System.Xml.Linq.XDocument> representa um documento XML.</span><span class="sxs-lookup"><span data-stu-id="95b2b-122"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="95b2b-123">Para obter informações detalhadas e exemplos, consulte [Visão geral da classe XDocument (C#)](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="95b2b-123">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="95b2b-124">Classe XDocumentType</span><span class="sxs-lookup"><span data-stu-id="95b2b-124">XDocumentType Class</span></span>  
 <span data-ttu-id="95b2b-125"><xref:System.Xml.Linq.XDocumentType> representa um DTD (definição de tipo de documento) de XML.</span><span class="sxs-lookup"><span data-stu-id="95b2b-125"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="95b2b-126">Classe XElement</span><span class="sxs-lookup"><span data-stu-id="95b2b-126">XElement Class</span></span>  
 <span data-ttu-id="95b2b-127"><xref:System.Xml.Linq.XElement> representa um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="95b2b-127"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="95b2b-128">Para obter informações detalhadas e exemplos, consulte [Visão geral da classe XElement (C#)](./xelement-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="95b2b-128">For detailed information and examples, see [XElement Class Overview (C#)](./xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="95b2b-129">Classe XName</span><span class="sxs-lookup"><span data-stu-id="95b2b-129">XName Class</span></span>  
 <span data-ttu-id="95b2b-130"><xref:System.Xml.Linq.XName> representa nomes de elementos (<xref:System.Xml.Linq.XElement>) e atributos (<xref:System.Xml.Linq.XAttribute>).</span><span class="sxs-lookup"><span data-stu-id="95b2b-130"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="95b2b-131">Para obter informações detalhadas e exemplos, consulte [Visão geral da classe XDocument (C#)](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="95b2b-131">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="95b2b-132">é criado para simplificar ao máximo os nomes XML.</span><span class="sxs-lookup"><span data-stu-id="95b2b-132">is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="95b2b-133">Devido à sua complexidade, nomes XML geralmente são considerados um tópico avançado em XML.</span><span class="sxs-lookup"><span data-stu-id="95b2b-133">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="95b2b-134">Pode-se afirmar que essa complexidade vem não dos namespaces, que os desenvolvedores usam regularmente em programação, mas dos prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="95b2b-134">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="95b2b-135">Prefixos de namespace podem ser úteis para reduzir os pressionamentos de teclas necessários para inserir XML ou para facilitar a leitura de XML.</span><span class="sxs-lookup"><span data-stu-id="95b2b-135">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="95b2b-136">No entanto, os prefixos frequentemente são apenas um atalho para usar o namespace de XML completo e não são necessários na maioria dos casos.</span><span class="sxs-lookup"><span data-stu-id="95b2b-136">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="95b2b-137">simplifica os nomes XML resolvendo todos os prefixos para o namespace de XML correspondente.</span><span class="sxs-lookup"><span data-stu-id="95b2b-137">simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="95b2b-138">Caso necessários, os prefixos estão disponíveis por meio do método <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A>.</span><span class="sxs-lookup"><span data-stu-id="95b2b-138">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="95b2b-139">É possível, se necessário, controlar os prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="95b2b-139">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="95b2b-140">Em algumas circunstâncias, se você estiver trabalhando com outros sistemas XML, como XSLT ou XAML, você precisará controlar os prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="95b2b-140">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="95b2b-141">Por exemplo, se você tiver uma expressão XPath que usa prefixos de namespace e está inserida em uma folha de estilos XSLT, verifique se o documento XML está serializado com prefixos de namespace que coincidem com os usados na expressão XPath.</span><span class="sxs-lookup"><span data-stu-id="95b2b-141">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="95b2b-142">Classe XNamespace</span><span class="sxs-lookup"><span data-stu-id="95b2b-142">XNamespace Class</span></span>  
 <span data-ttu-id="95b2b-143"><xref:System.Xml.Linq.XNamespace> representa um namespace para <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="95b2b-143"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="95b2b-144">Namespaces são um componente de um <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="95b2b-144">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="95b2b-145">Classe XNode</span><span class="sxs-lookup"><span data-stu-id="95b2b-145">XNode Class</span></span>  
 <span data-ttu-id="95b2b-146"><xref:System.Xml.Linq.XNode> é uma classe abstrata que representa os nós de uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="95b2b-146"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="95b2b-147">As seguintes classes derivam da classe <xref:System.Xml.Linq.XNode>:</span><span class="sxs-lookup"><span data-stu-id="95b2b-147">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="95b2b-148">Classe XNodeDocumentOrderComparer</span><span class="sxs-lookup"><span data-stu-id="95b2b-148">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="95b2b-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> fornece a funcionalidade para comparar nós para sua ordem do documento.</span><span class="sxs-lookup"><span data-stu-id="95b2b-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="95b2b-150">Classe XNodeEqualityComparer</span><span class="sxs-lookup"><span data-stu-id="95b2b-150">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="95b2b-151"><xref:System.Xml.Linq.XNodeEqualityComparer> fornece a funcionalidade para comparar nós para igualdade de valor.</span><span class="sxs-lookup"><span data-stu-id="95b2b-151"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="95b2b-152">Classe XObject</span><span class="sxs-lookup"><span data-stu-id="95b2b-152">XObject Class</span></span>  
 <span data-ttu-id="95b2b-153"><xref:System.Xml.Linq.XObject> é uma classe base abstrata de <xref:System.Xml.Linq.XNode> e <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="95b2b-153"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="95b2b-154">Ele fornece a anotação e a funcionalidade de evento.</span><span class="sxs-lookup"><span data-stu-id="95b2b-154">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="95b2b-155">Classe XObjectChange</span><span class="sxs-lookup"><span data-stu-id="95b2b-155">XObjectChange Class</span></span>  
 <span data-ttu-id="95b2b-156"><xref:System.Xml.Linq.XObjectChange> especifica o tipo de evento quando um evento é gerado para um <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="95b2b-156"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="95b2b-157">Classe XObjectChangeEventArgs</span><span class="sxs-lookup"><span data-stu-id="95b2b-157">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="95b2b-158"><xref:System.Xml.Linq.XObjectChangeEventArgs> fornece dados para os eventos de <xref:System.Xml.Linq.XObject.Changing> e de <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="95b2b-158"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="95b2b-159">Classe XProcessingInstruction</span><span class="sxs-lookup"><span data-stu-id="95b2b-159">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="95b2b-160"><xref:System.Xml.Linq.XProcessingInstruction> representa uma instrução de processamento XML.</span><span class="sxs-lookup"><span data-stu-id="95b2b-160"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="95b2b-161">Uma instrução de processamento comunica informações a um aplicativo que processa o XML.</span><span class="sxs-lookup"><span data-stu-id="95b2b-161">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="95b2b-162">Classe XText</span><span class="sxs-lookup"><span data-stu-id="95b2b-162">XText Class</span></span>  
 <span data-ttu-id="95b2b-163"><xref:System.Xml.Linq.XText> representa um nó de texto.</span><span class="sxs-lookup"><span data-stu-id="95b2b-163"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="95b2b-164">Na maioria dos casos, você não tem que usar esta classe.</span><span class="sxs-lookup"><span data-stu-id="95b2b-164">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="95b2b-165">Essa classe é usada principalmente para conteúdo misto.</span><span class="sxs-lookup"><span data-stu-id="95b2b-165">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b2b-166">Confira também</span><span class="sxs-lookup"><span data-stu-id="95b2b-166">See also</span></span>

- [<span data-ttu-id="95b2b-167">Visão geral da programação LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="95b2b-167">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
