---
title: 'Como: converter uma matriz de Bytes em uma cadeia de caracteres no Visual Basic | Documentos do Microsoft'
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
- string conversion, arrays
- byte arrays, converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
caps.latest.revision: 9
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
ms.openlocfilehash: 0f8c5424ddfa80fb6b0bc6e5b678ca7f099e8bb4
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>Como converter uma matriz de bytes em uma cadeia de caracteres no Visual Basic
Este tópico mostra como converter os bytes de uma matriz de bytes em uma cadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Text.Encoding.GetString%2A>método o <xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName>classe para converter todos os bytes de uma matriz de bytes em uma cadeia de caracteres de codificação.</xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName> </xref:System.Text.Encoding.GetString%2A>  
  
 [!code-vb[VbVbalrStrings&#72;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-an-array-of-bytes-into-a-string_1.vb)]  
  
 Você pode escolher entre várias opções de codificação para converter uma matriz de bytes em uma cadeia de caracteres:  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName>: Obtém uma codificação de caracteres ASCII (7 bits) do conjunto.</xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName>  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte big-endian.</xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=fullName>  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=fullName>: Obtém uma codificação de página de código ANSI atual do sistema.</xref:System.Text.Encoding.Default%2A?displayProperty=fullName>  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte little-endian.</xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName>  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-32 usando a ordem de byte little-endian.</xref:System.Text.Encoding.UTF32%2A?displayProperty=fullName>  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-7.</xref:System.Text.Encoding.UTF7%2A?displayProperty=fullName>  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-8.</xref:System.Text.Encoding.UTF8%2A?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Text.Encoding?displayProperty=fullName></xref:System.Text.Encoding?displayProperty=fullName>   
 <xref:System.Text.Encoding.GetString%2A></xref:System.Text.Encoding.GetString%2A>   
 [Como: converter cadeias de caracteres em uma matriz de Bytes no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
