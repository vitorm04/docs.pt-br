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
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Como converter cadeias de caracteres hexadecimais em números (Visual Basic)

Este exemplo converte uma cadeia de caracteres hexadecimal em um inteiro usando o método <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>.

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Para converter uma cadeia de caracteres hexadecimal em um número

- Use o método <xref:System.Convert.ToInt32(System.String,System.Int32)> para converter o número expresso em base 16 em um inteiro.

  O primeiro argumento do método <xref:System.Convert.ToInt32(System.String,System.Int32)> é a cadeia de caracteres a ser convertida. O segundo argumento descreve em qual base o número é expresso; o hexadecimal é a base 16.

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- Observe que a cadeia de caracteres hexadecimal tem as seguintes restrições:

  - Ele não pode incluir o prefixo `&h`.
  - Ele não pode incluir o separador de dígito `_`.

  Se o prefixo ou um separador de dígitos estiver presente, a chamada para o método <xref:System.Convert.ToInt32(System.String,System.Int32)> lançará uma <xref:System.FormatException>.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
