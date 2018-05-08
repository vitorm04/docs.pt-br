---
title: Como acessar caracteres em cadeias de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 48507cade639660e6ce36697975d09fb29206c20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Como acessar caracteres em cadeias de caracteres no Visual Basic
Este exemplo demonstra como usar o <xref:System.String.Chars%2A> propriedade para acessar o caractere no local especificado em uma cadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 Às vezes é útil ter dados sobre os caracteres na cadeia de caracteres e as posições desses caracteres na cadeia de caracteres. Você pode pensar em uma cadeia de caracteres como uma matriz de caracteres (`Char` instâncias); você pode recuperar um determinado caractere consultando o índice do caractere através de <xref:System.String.Chars%2A> propriedade.  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 O `index` parâmetro o <xref:System.String.Chars%2A> propriedade é baseado em zero.  
  
## <a name="robust-programming"></a>Programação robusta  
 O <xref:System.String.Chars%2A> propriedade retorna o caractere na posição especificada. No entanto, alguns caracteres Unicode podem ser representados por mais de um caractere. Para obter mais informações sobre como trabalhar com caracteres Unicode, consulte [como: converter uma cadeia de caracteres em uma matriz de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 O <xref:System.String.Chars%2A> propriedade gera uma <xref:System.IndexOutOfRangeException> exceção se o `index` parâmetro for maior que ou igual ao comprimento da cadeia de caracteres, ou se ele for menor que zero  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.String.Chars%2A>  
 [Como converter uma cadeia de caracteres em uma matriz de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [Convertendo cadeias de caracteres em outros tipos de dados no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Cadeias de Caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)
