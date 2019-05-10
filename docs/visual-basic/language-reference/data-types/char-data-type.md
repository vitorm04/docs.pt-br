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
ms.openlocfilehash: 6600b3b2945120f2f24e14d4cc898cd814366045
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647071"
---
# <a name="char-data-type-visual-basic"></a>Tipo de dados Char (Visual Basic)
Contém pontos de código de (2 bytes) de 16 bits sem sinal que variam de 0 a 65535. Cada *ponto de código*, ou código de caractere, representa um único caractere Unicode.  
  
## <a name="remarks"></a>Comentários  
 Use o `Char` tipo de dados quando você precisa manter um único caractere e não é necessário para a sobrecarga de `String`. Em alguns casos, você pode usar `Char()`, uma matriz de `Char` elementos, para manter vários caracteres.  
  
 O valor padrão de `Char` é o caractere com um ponto de código de 0.  
  
## <a name="unicode-characters"></a>Caracteres Unicode  
 Os primeiros pontos de 128 código (0 – 127) do Unicode correspondem às letras e símbolos de um teclado americano padrão. Esses primeiros 128 pontos de código são as mesmas que as define o conjunto de caracteres ASCII. Os 128 pontos de código (128 – 255) representam caracteres especiais, como letras do alfabeto baseado em latim, acentos, símbolos de moeda e frações. O Unicode usa os pontos de código restantes (256 a 65535) para uma ampla variedade de símbolos, incluindo símbolos técnicos e matemáticos, diacríticos e caracteres textuais em todo o mundo.  
  
 Você pode usar métodos como <xref:System.Char.IsDigit%2A> e <xref:System.Char.IsPunctuation%2A> em um `Char` variável para determinar sua classificação de Unicode.  
  
## <a name="type-conversions"></a>Conversões de tipo  
 O Visual Basic não converter diretamente entre `Char` e os tipos numéricos. Você pode usar o <xref:Microsoft.VisualBasic.Strings.Asc%2A> ou <xref:Microsoft.VisualBasic.Strings.AscW%2A> função para converter um `Char` de valor para um `Integer` que representa seu ponto de código. Você pode usar o <xref:Microsoft.VisualBasic.Strings.Chr%2A> ou <xref:Microsoft.VisualBasic.Strings.ChrW%2A> função para converter um `Integer` de valor para um `Char` que tem esse ponto de código.  
  
 Se a verificação de tipo muda ([instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)) está ativada, você deve acrescentar o caractere de tipo literal em uma cadeia de caracteres de caractere único literal para identificá-lo como o `Char` tipo de dados. O exemplo a seguir ilustra essa situação.  
  
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
  
- **Números negativos.** `Char` é um tipo sem sinal e não pode representar um valor negativo. Em qualquer caso, você não deve usar `Char` para armazenar valores numéricos.  
  
- **Considerações de interoperabilidade.** Se a interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, lembre-se de que tipos de caractere têm uma largura de dados diferente (8 bits) em outros ambientes. Se você passar um argumento de 8 bits para tal componente, declare-o como `Byte` em vez de `Char` no seu novo código do Visual Basic.  
  
- **Ampliação.** O `Char` tipo de dados é ampliado para `String`. Isso significa que você pode converter `Char` à `String` e não encontrará um <xref:System.OverflowException?displayProperty=nameWithType> erro.  
  
- **Caracteres de tipo.** Acrescentar o caractere de tipo literal `C` em uma cadeia de caracteres único literal o força ao `Char` tipo de dados. `Char` não tem nenhum caractere de tipo de identificador.  
  
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
