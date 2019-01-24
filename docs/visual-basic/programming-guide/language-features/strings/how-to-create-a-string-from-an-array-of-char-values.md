---
title: 'Como: Criar uma cadeia de caracteres de uma matriz de valores Char (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: a067474d6b32589a34b031d5c3ea4e5a4be55834
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611456"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Como: Criar uma cadeia de caracteres de uma matriz de valores Char (Visual Basic)
Este exemplo cria a cadeia de caracteres "abcd" dos caracteres individuais.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Esse método não tem nenhum requisito especial.  
  
 A sintaxe `"a"c`, onde um único `c` segue um único caractere entre aspas, é usado para criar um caractere literal.  
  
## <a name="robust-programming"></a>Programação robusta  
 Caracteres nulos (equivalente a `Chr(0)`) na cadeia de caracteres levar a resultados inesperados ao usar a cadeia de caracteres. O caractere nulo será incluído com a cadeia de caracteres, mas os caracteres após o caractere nulo não serão exibidos em algumas situações.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.String>
- [Tipo de Dados de Caractere](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
