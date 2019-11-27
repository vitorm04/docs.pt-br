---
title: 'Como: iterar por meio de uma enumeração'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 6e8fd6760565a73d9d3b3d1d02fc872992eea354
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354019"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Como iterar em uma enumeração no Visual Basic
Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores de constante a nomes. Para iterar por meio de uma enumeração, você pode movê-lo para uma matriz usando o método <xref:System.Enum.GetValues%2A>. Você também pode iterar através de uma enumeração usando uma instrução `For...Each`, usando o método <xref:System.Enum.GetNames%2A> ou <xref:System.Enum.GetValues%2A> para extrair a cadeia de caracteres ou o valor numérico.  
  
### <a name="to-iterate-through-an-enumeration"></a>Para iterar por meio de uma enumeração  
  
- Declare uma matriz e converta a enumeração para ela com o método <xref:System.Enum.GetValues%2A> antes de passar a matriz, como faria com qualquer outra variável. O exemplo a seguir exibe cada membro da enumeração <xref:Microsoft.VisualBasic.FirstDayOfWeek> conforme ele é iterado por meio da enumeração.  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de Enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Como declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Quando Usar uma Enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Como determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Como fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Enumerações e Qualificação de Nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
