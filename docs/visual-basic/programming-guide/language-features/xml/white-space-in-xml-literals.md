---
title: Espaço em branco em literais XML
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 56ededeb12d07e979bc86b03924e1ae0f0432822
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336002"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>Espaço em branco em literais XML (Visual Basic)
O compilador Visual Basic incorpora apenas os caracteres de espaço em branco significativos de um literal XML quando ele cria um objeto [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Os caracteres de espaço em branco insignificantes não são incorporados.  
  
## <a name="significant-and-insignificant-white-space"></a>Espaço em branco significativo e insignificante  
 Os caracteres de espaço em branco em literais XML são significativos em apenas três áreas:  
  
- Quando estão em um valor de atributo.  
  
- Quando eles fazem parte do conteúdo de texto de um elemento e o texto também contém outros caracteres.  
  
- Quando estão em uma expressão inserida para o conteúdo de texto de um elemento.  
  
 Caso contrário, o compilador trata caracteres de espaço em branco como insignificantes e não inclui, em seguida, no objeto [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] para o literal.  
  
 Para incluir um espaço em branco insignificante em um literal XML, use uma expressão inserida que contenha um literal de cadeia de caracteres com o espaço em branco.  
  
> [!NOTE]
> Se o atributo `xml:space` aparecer em um literal de elemento XML, o compilador Visual Basic incluirá o atributo no objeto <xref:System.Xml.Linq.XElement>, mas a adição desse atributo não alterará a forma como o compilador trata o espaço em branco.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir contém dois elementos XML, externo e interno. Ambos os elementos contêm espaço em branco em seu conteúdo de texto. O espaço em branco no elemento externo é insignificante porque contém apenas espaços em branco e um elemento XML. O espaço em branco no elemento interno é significativo porque contém espaço em branco e texto.  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 Quando executado, esse código exibe o texto a seguir.  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Consulte também

- [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
