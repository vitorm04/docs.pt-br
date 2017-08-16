---
title: 'Como: acessar caracteres em cadeias de caracteres no Visual Basic | Documentos do Microsoft'
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
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
caps.latest.revision: 8
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
ms.openlocfilehash: ac276d7daf838f847a86d23d05585d8e93a93f17
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Como acessar caracteres em cadeias de caracteres no Visual Basic
Este exemplo demonstra como usar o <xref:System.String.Chars%2A>propriedade para acessar o caractere no local especificado em uma cadeia de caracteres.</xref:System.String.Chars%2A>  
  
## <a name="example"></a>Exemplo  
 Às vezes é útil ter dados sobre os caracteres na cadeia de caracteres e as posições desses caracteres na cadeia de caracteres. Você pode pensar em uma cadeia de caracteres como uma matriz de caracteres (`Char` instâncias); você pode recuperar um determinado caractere consultando o índice do caractere através do <xref:System.String.Chars%2A>propriedade.</xref:System.String.Chars%2A>  
  
 [!code-vb[49 VbVbalrStrings](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 O `index` parâmetro o <xref:System.String.Chars%2A>propriedade é baseada em zero.</xref:System.String.Chars%2A>  
  
## <a name="robust-programming"></a>Programação robusta  
 O <xref:System.String.Chars%2A>propriedade retorna o caractere na posição especificada.</xref:System.String.Chars%2A> No entanto, alguns caracteres Unicode podem ser representados por mais de um caractere. Para obter mais informações sobre como trabalhar com caracteres Unicode, consulte [como: converter uma cadeia de caracteres em uma matriz de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 O <xref:System.String.Chars%2A>propriedade lança um <xref:System.IndexOutOfRangeException>exceção se o `index` parâmetro for maior ou igual ao comprimento da cadeia de caracteres, ou se ele for menor que zero</xref:System.IndexOutOfRangeException> </xref:System.String.Chars%2A>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.String.Chars%2A></xref:System.String.Chars%2A>   
 [Como: converter uma cadeia de caracteres em uma matriz de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)   
 [Convertendo entre cadeias de caracteres e outros tipos de dados no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)   
 [Cadeias de Caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)
