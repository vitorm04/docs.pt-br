---
title: 'Como: Converter uma matriz de Bytes em uma cadeia de caracteres no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: f0676548bea2d4037f66fb15498c175b2d110d8b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826724"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="f5cca-102">Como: Converter uma matriz de Bytes em uma cadeia de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f5cca-102">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>
<span data-ttu-id="f5cca-103">Este tópico mostra como converter os bytes de uma matriz de bytes em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f5cca-103">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5cca-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5cca-104">Example</span></span>  
 <span data-ttu-id="f5cca-105">Este exemplo usa o <xref:System.Text.Encoding.GetString%2A> método da <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> classe para converter todos os bytes de uma matriz de bytes em uma cadeia de caracteres de codificação.</span><span class="sxs-lookup"><span data-stu-id="f5cca-105">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 <span data-ttu-id="f5cca-106">Você pode escolher entre várias opções de codificação para converter uma matriz de bytes em uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="f5cca-106">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
-   <span data-ttu-id="f5cca-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Obtém uma codificação para o conjunto de caracteres ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="f5cca-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="f5cca-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte big-endian.</span><span class="sxs-lookup"><span data-stu-id="f5cca-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="f5cca-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Obtém uma codificação para a página de código ANSI atual do sistema.</span><span class="sxs-lookup"><span data-stu-id="f5cca-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="f5cca-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-16 usando a ordem de byte little-endian.</span><span class="sxs-lookup"><span data-stu-id="f5cca-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="f5cca-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-32 usando a ordem de byte little-endian.</span><span class="sxs-lookup"><span data-stu-id="f5cca-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="f5cca-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-7.</span><span class="sxs-lookup"><span data-stu-id="f5cca-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="f5cca-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Obtém uma codificação para o formato UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f5cca-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5cca-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5cca-114">See also</span></span>

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [<span data-ttu-id="f5cca-115">Como: Converter cadeias de caracteres em uma matriz de Bytes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f5cca-115">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
