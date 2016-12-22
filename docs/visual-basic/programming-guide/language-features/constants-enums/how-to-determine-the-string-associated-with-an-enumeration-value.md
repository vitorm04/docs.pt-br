---
title: "Como determinar a cadeia de caracteres associada a um valor de enumera&#231;&#227;o (Visual Basic) | Microsoft Docs"
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
  - "enumerações [Visual Basic]"
  - "cadeias de caracteres {Visual Basic], valores de enumeração"
  - "Valores, membros de enumeração"
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como determinar a cadeia de caracteres associada a um valor de enumera&#231;&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Os métodos <xref:System.Enum.GetValues%2A> e <xref:System.Enum.GetNames%2A> permitem que você determine as sequências de caracteres e valores associados com membros de enumeração.  
  
### Para determinar a sequência de caracteres associada com uma enumeração  
  
-   Use o método <xref:System.Enum.GetNames%2A> para recuperar as sequências de caracteres associadas com os membros de enumeração.  Este exemplo declara que uma enumeração, `flavorEnum`,em seguida, usa o método <xref:System.Enum.GetNames%2A> para exibir as sequências de caracteres associadas a cada membro.  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## Consulte também  
 <xref:System.Enum.GetValues%2A>   
 <xref:System.Enum.GetNames%2A>   
 <xref:System.Enum>   
 [Como declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Como fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Como iterar em uma enumeração no Visual Basic](../Topic/How%20to:%20Iterate%20Through%20An%20Enumeration%20in%20Visual%20Basic.md)   
 [Quando usar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)