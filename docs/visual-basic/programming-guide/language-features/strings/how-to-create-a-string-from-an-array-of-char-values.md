---
title: 'Como: criar uma cadeia de caracteres de uma matriz de valores de caracteres (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e4bff22ad489500736a2a563d924e1b1a8133d17
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres (Visual Basic)
Este exemplo cria a cadeia de caracteres "abcd" de caracteres individuais.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrStrings&#61;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este método não possui requisitos especiais.  
  
 A sintaxe `"a"c`, onde um único `c` segue um único caractere entre aspas, é usada para criar um caractere literal.  
  
## <a name="robust-programming"></a>Programação robusta  
 Caracteres nulos (equivalente a `Chr(0)`) na sequência levar a resultados inesperados ao usar a cadeia de caracteres. O caractere nulo será incluído com a cadeia de caracteres, mas caracteres após o caractere nulo não serão exibidos em algumas situações.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.String></xref:System.String>   
 [Tipo de dados char](../../../../visual-basic/language-reference/data-types/char-data-type.md)   
 [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
