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
ms.locfileid: "33647947"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a><span data-ttu-id="ee73b-102">Como converter cadeias de caracteres em uma matriz de bytes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee73b-102">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>
<span data-ttu-id="ee73b-103">Este tópico mostra como converter uma cadeia de caracteres em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="ee73b-103">This topic shows how to convert a string into an array of bytes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee73b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ee73b-104">Example</span></span>  
 <span data-ttu-id="ee73b-105">Este exemplo usa o <xref:System.Text.Encoding.GetBytes%2A> método o <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> codificação classe para converter uma cadeia de caracteres em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="ee73b-105">This example uses the <xref:System.Text.Encoding.GetBytes%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert a string into an array of bytes.</span></span>  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 <span data-ttu-id="ee73b-106">Você pode escolher entre várias opções de codificação para converter uma cadeia de caracteres em uma matriz de bytes:</span><span class="sxs-lookup"><span data-stu-id="ee73b-106">You can choose from several encoding options to convert a string into a byte array:</span></span>  
  
-   <span data-ttu-id="ee73b-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Obtém uma codificação de caracteres ASCII (7 bits) do conjunto.</span><span class="sxs-lookup"><span data-stu-id="ee73b-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="ee73b-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte big-endian.</span><span class="sxs-lookup"><span data-stu-id="ee73b-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="ee73b-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Obtém uma codificação para a página de código ANSI atual do sistema.</span><span class="sxs-lookup"><span data-stu-id="ee73b-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="ee73b-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte little-endian.</span><span class="sxs-lookup"><span data-stu-id="ee73b-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="ee73b-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-32 usando a ordem de byte little-endian.</span><span class="sxs-lookup"><span data-stu-id="ee73b-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="ee73b-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-7.</span><span class="sxs-lookup"><span data-stu-id="ee73b-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="ee73b-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ee73b-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee73b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee73b-114">See Also</span></span>  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetBytes%2A>  
 [<span data-ttu-id="ee73b-115">Como: converter uma matriz de Bytes em uma cadeia de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee73b-115">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
