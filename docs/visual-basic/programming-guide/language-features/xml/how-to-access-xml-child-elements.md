---
title: Como acessar elementos filho XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 4ec7743a30b8101d813ac414a8f5164aeb6c593d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649198"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Como acessar elementos filho XML (Visual Basic)
Este exemplo mostra como usar um filho de propriedade de eixo para acessar todos os elementos filho XML que têm um nome especificado em um elemento XML. Em particular, ele usa o <xref:System.Xml.Linq.XElement.Value%2A> propriedade para obter o valor do primeiro elemento na coleção de `name` retorna de propriedade de eixo filho. O `name` propriedade de eixo filho obtém todos os elementos filho denominados `phone` no `contact` objeto. Este exemplo também usa o `phone` propriedade de eixo filho para acessar todos os elementos filho denominados `phone` que estão contidos no `contact` objeto.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma referência para o <xref:System.Xml.Linq> namespace.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>  
 [Propriedade do Eixo Filho XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [Propriedade do Valor XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
