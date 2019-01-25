---
title: 'Como: Determinar a cadeia de caracteres associada a um valor de enumeração (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 92d2e9918429c9cf408f288f832e4615b95ad423
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690183"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Como: Determinar a cadeia de caracteres associada a um valor de enumeração (Visual Basic)
O <xref:System.Enum.GetValues%2A> e <xref:System.Enum.GetNames%2A> métodos permitem determinar as cadeias de caracteres e valores associados a membros de enumeração.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Para determinar a cadeia de caracteres associada a uma enumeração  
  
-   Use o <xref:System.Enum.GetNames%2A> método para recuperar as cadeias de caracteres associadas com os membros de enumeração. Este exemplo declara uma enumeração `flavorEnum`, em seguida, usa o <xref:System.Enum.GetNames%2A> método para exibir as cadeias de caracteres associadas a cada membro.  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [Como: Declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Como: Fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Enumerações e Qualificação de Nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Como: Iterar por meio de uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Quando Usar uma Enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
