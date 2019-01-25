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
ms.openlocfilehash: 76acee8913df35d4d071017078b38a3c474c3357
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633799"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Como: Converter cadeias de caracteres hexadecimais em números (Visual Basic)
Este exemplo converte uma cadeia de caracteres hexadecimal em um inteiro usando o <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> método.  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Para converter uma cadeia de caracteres hexadecimal em um número  
  
-   Use o <xref:System.Convert.ToInt32(System.String,System.Int32)> método para converter o número expressado na base 16 para um número inteiro.  
  
     O primeiro argumento do <xref:System.Convert.ToInt32(System.String,System.Int32)> método é a cadeia de caracteres a ser convertido. O segundo argumento descreve qual base o número é expresso em; hexadecimal é base 16.  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- Observe que a cadeia de caracteres hexadecimal tem as seguintes restrições:

   - Ele não pode incluir o `&h` prefixo.
   - Ele não pode incluir o `_` separador de dígitos.

   Se o prefixo ou um separador de dígitos estiver presente, a chamada para o <xref:System.Convert.ToInt32(System.String,System.Int32)> método lança um <xref:System.FormatException>.

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
