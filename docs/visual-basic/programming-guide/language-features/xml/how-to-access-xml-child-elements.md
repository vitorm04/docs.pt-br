---
title: Como acessar elementos filho XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 32bdb1ba476a954bdad1f23c3ecc6129c90ccaac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347170"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Como acessar elementos filho XML (Visual Basic)
Este exemplo mostra como usar uma propriedade de eixo filho para acessar todos os elementos filho XML que têm um nome especificado em um elemento XML. Em particular, ele usa a propriedade <xref:System.Xml.Linq.XElement.Value%2A> para obter o valor do primeiro elemento na coleção que a propriedade de eixo filho `name` retorna. A propriedade do eixo filho `name` Obtém todos os elementos filho chamados `phone` no objeto `contact`. Este exemplo também usa a propriedade de eixo filho `phone` para acessar todos os elementos filho chamados `phone` contidos no objeto `contact`.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a>Compilar o código  
 Este exemplo requer:  
  
- Uma referência ao namespace <xref:System.Xml.Linq>.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [Propriedade do Eixo Filho XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Propriedade do Valor XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
