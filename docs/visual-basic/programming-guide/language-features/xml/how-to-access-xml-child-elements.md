---
title: 'Como: acessar elementos filho XML (Visual Basic) | Documentos do Microsoft'
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
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
caps.latest.revision: 18
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
ms.openlocfilehash: 1468650e22955329031d6e05e8bd0210b03767dc
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Como acessar elementos filho XML (Visual Basic)
Este exemplo mostra como usar um filho de propriedade de eixo para acessar todos os elementos filho XML que têm um nome especificado em um elemento XML. Em particular, ele usa o <xref:System.Xml.Linq.XElement.Value%2A>propriedade para obter o valor do primeiro elemento na coleção de `name` retorna de propriedade de eixo filho.</xref:System.Xml.Linq.XElement.Value%2A> O `name` propriedade de eixo filho obtém todos os elementos filho chamados `phone` no `contact` objeto. Este exemplo também usa o `phone` propriedade do eixo filho para acessar todos os elementos filho chamados `phone` que estão contidos no `contact` objeto.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbXMLSamples n º&10;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma referência para o <xref:System.Xml.Linq>namespace.</xref:System.Xml.Linq>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>   
 [Propriedade de eixo filho XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)   
 [Propriedade de valor XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)   
 [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
