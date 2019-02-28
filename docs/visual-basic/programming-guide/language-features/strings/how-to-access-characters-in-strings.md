---
title: 'Como: Caracteres de acesso em cadeias de caracteres no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: f2831333008844c959c3625698fce6c485450683
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967549"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Como: Caracteres de acesso em cadeias de caracteres no Visual Basic
Este exemplo demonstra como usar o <xref:System.String.Chars%2A> propriedade para acessar o caractere no local especificado em uma cadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 Às vezes é útil ter dados sobre os caracteres na cadeia de caracteres e as posições desses caracteres na cadeia de caracteres. Você pode pensar em uma cadeia de caracteres como uma matriz de caracteres (`Char` instâncias); você pode recuperar um determinado caractere consultando o índice do caractere através de <xref:System.String.Chars%2A> propriedade.  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 O `index` parâmetro do <xref:System.String.Chars%2A> propriedade é baseado em zero.  
  
## <a name="robust-programming"></a>Programação robusta  
 O <xref:System.String.Chars%2A> propriedade retorna o caractere na posição especificada. No entanto, alguns caracteres Unicode podem ser representados por mais de um caractere. Para obter mais informações sobre como trabalhar com caracteres Unicode, consulte [como: Converter uma cadeia de caracteres em uma matriz de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 O <xref:System.String.Chars%2A> propriedade gera uma <xref:System.IndexOutOfRangeException> exceção se o `index` parâmetro é maior que ou igual ao comprimento da cadeia de caracteres, ou se ele for menor que zero  
  
## <a name="see-also"></a>Consulte também
- <xref:System.String.Chars%2A>
- [Como: Converter uma cadeia de caracteres em uma matriz de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [Convertendo cadeias de caracteres em outros tipos de dados no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Cadeias de Caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)
