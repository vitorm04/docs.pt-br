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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: efcbea753a37d74599a87a3bc00394ea34a9074a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="57b9b-102">Como converter uma matriz de bytes em uma cadeia de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57b9b-102">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>
<span data-ttu-id="57b9b-103">Este tópico mostra como converter os bytes de uma matriz de bytes em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="57b9b-103">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57b9b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57b9b-104">Example</span></span>  
 <span data-ttu-id="57b9b-105">Este exemplo usa o <xref:System.Text.Encoding.GetString%2A>método o <xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName>classe para converter todos os bytes de uma matriz de bytes em uma cadeia de caracteres de codificação.</xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName> </xref:System.Text.Encoding.GetString%2A></span><span class="sxs-lookup"><span data-stu-id="57b9b-105">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 <span data-ttu-id="57b9b-106">[!code-vb[VbVbalrStrings&#72;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-an-array-of-bytes-into-a-string_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="57b9b-106">[!code-vb[VbVbalrStrings#72](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-an-array-of-bytes-into-a-string_1.vb)]</span></span>  
  
 <span data-ttu-id="57b9b-107">Você pode escolher entre várias opções de codificação para converter uma matriz de bytes em uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="57b9b-107">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
-   <span data-ttu-id="57b9b-108"><xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName>: Obtém uma codificação de caracteres ASCII (7 bits) do conjunto.</xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="57b9b-108"><xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="57b9b-109"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte big-endian.</xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="57b9b-109"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=fullName>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="57b9b-110"><xref:System.Text.Encoding.Default%2A?displayProperty=fullName>: Obtém uma codificação de página de código ANSI atual do sistema.</xref:System.Text.Encoding.Default%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="57b9b-110"><xref:System.Text.Encoding.Default%2A?displayProperty=fullName>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="57b9b-111"><xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte little-endian.</xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="57b9b-111"><xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="57b9b-112"><xref:System.Text.Encoding.UTF32%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-32 usando a ordem de byte little-endian.</xref:System.Text.Encoding.UTF32%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="57b9b-112"><xref:System.Text.Encoding.UTF32%2A?displayProperty=fullName>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="57b9b-113"><xref:System.Text.Encoding.UTF7%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-7.</xref:System.Text.Encoding.UTF7%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="57b9b-113"><xref:System.Text.Encoding.UTF7%2A?displayProperty=fullName>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="57b9b-114"><xref:System.Text.Encoding.UTF8%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF-8.</xref:System.Text.Encoding.UTF8%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="57b9b-114"><xref:System.Text.Encoding.UTF8%2A?displayProperty=fullName>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57b9b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57b9b-115">See Also</span></span>  
 <span data-ttu-id="57b9b-116"><xref:System.Text.Encoding?displayProperty=fullName></xref:System.Text.Encoding?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="57b9b-116"><xref:System.Text.Encoding?displayProperty=fullName></span></span>   
 <span data-ttu-id="57b9b-117"><xref:System.Text.Encoding.GetString%2A></xref:System.Text.Encoding.GetString%2A></span><span class="sxs-lookup"><span data-stu-id="57b9b-117"><xref:System.Text.Encoding.GetString%2A></span></span>   
<span data-ttu-id="57b9b-118"> [Como: converter cadeias de caracteres em uma matriz de Bytes no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)</span><span class="sxs-lookup"><span data-stu-id="57b9b-118"> [How to: Convert Strings into an Array of Bytes in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)</span></span>
