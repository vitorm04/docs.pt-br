---
title: Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 08ad2f1c9455853e92533a7f00726c73b6adb87e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071151"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres (Visual Basic)

Este exemplo cria a cadeia "abcd" de caracteres individuais.  
  
## <a name="example"></a>Exemplo  

 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a>Compilar o código  

 Esse método não tem requisitos especiais.  
  
 A sintaxe `"a"c` , em que um único `c` segue um único caractere entre aspas, é usada para criar um literal de caractere.  
  
## <a name="robust-programming"></a>Programação robusta  

 Caracteres nulos (equivalente a `Chr(0)` ) na cadeia de caracteres levam a resultados inesperados ao usar a cadeia de caracteres. O caractere nulo será incluído com a cadeia de caracteres, mas os caracteres após o caractere nulo não serão exibidos em algumas situações.  
  
## <a name="see-also"></a>Confira também

- <xref:System.String>
- [Tipo de Dados de Caractere](../../../language-reference/data-types/char-data-type.md)
- [Data Types](../data-types/index.md)
