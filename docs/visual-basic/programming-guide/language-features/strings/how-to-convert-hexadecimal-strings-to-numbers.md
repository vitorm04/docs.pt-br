---
title: Como converter cadeias de caracteres hexadecimais em números (Visual Basic)
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af0e6c1e30c116709ed98240de7bf3471fa842d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648636"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="b3250-102">Como converter cadeias de caracteres hexadecimais em números (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3250-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="b3250-103">Este exemplo converte uma cadeia de caracteres hexadecimal em um número inteiro usando o <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="b3250-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="b3250-104">Para converter uma cadeia de caracteres hexadecimal em um número</span><span class="sxs-lookup"><span data-stu-id="b3250-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="b3250-105">Use o <xref:System.Convert.ToInt32(System.String,System.Int32)> método para converter o número expressado na base-16 como um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="b3250-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="b3250-106">O primeiro argumento do <xref:System.Convert.ToInt32(System.String,System.Int32)> método é a cadeia de caracteres para converter.</span><span class="sxs-lookup"><span data-stu-id="b3250-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="b3250-107">O segundo argumento descreve qual base o número é expresso; hexadecimal é base 16.</span><span class="sxs-lookup"><span data-stu-id="b3250-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- <span data-ttu-id="b3250-108">Observe que a cadeia de caracteres hexadecimal tem as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="b3250-108">Note that the hexadecimal string has the following restrictions:</span></span>

   - <span data-ttu-id="b3250-109">Não é possível incluir o `&h` prefixo.</span><span class="sxs-lookup"><span data-stu-id="b3250-109">It cannot include the `&h` prefix.</span></span>
   - <span data-ttu-id="b3250-110">Não é possível incluir o `_` o separador de dígito.</span><span class="sxs-lookup"><span data-stu-id="b3250-110">It cannot include the `_` digit separator.</span></span>

   <span data-ttu-id="b3250-111">Se o prefixo ou um separador de dígito estiver presente, a chamada para o <xref:System.Convert.ToInt32(System.String,System.Int32)> método lança um <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="b3250-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3250-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3250-112">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
