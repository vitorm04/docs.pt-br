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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 12885f93bb7e56dd66d36090d41700195313e944
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-classes-overview-visual-basic"></a>LINQ to XML visão geral de Classes (Visual Basic)
Este tópico fornece uma lista da [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes o <xref:System.Xml.Linq>namespace e uma breve descrição de cada um.</xref:System.Xml.Linq>  
  
## <a name="linq-to-xml-classes"></a>Classes LINQ to XML  
  
### <a name="xattribute-class"></a>Classe XAttribute  
 <xref:System.Xml.Linq.XAttribute>representa um atributo XML.</xref:System.Xml.Linq.XAttribute> Para obter informações detalhadas e exemplos, consulte [(Visual Basic) Visão geral da classe XAttribute](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>Classe XCData  
 <xref:System.Xml.Linq.XCData>representa um nó de texto CDATA.</xref:System.Xml.Linq.XCData>  
  
### <a name="xcomment-class"></a>Classe XComment  
 <xref:System.Xml.Linq.XComment>representa um comentário XML.</xref:System.Xml.Linq.XComment>  
  
### <a name="xcontainer-class"></a>Classe XContainer  
 <xref:System.Xml.Linq.XContainer>é uma classe base abstrata para todos os nós que podem ter nós filho.</xref:System.Xml.Linq.XContainer> As seguintes classes derivam de <xref:System.Xml.Linq.XContainer>classe:</xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>Classe XDeclaration  
 <xref:System.Xml.Linq.XDeclaration>representa uma declaração XML.</xref:System.Xml.Linq.XDeclaration> Uma declaração XML é usada para declarar a versão XML e a codificação de um documento. Além disso, uma declaração XML especifica se o documento XML é autônomo. Se um documento é autônomo, não há nenhuma declaração de marcação externa, em um DTD externo, ou uma entidade de parâmetro externo referenciada do subconjunto interno.  
  
### <a name="xdocument-class"></a>Classe XDocument  
 <xref:System.Xml.Linq.XDocument>representa um documento XML.</xref:System.Xml.Linq.XDocument> Para obter informações detalhadas e exemplos, consulte [visão geral da classe XDocument (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>Classe XDocumentType  
 <xref:System.Xml.Linq.XDocumentType>representa uma definição de tipo de documento (DTD) XML.</xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xelement-class"></a>Classe XElement  
 <xref:System.Xml.Linq.XElement>representa um elemento XML.</xref:System.Xml.Linq.XElement> Para obter informações detalhadas e exemplos, consulte [(Visual Basic) Visão geral da classe XElement](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).  
  
### <a name="xname-class"></a>Classe XName  
 <xref:System.Xml.Linq.XName>representa os nomes dos elementos (<xref:System.Xml.Linq.XElement>) e atributos (<xref:System.Xml.Linq.XAttribute>).</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XName> Para obter informações detalhadas e exemplos, consulte [visão geral da classe XDocument (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é criado para simplificar ao máximo os nomes XML. Devido à complexidade, nomes XML são geralmente considerados um tópico avançado em XML. Sem dúvida, essa complexidade vem não de namespaces, que os desenvolvedores usam regularmente em programação, mas dos prefixos de namespace. Prefixos de Namespace podem ser útil para reduzir os pressionamentos de teclas necessários quando o XML de entrada, ou para facilitar a leitura de XML. No entanto, prefixos geralmente são apenas um atalho para usar o namespace XML completo e não são necessários na maioria dos casos. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]simplifica os nomes XML resolvendo todos os prefixos para o namespace XML correspondente. Prefixos estão disponíveis, se forem necessários, por meio de <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A>método.</xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A>  
  
 É possível, se necessário, controlar os prefixos de namespace. Em algumas circunstâncias, se você estiver trabalhando com outros sistemas XML, como XSLT ou XAML, você precisará controlar os prefixos de namespace. Por exemplo, se você tiver uma expressão XPath que usa prefixos de namespace e está inserida em uma folha de estilos XSLT, verifique se o documento XML está serializado com prefixos de namespace que coincidem com os usados na expressão XPath.  
  
### <a name="xnamespace-class"></a>Classe XNamespace  
 <xref:System.Xml.Linq.XNamespace>representa um namespace para um <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XNamespace> Namespaces são um componente de <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName>  
  
### <a name="xnode-class"></a>Classe XNode  
 <xref:System.Xml.Linq.XNode>é uma classe abstrata que representa os nós de uma árvore XML.</xref:System.Xml.Linq.XNode> As seguintes classes derivam de <xref:System.Xml.Linq.XNode>classe:</xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XText></xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType></xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>Classe XNodeDocumentOrderComparer  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer>fornece a funcionalidade para comparar nós para sua ordem do documento.</xref:System.Xml.Linq.XNodeDocumentOrderComparer>  
  
### <a name="xnodeequalitycomparer-class"></a>Classe XNodeEqualityComparer  
 <xref:System.Xml.Linq.XNodeEqualityComparer>fornece funcionalidade para comparar nós para igualdade de valor.</xref:System.Xml.Linq.XNodeEqualityComparer>  
  
### <a name="xobject-class"></a>Classe XObject  
 <xref:System.Xml.Linq.XObject>é uma classe base abstrata e <xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XNode></xref:System.Xml.Linq.XObject> Ele fornece a anotação e a funcionalidade de evento.  
  
### <a name="xobjectchange-class"></a>Classe XObjectChange  
 <xref:System.Xml.Linq.XObjectChange>Especifica o tipo de evento quando um evento é gerado para <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></xref:System.Xml.Linq.XObjectChange>  
  
### <a name="xobjectchangeeventargs-class"></a>Classe XObjectChangeEventArgs  
 <xref:System.Xml.Linq.XObjectChangeEventArgs>Fornece dados para o <xref:System.Xml.Linq.XObject.Changing>e <xref:System.Xml.Linq.XObject.Changed>eventos.</xref:System.Xml.Linq.XObject.Changed> </xref:System.Xml.Linq.XObject.Changing></xref:System.Xml.Linq.XObjectChangeEventArgs>  
  
### <a name="xprocessinginstruction-class"></a>Classe XProcessingInstruction  
 <xref:System.Xml.Linq.XProcessingInstruction>representa uma instrução de processamento XML.</xref:System.Xml.Linq.XProcessingInstruction> Uma instrução de processamento comunica informações a um aplicativo que processa o XML.  
  
### <a name="xtext-class"></a>Classe XText  
 <xref:System.Xml.Linq.XText>representa um nó de texto.</xref:System.Xml.Linq.XText> Na maioria dos casos, você não tem que usar esta classe. Essa classe é usada principalmente para conteúdo misto.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ para visão geral da programação XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
