---
title: Como iterar em uma enumeração no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 06609d38c805e5f073a2f3a299ecc3aa7cf7be01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Como iterar em uma enumeração no Visual Basic
Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores de constante a nomes. Para iterar por meio de uma enumeração, você pode movê-la em uma matriz usando o <xref:System.Enum.GetValues%2A> método. Você também pode iterar por meio de uma enumeração usando um `For...Each` instrução, usando o <xref:System.Enum.GetNames%2A> ou <xref:System.Enum.GetValues%2A> método para extrair o valor de cadeia de caracteres ou numérica.  
  
### <a name="to-iterate-through-an-enumeration"></a>Para iterar por meio de uma enumeração  
  
-   Declara uma matriz e converter a enumeração com o <xref:System.Enum.GetValues%2A> método antes de passar a matriz como você faria qualquer outra variável. O exemplo a seguir exibe cada membro da enumeração <xref:Microsoft.VisualBasic.FirstDayOfWeek> como ele itera por meio de enumeração.  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de Enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Quando Usar uma Enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Como determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Como fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Enumerações e Qualificação de Nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
