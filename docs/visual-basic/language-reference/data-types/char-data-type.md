---
title: Tipo de dados (Visual Basic) char | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Char
dev_langs:
- VB
helpviewer_keywords:
- literal type characters, C
- Char data type
- C literal type character
- data types [Visual Basic], assigning
- Char data type, character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8f6d61c2bba25acc46a575ba4eec3e7177c47fc4
ms.lasthandoff: 03/13/2017

---
# <a name="char-data-type-visual-basic"></a>Tipo de dados Char (Visual Basic)
Armazena pontos de código de (2 bytes) de 16 bits sem sinal cujo valor varia de 0 a 65535. Cada *ponto de código*, ou código de caractere, representa um único caractere Unicode.  
  
## <a name="remarks"></a>Comentários  
 Use o `Char` de tipo de dados quando você precisa armazenar um único caractere e não é necessário para a sobrecarga de `String`. Em alguns casos, você pode usar `Char()`, uma matriz de `Char` elementos, para manter vários caracteres.  
  
 O valor padrão de `Char` é o caractere com um ponto de código de 0.  
  
## <a name="unicode-characters"></a>Caracteres Unicode  
 Os primeiro 128 pontos de código (0 – 127) do Unicode correspondem às letras e símbolos de um teclado americano padrão. Esses pontos de 128 código primeiro são as mesmas que as define o conjunto de caracteres ASCII. Os 128 pontos de código (128 – 255) representam caracteres especiais, como letras do alfabeto latino, acentos, símbolos monetários e frações. O Unicode usa os pontos de código restantes (256-65535) para uma ampla variedade de símbolos, incluindo caracteres textuais em todo o mundo, sinais diacríticos e símbolos matemáticos e técnicos.  
  
 Você pode usar métodos como <xref:System.Char.IsDigit%2A>e <xref:System.Char.IsPunctuation%2A>em um `Char` variável para determinar sua classificação Unicode.</xref:System.Char.IsPunctuation%2A> </xref:System.Char.IsDigit%2A>  
  
## <a name="type-conversions"></a>Conversões de tipo  
 O Visual Basic não converter diretamente entre `Char` e os tipos numéricos. Você pode usar o <xref:Microsoft.VisualBasic.Strings.Asc%2A>ou <xref:Microsoft.VisualBasic.Strings.AscW%2A>função para converter um `Char` valor para um `Integer` que representa seu ponto de código.</xref:Microsoft.VisualBasic.Strings.AscW%2A> </xref:Microsoft.VisualBasic.Strings.Asc%2A> Você pode usar o <xref:Microsoft.VisualBasic.Strings.Chr%2A>ou <xref:Microsoft.VisualBasic.Strings.ChrW%2A>função para converter um `Integer` valor para um `Char` que tem esse ponto de código.</xref:Microsoft.VisualBasic.Strings.ChrW%2A> </xref:Microsoft.VisualBasic.Strings.Chr%2A>  
  
 Se a verificação de tipo muda ([instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)) estiver ativado, você deve acrescentar o caractere de tipo literal em uma cadeia de único caractere literal para identificá-lo como o `Char` tipo de dados. O exemplo a seguir ilustra essa situação.  
  
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
  
-   **Números negativos.** `Char`é um tipo sem sinal e não pode representar um valor negativo. Em qualquer caso, você não deve usar `Char` para armazenar valores numéricos.  
  
-   **Considerações de interoperabilidade.** Interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, lembre-se de que tipos de caracteres uma largura de dados diferente (8 bits) em outros ambientes. Se você passar um argumento de 8 bits para tal um componente, declare-o como `Byte` em vez de `Char` em seu novo código Visual Basic.  
  
-   **Ampliação.** O `Char` tipo de dados amplia a `String`. Isso significa que você pode converter `Char` para `String` e não encontrará um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName>  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `C` para uma cadeia de caracteres único literal força-o `Char` tipo de dados. `Char`não tem nenhum caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é o <xref:System.Char?displayProperty=fullName>estrutura.</xref:System.Char?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Char?displayProperty=fullName></xref:System.Char?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Strings.Asc%2A></xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A></xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A></xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipo de dados String](../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Como: chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
