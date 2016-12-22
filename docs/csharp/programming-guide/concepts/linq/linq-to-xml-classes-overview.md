---
title: "LINQ para vis&#227;o geral das Classes XML (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# LINQ para vis&#227;o geral das Classes XML (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico fornece uma lista da [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes de <xref:System.Xml.Linq> namespace e uma breve descrição de cada.  
  
## Classes LINQ to XML  
  
### Classe XAttribute  
 <xref:System.Xml.Linq.XAttribute> representa um atributo XML. Para obter informações detalhadas e exemplos, consulte [Visão geral da classe XAttribute \(c\#\)](../../../../csharp/programming-guide/concepts/linq/xattribute-class-overview.md).  
  
### Classe XCData  
 <xref:System.Xml.Linq.XCData> representa um nó de texto CDATA.  
  
### Classe XComment  
 <xref:System.Xml.Linq.XComment> representa um comentário XML.  
  
### Classe XContainer  
 <xref:System.Xml.Linq.XContainer> é uma classe base abstrata para todos os nós que podem ter nós filho. As seguintes classes derivam de <xref:System.Xml.Linq.XContainer> classe:  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument>  
  
### Classe XDeclaration  
 <xref:System.Xml.Linq.XDeclaration> representa uma declaração XML. Uma declaração XML é usada para declarar a versão XML e a codificação de um documento. Além disso, uma declaração XML Especifica se o documento XML é autônomo. Se um documento é autônomo, não há nenhuma declaração de marcação externa, em um DTD externo ou em uma entidade de parâmetro externo referenciada do subconjunto interno.  
  
### Classe XDocument  
 <xref:System.Xml.Linq.XDocument> representa um documento XML. Para obter informações detalhadas e exemplos, consulte [Visão geral da classe XDocument \(c\#\)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
### Classe XDocumentType  
 <xref:System.Xml.Linq.XDocumentType> representa uma definição de tipo de documento \(DTD\) XML.  
  
### Classe XElement  
 <xref:System.Xml.Linq.XElement> representa um elemento XML. Para obter informações detalhadas e exemplos, consulte [Visão geral da classe de XElement \(c\#\)](../../../../csharp/programming-guide/concepts/linq/xelement-class-overview.md).  
  
### Classe XName  
 <xref:System.Xml.Linq.XName> representa os nomes dos elementos \(<xref:System.Xml.Linq.XElement>\) e atributos \(<xref:System.Xml.Linq.XAttribute>\). Para obter informações detalhadas e exemplos, consulte [Visão geral da classe XDocument \(c\#\)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é projetado para tornar os nomes XML mais direta possível. Devido à complexidade, nomes XML são geralmente considerados um tópico avançado em XML. Sem dúvida, essa complexidade vem não de namespaces, que os desenvolvedores usam regularmente em programação, mas dos prefixos de namespace. Prefixos de namespace podem ser útil para reduzir os pressionamentos de teclas necessários quando o XML de entrada, ou para facilitar a leitura de XML. No entanto, prefixos geralmente são apenas um atalho para usar o namespace XML completo e não são necessários na maioria dos casos.[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] simplifica os nomes XML resolvendo todos os prefixos para o namespace XML correspondente. Prefixos estão disponíveis, se forem necessários, por meio de <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> método.  
  
 É possível, se necessário, para prefixos de namespace do controle. Em algumas circunstâncias, se você estiver trabalhando com outros sistemas XML, como XSLT ou XAML, você precisa controlar prefixos de namespace. Por exemplo, se você tiver uma expressão XPath que usa prefixos de namespace e é inserida em uma folha de estilos XSLT, você deve garantir que o documento XML é serializado com prefixos de namespace que coincidem com os usados na expressão XPath.  
  
### Classe XNamespace  
 <xref:System.Xml.Linq.XNamespace> representa um namespace para um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>. Namespaces são um componente de um <xref:System.Xml.Linq.XName>.  
  
### Classe XNode  
 <xref:System.Xml.Linq.XNode> é uma classe abstrata que representa os nós de uma árvore XML. As seguintes classes derivam de <xref:System.Xml.Linq.XNode> classe:  
  
-   <xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType>  
  
### Classe XNodeDocumentOrderComparer  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer> fornece a funcionalidade para comparar nós para sua ordem do documento.  
  
### Classe XNodeEqualityComparer  
 <xref:System.Xml.Linq.XNodeEqualityComparer> fornece funcionalidade para comparar nós para igualdade de valor.  
  
### Classe XObject  
 <xref:System.Xml.Linq.XObject> é uma classe base abstrata de <xref:System.Xml.Linq.XNode> e <xref:System.Xml.Linq.XAttribute>. Ele fornece funcionalidade de anotação e eventos.  
  
### Classe XObjectChange  
 <xref:System.Xml.Linq.XObjectChange> Especifica o tipo de evento quando um evento é gerado para um <xref:System.Xml.Linq.XObject>.  
  
### Classe XObjectChangeEventArgs  
 <xref:System.Xml.Linq.XObjectChangeEventArgs> Fornece dados para o <xref:System.Xml.Linq.XObject.Changing> e <xref:System.Xml.Linq.XObject.Changed> eventos.  
  
### Classe XProcessingInstruction  
 <xref:System.Xml.Linq.XProcessingInstruction> representa uma instrução de processamento XML. Uma instrução de processamento comunica informações a um aplicativo que processa o XML.  
  
### Classe XText  
 <xref:System.Xml.Linq.XText> representa um nó de texto. Na maioria dos casos, você não precisa usar essa classe. Essa classe é usada principalmente para conteúdo misto.  
  
## Consulte também  
 [LINQ to XML visão geral da programação \(c\#\)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)