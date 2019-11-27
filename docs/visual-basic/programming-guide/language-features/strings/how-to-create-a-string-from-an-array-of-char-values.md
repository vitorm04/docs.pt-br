---
title: Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 03138a851afc55f735cc66edeb345817428a0452
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344395"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres (Visual Basic)
Este exemplo cria a cadeia "abcd" de caracteres individuais.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Esse método não tem requisitos especiais.  
  
 A sintaxe `"a"c`, em que uma única `c` segue um único caractere entre aspas, é usada para criar um literal de caractere.  
  
## <a name="robust-programming"></a>Programação Robusta  
 Caracteres nulos (equivalente a `Chr(0)`) na cadeia de caracteres levam a resultados inesperados ao usar a cadeia de caracteres. O caractere nulo será incluído com a cadeia de caracteres, mas os caracteres após o caractere nulo não serão exibidos em algumas situações.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.String>
- [Tipo de Dados de Caractere](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
