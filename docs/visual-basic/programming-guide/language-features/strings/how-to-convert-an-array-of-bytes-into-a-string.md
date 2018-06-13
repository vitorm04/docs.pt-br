---
title: Como converter uma matriz de bytes em uma cadeia de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: c22ae89322230d8a98ae3ae2c1485e73456e0a7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648968"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>Como converter uma matriz de bytes em uma cadeia de caracteres no Visual Basic
Este tópico mostra como converter os bytes de uma matriz de bytes em uma cadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Text.Encoding.GetString%2A> método o <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> classe para converter todos os bytes de uma matriz de bytes em uma cadeia de caracteres de codificação.  
  
 [!code-vb[VbVbalrStrings#72](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-an-array-of-bytes-into-a-string_1.vb)]  
  
 Você pode escolher entre várias opções de codificação para converter uma matriz de bytes em uma cadeia de caracteres:  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Obtém uma codificação de caracteres ASCII (7 bits) do conjunto.  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte big-endian.  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Obtém uma codificação para a página de código ANSI atual do sistema.  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte little-endian.  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-32 usando a ordem de byte little-endian.  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-7.  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-8.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetString%2A>  
 [Como: converter cadeias de caracteres em uma matriz de Bytes no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
