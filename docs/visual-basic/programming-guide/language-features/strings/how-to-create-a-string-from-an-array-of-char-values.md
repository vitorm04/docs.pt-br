---
title: Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 104b329011d69e10a2926f31ce5d296759a3cce8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647157"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres (Visual Basic)
Este exemplo cria a cadeia de caracteres "abcd" de caracteres individuais.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este método não tem requisitos especiais.  
  
 A sintaxe `"a"c`, onde um único `c` segue um único caractere entre aspas, é usada para criar um caractere literal.  
  
## <a name="robust-programming"></a>Programação robusta  
 Caracteres nulos (equivalente a `Chr(0)`) na cadeia de levar a resultados inesperados ao usar a cadeia de caracteres. O caractere nulo será incluído com a cadeia de caracteres, mas caracteres após o caractere nulo não serão exibidos em algumas situações.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.String>  
 [Tipo de Dados de Caractere](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
