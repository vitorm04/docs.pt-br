---
title: Como converter cadeias de caracteres hexadecimais em números
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: f0a97a0c212a64bfa4db4606ee526b666f07877a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347166"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="655d0-102">Como converter cadeias de caracteres hexadecimais em números (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="655d0-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>

<span data-ttu-id="655d0-103">Este exemplo converte uma cadeia de caracteres hexadecimal em um inteiro usando o método <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="655d0-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="655d0-104">Para converter uma cadeia de caracteres hexadecimal em um número</span><span class="sxs-lookup"><span data-stu-id="655d0-104">To convert a hexadecimal string to a number</span></span>

- <span data-ttu-id="655d0-105">Use o método <xref:System.Convert.ToInt32(System.String,System.Int32)> para converter o número expresso em base 16 em um inteiro.</span><span class="sxs-lookup"><span data-stu-id="655d0-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>

  <span data-ttu-id="655d0-106">O primeiro argumento do método <xref:System.Convert.ToInt32(System.String,System.Int32)> é a cadeia de caracteres a ser convertida.</span><span class="sxs-lookup"><span data-stu-id="655d0-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="655d0-107">O segundo argumento descreve em qual base o número é expresso; o hexadecimal é a base 16.</span><span class="sxs-lookup"><span data-stu-id="655d0-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- <span data-ttu-id="655d0-108">Observe que a cadeia de caracteres hexadecimal tem as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="655d0-108">Note that the hexadecimal string has the following restrictions:</span></span>

  - <span data-ttu-id="655d0-109">Ele não pode incluir o prefixo `&h`.</span><span class="sxs-lookup"><span data-stu-id="655d0-109">It cannot include the `&h` prefix.</span></span>
  - <span data-ttu-id="655d0-110">Ele não pode incluir o separador de dígito `_`.</span><span class="sxs-lookup"><span data-stu-id="655d0-110">It cannot include the `_` digit separator.</span></span>

  <span data-ttu-id="655d0-111">Se o prefixo ou um separador de dígitos estiver presente, a chamada para o método <xref:System.Convert.ToInt32(System.String,System.Int32)> lançará uma <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="655d0-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="655d0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="655d0-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
