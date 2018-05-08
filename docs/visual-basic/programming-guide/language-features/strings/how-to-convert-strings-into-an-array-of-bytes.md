---
title: Como converter cadeias de caracteres em uma matriz de bytes no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: da4a47b955b91f4bb39ecd7832da30d76e75d553
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>Como converter cadeias de caracteres em uma matriz de bytes no Visual Basic
Este tópico mostra como converter uma cadeia de caracteres em uma matriz de bytes.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Text.Encoding.GetBytes%2A> método o <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> codificação classe para converter uma cadeia de caracteres em uma matriz de bytes.  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 Você pode escolher entre várias opções de codificação para converter uma cadeia de caracteres em uma matriz de bytes:  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Obtém uma codificação de caracteres ASCII (7 bits) do conjunto.  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte big-endian.  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Obtém uma codificação para a página de código ANSI atual do sistema.  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte little-endian.  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-32 usando a ordem de byte little-endian.  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-7.  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-8.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetBytes%2A>  
 [Como: converter uma matriz de Bytes em uma cadeia de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
