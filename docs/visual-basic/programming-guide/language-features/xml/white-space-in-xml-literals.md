---
title: "Espaço em branco em literais XML (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b98a88696f24cc0b95401812471d13acea4faa6d
ms.lasthandoff: 03/13/2017

---
# <a name="white-space-in-xml-literals-visual-basic"></a>Espaço em branco em literais XML (Visual Basic)
O [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador incorpora somente os caracteres de espaço em branco significativo de um literal XML quando ele cria uma [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objeto. Os caracteres de espaço em branco insignificante não são incorporados.  
  
## <a name="significant-and-insignificant-white-space"></a>Espaço em branco significativo e irrisória  
 Caracteres de espaço em branco em literais XML são significativos apenas três áreas:  
  
-   Quando eles estão em um valor de atributo.  
  
-   Quando eles fazem parte de conteúdo de texto um elemento do e o texto também contém outros caracteres.  
  
-   Quando eles estiverem em uma expressão inserida para o conteúdo de texto de um elemento.  
  
 Caso contrário, o compilador trata caracteres de espaço em branco como insignificante e não inclui, em seguida, o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objeto para o literal.  
  
 Para incluir espaço em branco insignificante em um literal XML, use uma expressão incorporada que contém uma cadeia de caracteres literal com o espaço em branco.  
  
> [!NOTE]
>  Se o `xml:space` atributo aparece em um elemento XML literal, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador inclui o atributo no <xref:System.Xml.Linq.XElement>objeto, mas adicionar esse atributo não alterar como o compilador trata espaços em branco.</xref:System.Xml.Linq.XElement>  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir contém dois elementos XML, externos e internos. Os dois elementos contêm espaços em branco em seu conteúdo de texto. O espaço em branco no elemento externo é insignificante, porque ele contém somente espaço em branco e um elemento XML. O espaço em branco no elemento interno é significativo porque ele contém espaços em branco e texto.  
  
 [!code-vb[29 VbXMLSamples](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 Quando executado, esse código exibe o texto a seguir.  
  
```  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
