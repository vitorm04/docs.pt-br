---
title: Espaço em branco em literais XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 08be345557d10a528aa03234883eba1b3a31beaa
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832743"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>Espaço em branco em literais XML (Visual Basic)
O compilador do Visual Basic incorpora somente os caracteres de espaço em branco significativo de um literal XML quando ele cria um [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objeto. Os caracteres de espaço em branco insignificante não são incorporados.  
  
## <a name="significant-and-insignificant-white-space"></a>Espaço em branco significativo e irrisória  
 Caracteres de espaço em branco em literais XML são significativos em apenas três áreas:  
  
-   Quando eles estão em um valor de atributo.  
  
-   Quando eles fazem parte de um elemento conteúdo de texto e o texto também contiver outros caracteres.  
  
-   Quando eles estão em uma expressão inserida para o conteúdo de texto de um elemento.  
  
 Caso contrário, o compilador trata caracteres de espaço em branco como insignificante e não inclui, em seguida, no [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objeto para o literal.  
  
 Para incluir espaço em branco insignificante em um literal XML, use uma expressão inserida que contém uma cadeia de caracteres literal com o espaço em branco.  
  
> [!NOTE]
>  Se o `xml:space` atributo é exibido em um elemento XML literal, o compilador do Visual Basic inclui o atributo no <xref:System.Xml.Linq.XElement> objeto, mas adicionando esse atributo não altera como o compilador trata espaços em branco.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir contém dois elementos XML, externos e internos. Ambos os elementos de contenham espaço em branco em seu conteúdo de texto. O espaço em branco no elemento externo é insignificante, porque ele contém apenas espaços em branco e um elemento XML. O espaço em branco no elemento interno é significativo porque ele contém espaço em branco e texto.  
  
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
