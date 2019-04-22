---
title: 'Como: Elementos descendentes de XML de acesso (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: bfbf849bd296f639f03580346e4a9c52ce000abd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832210"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Como: Elementos descendentes de XML de acesso (Visual Basic)
Este exemplo mostra como usar uma propriedade de eixo descendente para acessar todos os elementos XML que têm um nome especificado e que estão contidas em um elemento XML. Em particular, ele usa o `Value` propriedade para obter o valor do primeiro elemento na coleção que o `name` retorna da propriedade de eixo descendente. O `name` propriedade de eixo descendente obtém todos os elementos chamados `name` que estão contidos no `contacts` objeto. Este exemplo também usa o `phone` propriedade de eixo descendente para acessar todos os descendentes nomeados `phone` que estão contidos no `contacts` objeto.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma referência para o <xref:System.Xml.Linq> namespace.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [Propriedade de Eixo Descendente XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [Propriedade do Valor XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
