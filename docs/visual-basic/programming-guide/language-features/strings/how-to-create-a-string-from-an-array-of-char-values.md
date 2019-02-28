---
title: 'Como: Criar uma cadeia de caracteres de uma matriz de valores Char (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 0d3a4caf0967ab77de7d91470e43e52521dbd2da
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975505"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Como: Criar uma cadeia de caracteres de uma matriz de valores Char (Visual Basic)
Este exemplo cria a cadeia de caracteres "abcd" dos caracteres individuais.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Esse método não tem nenhum requisito especial.  
  
 A sintaxe `"a"c`, onde um único `c` segue um único caractere entre aspas, é usado para criar um caractere literal.  
  
## <a name="robust-programming"></a>Programação robusta  
 Caracteres nulos (equivalente a `Chr(0)`) na cadeia de caracteres levar a resultados inesperados ao usar a cadeia de caracteres. O caractere nulo será incluído com a cadeia de caracteres, mas os caracteres após o caractere nulo não serão exibidos em algumas situações.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.String>
- [Tipo de Dados de Caractere](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
