---
title: "Como: determinar a cadeia de caracteres associada a um valor de enumeração (Visual Basic) | Documentos do Microsoft"
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
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values, enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
caps.latest.revision: 12
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
ms.openlocfilehash: 193d14ae8df4d67ed22d44e1e4ca1983558c07f2
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Como determinar a cadeia de caracteres associada a um valor de enumeração (Visual Basic)
O <xref:System.Enum.GetValues%2A>e <xref:System.Enum.GetNames%2A>métodos permitem que você determine as cadeias de caracteres e valores associados a membros de enumeração.</xref:System.Enum.GetNames%2A> </xref:System.Enum.GetValues%2A>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Para determinar a cadeia de caracteres associada a uma enumeração  
  
-   Use o <xref:System.Enum.GetNames%2A>método para recuperar as cadeias de caracteres associadas com os membros de enumeração.</xref:System.Enum.GetNames%2A> Este exemplo declara uma enumeração, `flavorEnum`, em seguida, usa o <xref:System.Enum.GetNames%2A>método para exibir as cadeias de caracteres associadas a cada membro.</xref:System.Enum.GetNames%2A>  
  
     [!code-vb[VbEnumsTask n º&2;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Enum.GetValues%2A></xref:System.Enum.GetValues%2A>   
 <xref:System.Enum.GetNames%2A></xref:System.Enum.GetNames%2A>   
 <xref:System.Enum></xref:System.Enum>   
 [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Como: fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Como: iterar por uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [Quando usar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
