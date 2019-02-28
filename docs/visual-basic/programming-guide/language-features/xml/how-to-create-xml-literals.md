---
title: 'Como: Criar literais XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: c79b607f9ce5c779539b7700feafb7d4e3d67d24
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974244"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>Como: Criar literais XML (Visual Basic)
Você pode criar um documento, fragmento ou elemento XML diretamente no código usando um literal XML. Os exemplos neste tópico demonstram como criar um elemento XML que tem três elementos filho e como criar um documento XML.  
  
 Você também pode usar o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs para criar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objetos. Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.  
  
### <a name="to-create-an-xml-element"></a>Para criar um elemento XML  
  
-   Crie o XML embutido usando a sintaxe de literais XML, que é o mesmo que a sintaxe XML real.  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     Execute o código. A saída desse código é:  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>Para criar um documento XML  
  
-   Crie o documento XML embutido. O código a seguir cria um documento XML que tem sintaxe literal, uma declaração XML, uma instrução de processamento, um comentário e um elemento que contém outro elemento.  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     Execute o código. A saída desse código é:  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>Consulte também
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Literal do Elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literal de Documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
