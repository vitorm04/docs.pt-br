---
title: Como converter cadeias de caracteres em uma matriz de bytes
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: 76fde3120ce629ce32f29ca28d90eba24fff726c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351965"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a><span data-ttu-id="984c7-102">Como converter cadeias de caracteres em uma matriz de bytes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="984c7-102">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>
<span data-ttu-id="984c7-103">Este tópico mostra como converter uma cadeia de caracteres em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="984c7-103">This topic shows how to convert a string into an array of bytes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="984c7-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="984c7-104">Example</span></span>  
 <span data-ttu-id="984c7-105">Este exemplo usa o método <xref:System.Text.Encoding.GetBytes%2A> da classe de codificação <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> para converter uma cadeia de caracteres em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="984c7-105">This example uses the <xref:System.Text.Encoding.GetBytes%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert a string into an array of bytes.</span></span>  
  
 [!code-vb[VbVbalrStrings#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#74)]  
  
 <span data-ttu-id="984c7-106">Você pode escolher entre várias opções de codificação para converter uma cadeia de caracteres em uma matriz de bytes:</span><span class="sxs-lookup"><span data-stu-id="984c7-106">You can choose from several encoding options to convert a string into a byte array:</span></span>  
  
- <span data-ttu-id="984c7-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Obtém uma codificação para o conjunto de caracteres ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="984c7-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
- <span data-ttu-id="984c7-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-16 usando a ordem de bytes big-endian.</span><span class="sxs-lookup"><span data-stu-id="984c7-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
- <span data-ttu-id="984c7-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Obtém uma codificação para a página de código ANSI atual do sistema.</span><span class="sxs-lookup"><span data-stu-id="984c7-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
- <span data-ttu-id="984c7-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte little-endian.</span><span class="sxs-lookup"><span data-stu-id="984c7-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="984c7-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-32 usando a ordem de byte little-endian.</span><span class="sxs-lookup"><span data-stu-id="984c7-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="984c7-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-7.</span><span class="sxs-lookup"><span data-stu-id="984c7-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
- <span data-ttu-id="984c7-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-8.</span><span class="sxs-lookup"><span data-stu-id="984c7-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="984c7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="984c7-114">See also</span></span>

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [<span data-ttu-id="984c7-115">Como converter uma matriz de bytes em uma cadeia de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="984c7-115">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
