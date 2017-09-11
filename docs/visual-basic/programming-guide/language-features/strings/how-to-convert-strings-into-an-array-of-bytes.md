---
title: 'Como: converter cadeias de caracteres em uma matriz de Bytes no Visual Basic | Documentos do Microsoft'
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
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
caps.latest.revision: 8
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e32d72c3be1e4ef4d717b6154b52e53a625325f2
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a><span data-ttu-id="78c4f-102">Como converter cadeias de caracteres em uma matriz de bytes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="78c4f-102">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>
<span data-ttu-id="78c4f-103">Este tópico mostra como converter uma cadeia de caracteres em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="78c4f-103">This topic shows how to convert a string into an array of bytes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78c4f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="78c4f-104">Example</span></span>  
 <span data-ttu-id="78c4f-105">Este exemplo usa o <xref:System.Text.Encoding.GetBytes%2A>método o <xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName>classe para converter uma cadeia de caracteres em uma matriz de bytes de codificação.</xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName> </xref:System.Text.Encoding.GetBytes%2A></span><span class="sxs-lookup"><span data-stu-id="78c4f-105">This example uses the <xref:System.Text.Encoding.GetBytes%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName> encoding class to convert a string into an array of bytes.</span></span>  
  
 <span data-ttu-id="78c4f-106">[!code-vb[VbVbalrStrings&#74;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="78c4f-106">[!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]</span></span>  
  
 <span data-ttu-id="78c4f-107">Você pode escolher entre várias opções de codificação para converter uma cadeia de caracteres em uma matriz de bytes:</span><span class="sxs-lookup"><span data-stu-id="78c4f-107">You can choose from several encoding options to convert a string into a byte array:</span></span>  
  
-   <span data-ttu-id="78c4f-108"><xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName>: Obtém uma codificação de caracteres ASCII (7 bits) do conjunto.</xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="78c4f-108"><xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="78c4f-109"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte big-endian.</xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="78c4f-109"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=fullName>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="78c4f-110"><xref:System.Text.Encoding.Default%2A?displayProperty=fullName>: Obtém uma codificação de página de código ANSI atual do sistema.</xref:System.Text.Encoding.Default%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="78c4f-110"><xref:System.Text.Encoding.Default%2A?displayProperty=fullName>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="78c4f-111"><xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte little-endian.</xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="78c4f-111"><xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="78c4f-112"><xref:System.Text.Encoding.UTF32%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-32 usando a ordem de byte little-endian.</xref:System.Text.Encoding.UTF32%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="78c4f-112"><xref:System.Text.Encoding.UTF32%2A?displayProperty=fullName>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="78c4f-113"><xref:System.Text.Encoding.UTF7%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-7.</xref:System.Text.Encoding.UTF7%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="78c4f-113"><xref:System.Text.Encoding.UTF7%2A?displayProperty=fullName>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="78c4f-114"><xref:System.Text.Encoding.UTF8%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-8.</xref:System.Text.Encoding.UTF8%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="78c4f-114"><xref:System.Text.Encoding.UTF8%2A?displayProperty=fullName>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78c4f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78c4f-115">See Also</span></span>  
 <span data-ttu-id="78c4f-116"><xref:System.Text.Encoding?displayProperty=fullName></xref:System.Text.Encoding?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="78c4f-116"><xref:System.Text.Encoding?displayProperty=fullName></span></span>   
 <span data-ttu-id="78c4f-117"><xref:System.Text.Encoding.GetBytes%2A></xref:System.Text.Encoding.GetBytes%2A></span><span class="sxs-lookup"><span data-stu-id="78c4f-117"><xref:System.Text.Encoding.GetBytes%2A></span></span>   
<span data-ttu-id="78c4f-118"> [Como: converter uma matriz de Bytes em uma cadeia de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)</span><span class="sxs-lookup"><span data-stu-id="78c4f-118"> [How to: Convert an Array of Bytes into a String in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)</span></span>
