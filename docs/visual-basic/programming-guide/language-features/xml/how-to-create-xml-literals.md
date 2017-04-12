---
title: 'Como: criar literais XML (Visual Basic) | Documentos do Microsoft'
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
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 72d96f36fc17f32ac3ee3ea97175f112fcd21681
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-xml-literals-visual-basic"></a>Como criar literais XML (Visual Basic)
Você pode criar um documento XML, fragmento ou elemento diretamente no código usando um literal XML. Os exemplos neste tópico demonstram como criar um elemento XML que tem três elementos filho e como criar um documento XML.  
  
 Você também pode usar o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] APIs para criar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objetos. Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>  
  
### <a name="to-create-an-xml-element"></a>Para criar um elemento XML  
  
-   Crie o XML embutido usando a sintaxe literal XML, que é o mesmo que a sintaxe XML real.  
  
     [!code-vb[VbXMLSamples n º&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     Execute o código. A saída desse código é:  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>Para criar um documento XML  
  
-   Crie o documento XML embutido. O código a seguir cria um documento XML que tem sintaxe literal, uma declaração XML, uma instrução de processamento, um comentário e um elemento que contém outro elemento.  
  
     [!code-vb[30 VbXMLSamples](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     Execute o código. A saída desse código é:  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>Consulte também  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Literal do elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Literal de Documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
