---
title: Como converter uma cadeia de caracteres em uma matriz de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: c109143601e304b1ec15a60c71d65fe6bd15aae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Como converter uma cadeia de caracteres em uma matriz de caracteres no Visual Basic
Às vezes é útil ter dados sobre os caracteres na cadeia de caracteres e as posições desses caracteres na cadeia de caracteres, como quando você estiver analisando uma cadeia de caracteres. Este exemplo mostra como você pode obter uma matriz de caracteres em uma cadeia de caracteres chamando a cadeia de caracteres <xref:System.String.ToCharArray%2A> método.  
  
## <a name="example"></a>Exemplo  
 Este exemplo demonstra como dividir uma cadeia de caracteres em uma `Char` matriz e como dividir uma cadeia de caracteres em um `String` matriz de seus caracteres de texto Unicode. A razão para essa distinção é que caracteres Unicode de texto podem ser compostos de dois ou mais `Char` caracteres (como um par substituto ou uma combinação sequência de caracteres). Para obter mais informações, consulte <xref:System.Globalization.TextElementEnumerator> e "The Unicode Standard" em http://www.unicode.org.  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a>Exemplo  
 É mais difícil dividir uma cadeia de caracteres em seus caracteres Unicode de texto, mas isso é necessário se você precisar de informações sobre a representação visual de uma cadeia de caracteres. Este exemplo usa o <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> método para obter informações sobre os caracteres de texto Unicode que compõem uma cadeia de caracteres.  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [Como acessar caracteres em cadeias de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [Convertendo cadeias de caracteres em outros tipos de dados no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Cadeias de Caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)
