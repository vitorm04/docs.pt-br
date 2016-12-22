---
title: "Como acessar elementos descendentes XML (Visual Basic) | Microsoft Docs"
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
  - "propriedade de eixo descendente [Visual Basic]"
  - "XML [Visual Basic], acessando"
  - "eixo XML [Visual Basic], descendente"
  - "propriedade de eixo descendente XML [Visual Basic]"
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como acessar elementos descendentes XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Esse exemplo mostra como usar uma propriedade do eixo descendente para acessar todos os elementos XML que possuem um nome especificado e que estão contidas em um elemento XML.  Em particular, ele usa a propriedade `Value` para obter o valor do primeiro elemento na coleção que a propriedade do eixo descendente `name` retorna.  A propriedade do eixo descendente `name` obtém todos os elementos chamados `name` que estão contidos no objeto `contacts`.  Este exemplo também usa a propriedade do eixo descendente `phone` para acessar todos os descendentes chamados `phone` que estão contidos no objeto `contacts`.  
  
## Exemplo  
 [!CODE [VbXMLSamples#31](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#31)]  
  
## Compilando o código  
 Este exemplo requer:  
  
-   Uma referência ao namespace <xref:System.Xml.Linq>.  
  
## Consulte também  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName>   
 [Propriedade de eixo descendente XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)   
 [Propriedade do valor XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)   
 [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)