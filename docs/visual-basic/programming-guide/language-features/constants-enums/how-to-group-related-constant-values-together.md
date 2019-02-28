---
title: 'Como: Agrupar valores constantes relacionados juntos (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 63475487c8a35f5b306b28d4e7097324bef00d85
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977819"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Como: Agrupar valores constantes relacionados juntos (Visual Basic)
Uma enumeração é a melhor maneira de agrupar constantes relacionadas. Você cria uma enumeração com o `Enum` instrução na seção de declarações de uma classe ou um módulo. Para obter mais informações, confira [Como: Declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>Para o grupo de valores constantes relacionados  
  
1.  Escrever uma declaração que inclui um nível de acesso do código, o `Enum` palavra-chave e um nome válido. Este exemplo cria o `Private` enumeração, `temperatureValues`.  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2.  Defina as constantes na enumeração. Este exemplo cria o `Public` enumeração `temperatureValues` e atribui seus valores.  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>Consulte também
- [Enumerações e Qualificação de Nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Como: Fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Quando Usar uma Enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Visão Geral de Constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Tipos de Dados Constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)
