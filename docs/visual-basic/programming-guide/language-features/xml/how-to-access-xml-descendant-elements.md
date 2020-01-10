---
title: Como acessar elementos descendentes XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: cc045114c67ee2917ef672e734bc852c40d408ac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347166"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Como acessar elementos descendentes XML (Visual Basic)
Este exemplo mostra como usar uma propriedade de eixo descendente para acessar todos os elementos XML que têm um nome especificado e que estão contidos em um elemento XML. Em particular, ele usa a propriedade `Value` para obter o valor do primeiro elemento na coleção que a propriedade do eixo descendente `name` retorna. A propriedade `name` eixo descendente Obtém todos os elementos chamados `name` contidos no objeto `contacts`. Este exemplo também usa a propriedade `phone` eixo descendente para acessar todos os descendentes nomeados `phone` contidos no objeto `contacts`.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a>Compilar o código  
 Este exemplo requer:  
  
- Uma referência ao namespace <xref:System.Xml.Linq>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [Propriedade de Eixo Descendente XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [Propriedade do Valor XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
