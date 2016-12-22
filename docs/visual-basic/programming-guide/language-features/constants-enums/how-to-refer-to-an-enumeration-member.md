---
title: "Como fazer refer&#234;ncia a um membro de enumera&#231;&#227;o (Visual Basic) | Microsoft Docs"
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
  - "constantes, enumeradas"
  - "membros de enumeração"
  - "enumerações [Visual Basic], referindo-se a"
  - "Valores, associando valores constantes a nomes"
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como fazer refer&#234;ncia a um membro de enumera&#231;&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar nomes valores constantes.  Por exemplo, você pode declarar uma enumeração de um conjunto de constantes de inteiro associados com os dias da semana e, em seguida, usar os nomes dos dias em vez de seus valores inteiros no seu código.  
  
 Você pode evitar o uso de nomes totalmente qualificados com o `Imports` instrução.  Para obter mais informações, consulte [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### Para se referir a um membro de enumeração  
  
-   Qualifica o nome do membro com a enumeração.  Por exemplo, o exemplo a seguir atribui o `Saturday` membro da `FirstDayOfWeek` enumeração à variável `DayValue`.  
  
     [!code-vb[VbEnumsTask#19](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]  
  
## Consulte também  
 [Como declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Como iterar em uma enumeração no Visual Basic](../Topic/How%20to:%20Iterate%20Through%20An%20Enumeration%20in%20Visual%20Basic.md)   
 [Como determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Quando usar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)