---
title: "Preservar espaço em branco ao carregar ou analisar XML2 | Documentos do Microsoft"
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
ms.assetid: ef6518e0-2c8d-462c-8b92-a16e9dc737ad
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
ms.openlocfilehash: 39e4270acc0e9a9df5c3855f8c087f41d9612197
ms.lasthandoff: 03/13/2017

---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>Preservar espaço em branco para carregar ou ao analisar XML
Este tópico descreve como controlar o comportamento de espaço em branco de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Um cenário comum é ler o XML recuado, criar uma árvore XML na memória sem nenhum nó de texto de espaço em branco (isto é, não preservar espaço em branco), executar algumas operações no XML e, em seguida, salvar o XML com recuo. Quando você serializa o XML com formatação, somente os espaços em branco significativos na árvore XML são preservados. Este é o comportamento padrão para [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente. Você pode não querer modificar este recuo de nenhuma forma. Para fazer isso em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], você preserva o espaço em branco quando você carregar ou analisar XML e desativa o formatação quando você serializa XML.  
  
 Este tópico descreve o comportamento de espaço em branco dos métodos que preenchem árvores XML. Para obter informações sobre como controlar o espaço em branco quando você serializa árvores XML, consulte [preservar espaço em branco ao serializar](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>Comportamento dos métodos que preenchem árvores XML  
 Os seguintes métodos na <xref:System.Xml.Linq.XElement>e <xref:System.Xml.Linq.XDocument>classes preencher uma árvore XML.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> Você pode preencher uma árvore XML de um arquivo, um <xref:System.IO.TextReader>, um <xref:System.Xml.XmlReader>, ou uma cadeia de caracteres:</xref:System.Xml.XmlReader> </xref:System.IO.TextReader>  
  
-   <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>  
  
 Se o método não utiliza <xref:System.Xml.Linq.LoadOptions>como um argumento, o método não irá preservar espaço em branco insignificante.</xref:System.Xml.Linq.LoadOptions>  
  
 Na maioria dos casos, se o método usa <xref:System.Xml.Linq.LoadOptions>como um argumento, você pode opcionalmente preservar espaço em branco irrisória como nós de texto na árvore XML.</xref:System.Xml.Linq.LoadOptions> No entanto, se o método é carregar XML de um <xref:System.Xml.XmlReader>, o <xref:System.Xml.XmlReader>determina se o espaço em branco será preservado ou não.</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader> Definindo <xref:System.Xml.Linq.LoadOptions>não terá efeito.</xref:System.Xml.Linq.LoadOptions>  
  
 Com esses métodos, se o espaço em branco é preservado, espaço em branco irrisória é inserido na árvore XML como <xref:System.Xml.Linq.XText>nós.</xref:System.Xml.Linq.XText> Se o espaço em branco não é preservada, os nós de texto não são inseridos.  
  
 Você pode criar uma árvore XML usando <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> Nós que são gravados para o <xref:System.Xml.XmlWriter>são preenchidos na árvore.</xref:System.Xml.XmlWriter> No entanto, quando você cria uma árvore XML usando esse método, todos os nós são mantidos, independentemente se o nó é o espaço em branco ou não, ou se o espaço em branco é significativo ou não.  
  
## <a name="see-also"></a>Consulte também  
 [Análise de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
