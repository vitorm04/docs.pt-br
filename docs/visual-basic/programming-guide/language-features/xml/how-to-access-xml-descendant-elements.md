---
title: 'Como: acessar elementos descendentes XML (Visual Basic) | Documentos do Microsoft'
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
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
caps.latest.revision: 19
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
ms.openlocfilehash: 4b614de10da5508eecdff9625976c1a68a3085a6
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Como acessar elementos descendentes XML (Visual Basic)
Este exemplo mostra como usar uma propriedade de eixo descendente para acessar todos os elementos XML que têm um nome especificado e que estão contidas em um elemento XML. Em particular, ele usa o `Value` propriedade para obter o valor do primeiro elemento na coleção de `name` retorna de propriedade de eixo descendente. O `name` propriedade de eixo descendente obtém todos os elementos chamados `name` que estão contidos no `contacts` objeto. Este exemplo também usa o `phone` propriedade de eixo descendente para acessar todos os descendentes nomeados `phone` que estão contidos no `contacts` objeto.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbXMLSamples&#31;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma referência para o <xref:System.Xml.Linq>namespace.</xref:System.Xml.Linq>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName>   
 [Propriedade de eixo descendente XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)   
 [Propriedade de valor XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)   
 [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
