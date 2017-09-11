---
title: "Visão geral (Visual Basic) de Classes LINQ to XML | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8c999860ed04c754855792d814cd3801f5f92c90
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-xml-classes-overview-visual-basic"></a><span data-ttu-id="9907d-102">LINQ to XML visão geral de Classes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9907d-102">LINQ to XML Classes Overview (Visual Basic)</span></span>
<span data-ttu-id="9907d-103">Este tópico fornece uma lista da [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes o <xref:System.Xml.Linq>namespace e uma breve descrição de cada um.</xref:System.Xml.Linq></span><span class="sxs-lookup"><span data-stu-id="9907d-103">This topic provides a list of the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="9907d-104">Classes LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="9907d-104">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="9907d-105">Classe XAttribute</span><span class="sxs-lookup"><span data-stu-id="9907d-105">XAttribute Class</span></span>  
 <span data-ttu-id="9907d-106"><xref:System.Xml.Linq.XAttribute>representa um atributo XML.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="9907d-106"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="9907d-107">Para obter informações detalhadas e exemplos, consulte [(Visual Basic) Visão geral da classe XAttribute](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9907d-107">For detailed information and examples, see [XAttribute Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="9907d-108">Classe XCData</span><span class="sxs-lookup"><span data-stu-id="9907d-108">XCData Class</span></span>  
 <span data-ttu-id="9907d-109"><xref:System.Xml.Linq.XCData>representa um nó de texto CDATA.</xref:System.Xml.Linq.XCData></span><span class="sxs-lookup"><span data-stu-id="9907d-109"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="9907d-110">Classe XComment</span><span class="sxs-lookup"><span data-stu-id="9907d-110">XComment Class</span></span>  
 <span data-ttu-id="9907d-111"><xref:System.Xml.Linq.XComment>representa um comentário XML.</xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="9907d-111"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="9907d-112">Classe XContainer</span><span class="sxs-lookup"><span data-stu-id="9907d-112">XContainer Class</span></span>  
 <span data-ttu-id="9907d-113"><xref:System.Xml.Linq.XContainer>é uma classe base abstrata para todos os nós que podem ter nós filho.</xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="9907d-113"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="9907d-114">As seguintes classes derivam de <xref:System.Xml.Linq.XContainer>classe:</xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="9907d-114">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
-   <span data-ttu-id="9907d-115"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="9907d-115"><xref:System.Xml.Linq.XElement></span></span>  
  
-   <span data-ttu-id="9907d-116"><xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="9907d-116"><xref:System.Xml.Linq.XDocument></span></span>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="9907d-117">Classe XDeclaration</span><span class="sxs-lookup"><span data-stu-id="9907d-117">XDeclaration Class</span></span>  
 <span data-ttu-id="9907d-118"><xref:System.Xml.Linq.XDeclaration>representa uma declaração XML.</xref:System.Xml.Linq.XDeclaration></span><span class="sxs-lookup"><span data-stu-id="9907d-118"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="9907d-119">Uma declaração XML é usada para declarar a versão XML e a codificação de um documento.</span><span class="sxs-lookup"><span data-stu-id="9907d-119">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="9907d-120">Além disso, uma declaração XML especifica se o documento XML é autônomo.</span><span class="sxs-lookup"><span data-stu-id="9907d-120">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="9907d-121">Se um documento é autônomo, não há nenhuma declaração de marcação externa, em um DTD externo, ou uma entidade de parâmetro externo referenciada do subconjunto interno.</span><span class="sxs-lookup"><span data-stu-id="9907d-121">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="9907d-122">Classe XDocument</span><span class="sxs-lookup"><span data-stu-id="9907d-122">XDocument Class</span></span>  
 <span data-ttu-id="9907d-123"><xref:System.Xml.Linq.XDocument>representa um documento XML.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="9907d-123"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="9907d-124">Para obter informações detalhadas e exemplos, consulte [visão geral da classe XDocument (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9907d-124">For detailed information and examples, see [XDocument Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="9907d-125">Classe XDocumentType</span><span class="sxs-lookup"><span data-stu-id="9907d-125">XDocumentType Class</span></span>  
 <span data-ttu-id="9907d-126"><xref:System.Xml.Linq.XDocumentType>representa uma definição de tipo de documento (DTD) XML.</xref:System.Xml.Linq.XDocumentType></span><span class="sxs-lookup"><span data-stu-id="9907d-126"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="9907d-127">Classe XElement</span><span class="sxs-lookup"><span data-stu-id="9907d-127">XElement Class</span></span>  
 <span data-ttu-id="9907d-128"><xref:System.Xml.Linq.XElement>representa um elemento XML.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="9907d-128"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="9907d-129">Para obter informações detalhadas e exemplos, consulte [(Visual Basic) Visão geral da classe XElement](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9907d-129">For detailed information and examples, see [XElement Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="9907d-130">Classe XName</span><span class="sxs-lookup"><span data-stu-id="9907d-130">XName Class</span></span>  
 <span data-ttu-id="9907d-131"><xref:System.Xml.Linq.XName>representa os nomes dos elementos (<xref:System.Xml.Linq.XElement>) e atributos (<xref:System.Xml.Linq.XAttribute>).</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="9907d-131"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="9907d-132">Para obter informações detalhadas e exemplos, consulte [visão geral da classe XDocument (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9907d-132">For detailed information and examples, see [XDocument Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="9907d-133"> é criado para simplificar ao máximo os nomes XML.</span><span class="sxs-lookup"><span data-stu-id="9907d-133"> is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="9907d-134">Devido à complexidade, nomes XML são geralmente considerados um tópico avançado em XML.</span><span class="sxs-lookup"><span data-stu-id="9907d-134">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="9907d-135">Sem dúvida, essa complexidade vem não de namespaces, que os desenvolvedores usam regularmente em programação, mas dos prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="9907d-135">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="9907d-136">Prefixos de Namespace podem ser útil para reduzir os pressionamentos de teclas necessários quando o XML de entrada, ou para facilitar a leitura de XML.</span><span class="sxs-lookup"><span data-stu-id="9907d-136">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="9907d-137">No entanto, prefixos geralmente são apenas um atalho para usar o namespace XML completo e não são necessários na maioria dos casos.</span><span class="sxs-lookup"><span data-stu-id="9907d-137">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="9907d-138">simplifica os nomes XML resolvendo todos os prefixos para o namespace XML correspondente.</span><span class="sxs-lookup"><span data-stu-id="9907d-138"> simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="9907d-139">Prefixos estão disponíveis, se forem necessários, por meio de <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A>método.</xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="9907d-139">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="9907d-140">É possível, se necessário, controlar os prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="9907d-140">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="9907d-141">Em algumas circunstâncias, se você estiver trabalhando com outros sistemas XML, como XSLT ou XAML, você precisará controlar os prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="9907d-141">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="9907d-142">Por exemplo, se você tiver uma expressão XPath que usa prefixos de namespace e está inserida em uma folha de estilos XSLT, verifique se o documento XML está serializado com prefixos de namespace que coincidem com os usados na expressão XPath.</span><span class="sxs-lookup"><span data-stu-id="9907d-142">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="9907d-143">Classe XNamespace</span><span class="sxs-lookup"><span data-stu-id="9907d-143">XNamespace Class</span></span>  
 <span data-ttu-id="9907d-144"><xref:System.Xml.Linq.XNamespace>representa um namespace para um <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="9907d-144"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="9907d-145">Namespaces são um componente de <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="9907d-145">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="9907d-146">Classe XNode</span><span class="sxs-lookup"><span data-stu-id="9907d-146">XNode Class</span></span>  
 <span data-ttu-id="9907d-147"><xref:System.Xml.Linq.XNode>é uma classe abstrata que representa os nós de uma árvore XML.</xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="9907d-147"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="9907d-148">As seguintes classes derivam de <xref:System.Xml.Linq.XNode>classe:</xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="9907d-148">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
-   <span data-ttu-id="9907d-149"><xref:System.Xml.Linq.XText></xref:System.Xml.Linq.XText></span><span class="sxs-lookup"><span data-stu-id="9907d-149"><xref:System.Xml.Linq.XText></span></span>  
  
-   <span data-ttu-id="9907d-150"><xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="9907d-150"><xref:System.Xml.Linq.XContainer></span></span>  
  
-   <span data-ttu-id="9907d-151"><xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="9907d-151"><xref:System.Xml.Linq.XComment></span></span>  
  
-   <span data-ttu-id="9907d-152"><xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="9907d-152"><xref:System.Xml.Linq.XProcessingInstruction></span></span>  
  
-   <span data-ttu-id="9907d-153"><xref:System.Xml.Linq.XDocumentType></xref:System.Xml.Linq.XDocumentType></span><span class="sxs-lookup"><span data-stu-id="9907d-153"><xref:System.Xml.Linq.XDocumentType></span></span>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="9907d-154">Classe XNodeDocumentOrderComparer</span><span class="sxs-lookup"><span data-stu-id="9907d-154">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="9907d-155"><xref:System.Xml.Linq.XNodeDocumentOrderComparer>fornece a funcionalidade para comparar nós para sua ordem do documento.</xref:System.Xml.Linq.XNodeDocumentOrderComparer></span><span class="sxs-lookup"><span data-stu-id="9907d-155"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="9907d-156">Classe XNodeEqualityComparer</span><span class="sxs-lookup"><span data-stu-id="9907d-156">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="9907d-157"><xref:System.Xml.Linq.XNodeEqualityComparer>fornece funcionalidade para comparar nós para igualdade de valor.</xref:System.Xml.Linq.XNodeEqualityComparer></span><span class="sxs-lookup"><span data-stu-id="9907d-157"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="9907d-158">Classe XObject</span><span class="sxs-lookup"><span data-stu-id="9907d-158">XObject Class</span></span>  
 <span data-ttu-id="9907d-159"><xref:System.Xml.Linq.XObject>é uma classe base abstrata e <xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XNode></xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="9907d-159"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="9907d-160">Ele fornece a anotação e a funcionalidade de evento.</span><span class="sxs-lookup"><span data-stu-id="9907d-160">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="9907d-161">Classe XObjectChange</span><span class="sxs-lookup"><span data-stu-id="9907d-161">XObjectChange Class</span></span>  
 <span data-ttu-id="9907d-162"><xref:System.Xml.Linq.XObjectChange>Especifica o tipo de evento quando um evento é gerado para <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></xref:System.Xml.Linq.XObjectChange></span><span class="sxs-lookup"><span data-stu-id="9907d-162"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="9907d-163">Classe XObjectChangeEventArgs</span><span class="sxs-lookup"><span data-stu-id="9907d-163">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="9907d-164"><xref:System.Xml.Linq.XObjectChangeEventArgs>Fornece dados para o <xref:System.Xml.Linq.XObject.Changing>e <xref:System.Xml.Linq.XObject.Changed>eventos.</xref:System.Xml.Linq.XObject.Changed> </xref:System.Xml.Linq.XObject.Changing></xref:System.Xml.Linq.XObjectChangeEventArgs></span><span class="sxs-lookup"><span data-stu-id="9907d-164"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="9907d-165">Classe XProcessingInstruction</span><span class="sxs-lookup"><span data-stu-id="9907d-165">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="9907d-166"><xref:System.Xml.Linq.XProcessingInstruction>representa uma instrução de processamento XML.</xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="9907d-166"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="9907d-167">Uma instrução de processamento comunica informações a um aplicativo que processa o XML.</span><span class="sxs-lookup"><span data-stu-id="9907d-167">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="9907d-168">Classe XText</span><span class="sxs-lookup"><span data-stu-id="9907d-168">XText Class</span></span>  
 <span data-ttu-id="9907d-169"><xref:System.Xml.Linq.XText>representa um nó de texto.</xref:System.Xml.Linq.XText></span><span class="sxs-lookup"><span data-stu-id="9907d-169"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="9907d-170">Na maioria dos casos, você não tem que usar esta classe.</span><span class="sxs-lookup"><span data-stu-id="9907d-170">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="9907d-171">Essa classe é usada principalmente para conteúdo misto.</span><span class="sxs-lookup"><span data-stu-id="9907d-171">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9907d-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9907d-172">See Also</span></span>  
 [<span data-ttu-id="9907d-173">LINQ para visão geral da programação XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9907d-173">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
