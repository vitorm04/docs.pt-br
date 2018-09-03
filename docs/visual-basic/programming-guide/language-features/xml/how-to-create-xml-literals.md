---
title: Como criar literais XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: e5f8429b3ff02678bf8bf3e9e32bef6eb1a56831
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483613"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>Como criar literais XML (Visual Basic)
Você pode criar um documento, fragmento ou elemento XML diretamente no código usando um literal XML. Os exemplos neste tópico demonstram como criar um elemento XML que tem três elementos filho e como criar um documento XML.  
  
 Você também pode usar o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs para criar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objetos. Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.  
  
### <a name="to-create-an-xml-element"></a>Para criar um elemento XML  
  
-   Crie o XML embutido usando a sintaxe de literais XML, que é o mesmo que a sintaxe XML real.  
  
     [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     Execute o código. A saída desse código é:  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>Para criar um documento XML  
  
-   Crie o documento XML embutido. O código a seguir cria um documento XML que tem sintaxe literal, uma declaração XML, uma instrução de processamento, um comentário e um elemento que contém outro elemento.  
  
     [!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     Execute o código. A saída desse código é:  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>Consulte também  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Literal do Elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Literal de Documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
