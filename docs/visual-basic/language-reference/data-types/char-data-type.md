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
ms.openlocfilehash: 8313c2282a3b4b7b035f9f3b685a786c4471f53a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630146"
---
# <a name="char-data-type-visual-basic"></a>Tipo de dados Char (Visual Basic)

Contém pontos de código não assinados de 16 bits (2 bytes) que variam em valor de 0 a 65535. Cada *ponto de código*, ou código de caractere, representa um único caractere Unicode.

## <a name="remarks"></a>Comentários

Use o `Char` tipo de dados quando precisar manter apenas um único caractere e não precisar da sobrecarga de. `String` Em alguns casos, você pode `Char()`usar uma matriz de `Char` elementos para conter vários caracteres.

O valor padrão de `Char` é o caractere com um ponto de código de 0.

## <a name="unicode-characters"></a>Caracteres Unicode

Os primeiros 128 pontos de código (0 – 127) de Unicode correspondem às letras e aos símbolos em um teclado americano padrão. Esses primeiros 128 pontos de código são os mesmos que os conjuntos de caracteres ASCII define. Os segundos pontos de código 128 (128 – 255) representam caracteres especiais, como letras do alfabeto, acentos, símbolos de moeda e frações baseados em latim. O Unicode usa os pontos de código restantes (256-65535) para uma grande variedade de símbolos, incluindo caracteres de texto em todo o mundo, sinais diacríticos e símbolos matemáticos e técnicos.

Você pode usar métodos como <xref:System.Char.IsDigit%2A> e <xref:System.Char.IsPunctuation%2A> em uma `Char` variável para determinar sua classificação Unicode.

## <a name="type-conversions"></a>Conversões de tipo

Visual Basic não converte diretamente entre `Char` e os tipos numéricos. Você pode usar a <xref:Microsoft.VisualBasic.Strings.Asc%2A> função <xref:Microsoft.VisualBasic.Strings.AscW%2A> ou para converter um `Char` valor em um `Integer` que representa seu ponto de código. Você pode usar a <xref:Microsoft.VisualBasic.Strings.Chr%2A> função <xref:Microsoft.VisualBasic.Strings.ChrW%2A> ou para converter um `Integer` valor em um `Char` que tenha esse ponto de código.

Se a opção de verificação de tipo (a [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)) estiver on, você deverá acrescentar o caractere de tipo literal a um literal de cadeia de caracteres de caractere `Char` único para identificá-lo como o tipo de dados. O exemplo a seguir ilustra essa situação. A primeira atribuição para a `charVar` variável gera o erro [BC30512](../../misc/bc30512.md) do `Option Strict` compilador porque está ativada. O segundo é compilado com êxito porque o caractere `c` de tipo literal identifica o literal como um `Char` valor.

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a>Dicas de programação

- **Números negativos.** `Char`é um tipo não assinado e não pode representar um valor negativo. Em qualquer caso, você não deve usar `Char` para armazenar valores numéricos.

- **Considerações sobre interoperabilidade.** Se você interface com componentes não escritos para o .NET Framework, por exemplo, automação ou objetos COM, lembre-se de que os tipos de caracteres têm uma largura de dados diferente (8 bits) em outros ambientes. Se você passar um argumento de 8 bits para esse componente, declare-o como `Byte` em vez `Char` de em seu novo código de Visual Basic.

- **Ampliação.** O `Char` tipo de dados amplia para `String`. Isso significa que você pode `Char` Converter `String` em e não encontrará <xref:System.OverflowException?displayProperty=nameWithType>um.

- **Digite os caracteres.** Acrescentar o caractere `C` de tipo literal a um literal de cadeia de caracteres de caractere único força `Char` -o para o tipo de dados. `Char`Não tem um caractere de tipo de identificador.

- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Char?displayProperty=nameWithType>.

## <a name="see-also"></a>Consulte também

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)
- [Tipo de Dados String](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Como: chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
