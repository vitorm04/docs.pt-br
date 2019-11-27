---
title: Como converter uma cadeia de caracteres em uma matriz de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: d2f7128f97e576d37216d3aa9736921f13f77004
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352453"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Como converter uma cadeia de caracteres em uma matriz de caracteres no Visual Basic
Às vezes, é útil ter dados sobre os caracteres na cadeia de caracteres e as posições desses caracteres em sua cadeia de caracteres, como quando você está analisando uma cadeia de caracteres. Este exemplo mostra como você pode obter uma matriz dos caracteres em uma cadeia de caracteres chamando o método de <xref:System.String.ToCharArray%2A> da cadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 Este exemplo demonstra como dividir uma cadeia de caracteres em uma `Char` matriz e como dividir uma cadeia de caracteres em uma matriz `String` de seus caracteres de texto Unicode. O motivo para essa distinção é que os caracteres de texto Unicode podem ser compostos de dois ou mais caracteres `Char` (como um par alternativo ou uma sequência de caracteres de combinação). Para obter mais informações, consulte <xref:System.Globalization.TextElementEnumerator> e [o padrão Unicode](https://www.unicode.org/standard/standard.html).  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a>Exemplo  
 É mais difícil dividir uma String em seus caracteres de texto Unicode, mas isso é necessário se você precisar de informações sobre a representação visual de uma cadeia de caracteres. Este exemplo usa o método <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> para obter informações sobre os caracteres de texto Unicode que compõem uma cadeia de caracteres.  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [Como acessar caracteres em cadeias de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [Convertendo cadeias de caracteres em outros tipos de dados no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Cadeias de Caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)
