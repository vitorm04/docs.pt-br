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
Este exemplo demonstra como usar a propriedade <xref:System.String.Chars%2A> para acessar o caractere no local especificado em uma cadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 Às vezes, é útil ter dados sobre os caracteres na cadeia de caracteres e as posições desses caracteres na cadeia de caracteres. Você pode considerar uma cadeia de caracteres como uma matriz de personagens (`Char` instâncias); Você pode recuperar um caractere específico referenciando o índice desse caractere por meio da propriedade <xref:System.String.Chars%2A>.  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 O parâmetro `index` da propriedade <xref:System.String.Chars%2A> é baseado em zero.  
  
## <a name="robust-programming"></a>Programação robusta  
 A propriedade <xref:System.String.Chars%2A> retorna o caractere na posição especificada. No entanto, alguns caracteres Unicode podem ser representados por mais de um caractere. Para saber mais sobre como trabalhar com caracteres Unicode, confira [como converter uma cadeia de caracteres em uma matriz de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 A propriedade <xref:System.String.Chars%2A> gera uma exceção de <xref:System.IndexOutOfRangeException> se o parâmetro `index` for maior ou igual ao comprimento da cadeia de caracteres, ou se for menor que zero  
  
## <a name="see-also"></a>Consulte também

- <xref:System.String.Chars%2A>
- [Como converter uma cadeia de caracteres em uma matriz de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [Convertendo cadeias de caracteres em outros tipos de dados no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Cadeias de Caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)
