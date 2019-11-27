---
title: Como determinar a cadeia de caracteres associada a um valor de enumeração
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: c396a4e2ebe973f5be65c3fab5f22cdedb29be1a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351141"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Como determinar a cadeia de caracteres associada a um valor de enumeração (Visual Basic)
Os métodos <xref:System.Enum.GetValues%2A> e <xref:System.Enum.GetNames%2A> permitem que você determine as cadeias de caracteres e os valores associados aos membros da enumeração.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Para determinar a cadeia de caracteres associada a uma enumeração  
  
- Use o método <xref:System.Enum.GetNames%2A> para recuperar as cadeias de caracteres associadas aos membros da enumeração. Este exemplo declara uma enumeração, `flavorEnum`, em seguida, usa o método <xref:System.Enum.GetNames%2A> para exibir as cadeias de caracteres associadas a cada membro.  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [Como declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Como fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Enumerações e Qualificação de Nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Como: iterar por meio de uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Quando Usar uma Enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
