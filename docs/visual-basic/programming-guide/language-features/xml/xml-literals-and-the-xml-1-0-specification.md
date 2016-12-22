---
title: "Especifica&#231;&#227;o dos literais XML e do XML 1.0 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "literais XML [Visual Basic], especificação XML 1.0"
ms.assetid: 46f046e5-293c-41a3-b893-4e5f6e32e78a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Especifica&#231;&#227;o dos literais XML e do XML 1.0 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

A sintaxe do literal XML no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] oferece suporte à maior parte da especificação do Extensible Markup Language \(XML\) 1.0.  Para obter detalhes sobre a especificação XML 1.0, consulte [Linguagem de marcação extensível \(XML\) 1.0](http://go.microsoft.com/fwlink/?LinkId=73927) no site do W3C.  
  
## O que o Visual Basic não suporta  
  
-   Um literal XML não pode conter um Document Type Definition \(DTD\).  
  
-   Um documento literal XML deve começar com uma declaração de documento XML.  
  
-   Um literal XML não pode conter mais de 65.535 caracteres em uma linha.  
  
-   Namespace, prefixos, nomes de elemento, e nomes de atributo do XML não podem conter mais de 1.024 caracteres.  
  
## Recursos adicionais que Visual Basic suporta  
  
-   A sintaxe de expressão incorporada permitida em documentos e literais de elemento não é XML válido.  
  
## Consulte também  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Literal de documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [Literal do elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)