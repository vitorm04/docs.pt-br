---
title: Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: bf37ceba901e712df10ad4b39f9ad74194843136
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346766"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres (Visual Basic)
Este exemplo cria a cadeia "abcd" de caracteres individuais.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a>Compilar o código  
 Esse método não tem requisitos especiais.  
  
 A sintaxe `"a"c`, em que uma única `c` segue um único caractere entre aspas, é usada para criar um literal de caractere.  
  
## <a name="robust-programming"></a>Programação Robusta  
 Caracteres nulos (equivalente a `Chr(0)`) na cadeia de caracteres levam a resultados inesperados ao usar a cadeia de caracteres. O caractere nulo será incluído com a cadeia de caracteres, mas os caracteres após o caractere nulo não serão exibidos em algumas situações.  
  
## <a name="see-also"></a>Veja também

- <xref:System.String>
- [Tipo de Dados de Caractere](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
