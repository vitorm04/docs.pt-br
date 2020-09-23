---
title: Como agrupar valores constantes relacionados
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 0f694aee722e8ce31f663ec9fe52a09a2eb2a958
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058723"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Como agrupar valores constantes relacionados (Visual Basic)

Uma enumeração é a melhor maneira de agrupar constantes relacionadas juntas. Você cria uma enumeração com a `Enum` instrução na seção declarações de uma classe ou um módulo. Para obter mais informações, consulte [como: declarar uma enumeração](how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>Para agrupar valores constantes relacionados  
  
1. Escreva uma declaração que inclua um nível de acesso de código, a `Enum` palavra-chave e um nome válido. Este exemplo cria a `Private` enumeração, `temperatureValues` .  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. Defina as constantes na enumeração. Este exemplo cria a `Public` enumeração `temperatureValues` e atribui seus valores.  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>Confira também

- [Enumerações e qualificação de nome](enumerations-and-name-qualification.md)
- [Como fazer referência a um membro de enumeração](how-to-refer-to-an-enumeration-member.md)
- [Quando usar uma enumeração](when-to-use-an-enumeration.md)
- [Visão geral de constantes](constants-overview.md)
- [Tipos de dados constante e literal](constant-and-literal-data-types.md)
- [Constantes e enumerações](../../../language-reference/constants-and-enumerations.md)
