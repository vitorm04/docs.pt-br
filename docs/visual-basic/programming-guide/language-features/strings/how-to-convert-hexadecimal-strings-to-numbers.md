---
title: 'Como: Converter cadeias de caracteres hexadecimais em números (Visual Basic)'
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: ddb7b39f7a47234c003ca16e1d7ea013e113c108
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480879"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="86651-102">Como: Converter cadeias de caracteres hexadecimais em números (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86651-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>

<span data-ttu-id="86651-103">Este exemplo converte uma cadeia de caracteres hexadecimal em um inteiro usando o <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="86651-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="86651-104">Para converter uma cadeia de caracteres hexadecimal em um número</span><span class="sxs-lookup"><span data-stu-id="86651-104">To convert a hexadecimal string to a number</span></span>

- <span data-ttu-id="86651-105">Use o <xref:System.Convert.ToInt32(System.String,System.Int32)> método para converter o número expressado na base 16 para um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="86651-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>

  <span data-ttu-id="86651-106">O primeiro argumento do <xref:System.Convert.ToInt32(System.String,System.Int32)> método é a cadeia de caracteres a ser convertido.</span><span class="sxs-lookup"><span data-stu-id="86651-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="86651-107">O segundo argumento descreve qual base o número é expresso em; hexadecimal é base 16.</span><span class="sxs-lookup"><span data-stu-id="86651-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- <span data-ttu-id="86651-108">Observe que a cadeia de caracteres hexadecimal tem as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="86651-108">Note that the hexadecimal string has the following restrictions:</span></span>

  - <span data-ttu-id="86651-109">Ele não pode incluir o `&h` prefixo.</span><span class="sxs-lookup"><span data-stu-id="86651-109">It cannot include the `&h` prefix.</span></span>
  - <span data-ttu-id="86651-110">Ele não pode incluir o `_` separador de dígitos.</span><span class="sxs-lookup"><span data-stu-id="86651-110">It cannot include the `_` digit separator.</span></span>

  <span data-ttu-id="86651-111">Se o prefixo ou um separador de dígitos estiver presente, a chamada para o <xref:System.Convert.ToInt32(System.String,System.Int32)> método lança um <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="86651-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="86651-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86651-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
