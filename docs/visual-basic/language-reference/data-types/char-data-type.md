---
title: Tipo de dados Char (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: e672402535215ca30d19cc480e39b42b0364f137
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="char-data-type-visual-basic"></a>Tipo de dados Char (Visual Basic)
Armazena pontos de código de (2 bytes) de 16 bits sem sinal que variam de 0 a 65535. Cada *ponto de código*, ou código de caractere, representa um único caractere Unicode.  
  
## <a name="remarks"></a>Comentários  
 Use o `Char` quando você precisa manter um único tipo de dados de caracteres e não precisa da sobrecarga do `String`. Em alguns casos, você pode usar `Char()`, uma matriz de `Char` elementos, para manter vários caracteres.  
  
 O valor padrão de `Char` é o caractere com um ponto de código de 0.  
  
## <a name="unicode-characters"></a>Caracteres Unicode  
 Os primeiro 128 pontos de código (0 – 127) do Unicode correspondem às letras e símbolos de um teclado americano padrão. Esses pontos de 128 código primeira são os mesmos define o conjunto de caracteres ASCII. Os segundo 128 pontos de código (128 – 255) representam caracteres especiais, como letras do alfabeto latino, acentos, símbolos de moeda e frações. O Unicode usa os pontos de código restantes (256-65535) para uma ampla variedade de símbolos, incluindo caracteres de textuais em todo o mundo, sinais diacríticos e símbolos matemáticos e técnicos.  
  
 Você pode usar métodos como <xref:System.Char.IsDigit%2A> e <xref:System.Char.IsPunctuation%2A> em um `Char` variável para determinar sua classificação Unicode.  
  
## <a name="type-conversions"></a>Conversões de tipo  
 Visual Basic não converter diretamente entre `Char` e os tipos numéricos. Você pode usar o <xref:Microsoft.VisualBasic.Strings.Asc%2A> ou <xref:Microsoft.VisualBasic.Strings.AscW%2A> function para converter um `Char` valor para um `Integer` que representa o ponto de código. Você pode usar o <xref:Microsoft.VisualBasic.Strings.Chr%2A> ou <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function para converter um `Integer` valor para um `Char` com esse ponto de código.  
  
 Se a verificação de tipo muda ([instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)) está ativada, você deve acrescentar o caractere de tipo literal em uma cadeia de caracteres de único caractere literal para identificá-lo como o `Char` tipo de dados. O exemplo a seguir ilustra essa situação.  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Números negativos.** `Char` é um tipo não assinado e não pode representar um valor negativo. Em qualquer caso, você não deve usar `Char` para armazenar valores numéricos.  
  
-   **Considerações de interoperabilidade.** Interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, lembre-se de que tipos de caracteres uma largura de dados diferente (8 bits) em outros ambientes. Se você passar um argumento de 8 bits para tal componente, declare-o como `Byte` em vez de `Char` no seu novo código do Visual Basic.  
  
-   **Ampliação.** O `Char` tipo de dados amplia a `String`. Isso significa que você pode converter `Char` para `String` e não encontrará um <xref:System.OverflowException?displayProperty=nameWithType> erro.  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `C` para uma cadeia de único caractere literal força-o `Char` tipo de dados. `Char` não tem nenhum caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Char?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Char?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tipo de Dados String](../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Como chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
