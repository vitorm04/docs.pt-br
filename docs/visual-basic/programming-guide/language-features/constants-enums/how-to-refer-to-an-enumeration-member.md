---
title: "Como: fazer referência a um membro de enumeração (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values, associating constant values with names
- enumeration members
- constants, enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2f825bd28d1eb56cee563a0c50ade88d938e794d
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a>Como fazer referência a um membro de enumeração (Visual Basic)
Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e associar valores constantes com nomes. Por exemplo, você pode declarar uma enumeração de um conjunto de constantes de inteiro associados com os dias da semana e, em seguida, usar os nomes de dias em vez de seus valores inteiros em seu código.  
  
 Você pode evitar o uso de nomes totalmente qualificados com o `Imports` instrução. Para obter mais informações, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-refer-to-an-enumeration-member"></a>Para fazer referência a um membro de enumeração  
  
-   Qualifica o nome do membro com a enumeração. Por exemplo, o exemplo a seguir atribui o `Saturday` membro o `FirstDayOfWeek` enumeração à variável `DayValue`.  
  
     [!code-vb[19 VbEnumsTask](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Como: iterar por uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [Como: determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Quando Usar uma Enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
