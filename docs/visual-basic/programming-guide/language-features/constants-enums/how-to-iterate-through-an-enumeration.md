---
title: "Como: iterar por uma enumeração no Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
caps.latest.revision: 20
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
ms.openlocfilehash: 56ce450088f56d3e97d6ad7c4447368e67e04647
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Como iterar em uma enumeração no Visual Basic
Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores constantes com nomes. Para iterar por meio de uma enumeração, você pode movê-la para uma matriz usando o <xref:System.Enum.GetValues%2A>método.</xref:System.Enum.GetValues%2A> Você também pode percorrer uma enumeração usando um `For...Each` instrução, usando o <xref:System.Enum.GetNames%2A>ou <xref:System.Enum.GetValues%2A>método para extrair o valor de cadeia de caracteres ou numérica.</xref:System.Enum.GetValues%2A> </xref:System.Enum.GetNames%2A>  
  
### <a name="to-iterate-through-an-enumeration"></a>Para iterar em uma enumeração  
  
-   Declarar uma matriz e converter a enumeração com o <xref:System.Enum.GetValues%2A>método antes de passar a matriz como você faria qualquer outra variável.</xref:System.Enum.GetValues%2A> O exemplo a seguir exibe cada membro da enumeração <xref:Microsoft.VisualBasic.FirstDayOfWeek>como ele itera por meio da enumeração.</xref:Microsoft.VisualBasic.FirstDayOfWeek>  
  
     [!code-vb[VbEnumsTask&#7;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Quando usar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Como: determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Como: fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
