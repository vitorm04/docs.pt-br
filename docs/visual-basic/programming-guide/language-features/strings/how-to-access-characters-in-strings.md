---
title: Como acessar caracteres em cadeias de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 44a021ed3ce1d10613cf6ab7c959c62feec6046c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352458"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Como acessar caracteres em cadeias de caracteres no Visual Basic
This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.  
  
## <a name="example"></a>Exemplo  
 Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string. You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.  
  
## <a name="robust-programming"></a>Programação robusta  
 The <xref:System.String.Chars%2A> property returns the character at the specified position. However, some Unicode characters can be represented by more than one character. For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero  
  
## <a name="see-also"></a>Consulte também

- <xref:System.String.Chars%2A>
- [Como converter uma cadeia de caracteres em uma matriz de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [Convertendo cadeias de caracteres em outros tipos de dados no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Cadeias de Caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)
