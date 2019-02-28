---
title: 'Como: Iterar por meio de uma enumeração no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: dd7a540839fd833d3a316506e433c576edae5384
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979080"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Como: Iterar por meio de uma enumeração no Visual Basic
Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores de constante a nomes. Para iterar por meio de uma enumeração, você pode movê-lo em uma matriz usando o <xref:System.Enum.GetValues%2A> método. Você também pode iterar por meio de uma enumeração usando um `For...Each` instrução, usando o <xref:System.Enum.GetNames%2A> ou <xref:System.Enum.GetValues%2A> método para extrair o valor de cadeia de caracteres ou numérica.  
  
### <a name="to-iterate-through-an-enumeration"></a>Para iterar por meio de uma enumeração  
  
-   Declarar uma matriz e converter a enumeração a ele com o <xref:System.Enum.GetValues%2A> método antes de passar a matriz como você faria qualquer outra variável. O exemplo a seguir exibe cada membro da enumeração <xref:Microsoft.VisualBasic.FirstDayOfWeek> conforme ela itera por meio da enumeração.  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de Enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Como: Declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Quando Usar uma Enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Como: Determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Como: Fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Enumerações e Qualificação de Nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
