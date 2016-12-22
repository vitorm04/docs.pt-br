---
title: "Como acessar elementos filho XML (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "propriedade de eixo filho [Visual Basic]"
  - "XML [Visual Basic], acessando"
  - "eixo XML [Visual Basic], filho"
  - "propriedade de eixo filho XML [Visual Basic]"
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como acessar elementos filho XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como usar uma propriedade do eixo filho para acessar todos os elementos filho XML que têm um nome especificado em um elemento XML.  Em particular, ele usa a propriedade <xref:System.Xml.Linq.XElement.Value%2A> para obter o valor do primeiro elemento na coleção que a propriedade do eixo filho `name` retorna.  A propriedade do eixo filho `name` obtém todos os elementos filho chamados `phone` no objeto `contact`.  Este exemplo também usa a propriedade do eixo filho `phone` para acessar todos os elementos chamados `phone` que estão contidos no objeto filho `contact`.  
  
## Exemplo  
 [!CODE [VbXMLSamples#10](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#10)]  
  
## Compilando o código  
 Este exemplo requer:  
  
-   Uma referência ao namespace <xref:System.Xml.Linq>.  
  
## Consulte também  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>   
 [Propriedade do eixo filho XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)   
 [Propriedade do valor XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)   
 [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)