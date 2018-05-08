---
title: Tipo de dados da cadeia de caracteres (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: 894638bbe50dad2cae1f74a2f7b7fe006f029d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="string-data-type-visual-basic"></a>Tipo de dados da cadeia de caracteres (Visual Basic)
Contém sequências de pontos de código de (2 bytes) de 16 bits sem sinal que variam de 0 a 65535. Cada *ponto de código*, ou código de caractere, representa um único caractere Unicode. Uma cadeia de caracteres pode conter de 0 a aproximadamente dois bilhões (2 ^ 31) caracteres Unicode.  
  
## <a name="remarks"></a>Comentários  
 Use o `String` tipo de dados para manter vários caracteres sem a sobrecarga de gerenciamento de matriz de `Char()`, uma matriz de `Char` elementos.  
  
 O valor padrão de `String` é `Nothing` (uma referência nula). Observe que isso não é o mesmo que a cadeia de caracteres vazia (valor `""`).  
  
## <a name="unicode-characters"></a>Caracteres Unicode  
 Os primeiro 128 pontos de código (0 – 127) do Unicode correspondem às letras e símbolos de um teclado americano padrão. Esses pontos de 128 código primeira são os mesmos define o conjunto de caracteres ASCII. Os segundo 128 pontos de código (128 – 255) representam caracteres especiais, como letras do alfabeto latino, acentos, símbolos de moeda e frações. O Unicode usa os pontos de código restantes (256-65535) para uma ampla variedade de símbolos. Isso inclui caracteres textuais em todo o mundo, sinais diacríticos e símbolos matemáticos e técnicos.  
  
 Você pode usar métodos como <xref:System.Char.IsDigit%2A> e <xref:System.Char.IsPunctuation%2A> em um caractere individual em um `String` variável para determinar sua classificação Unicode.  
  
## <a name="format-requirements"></a>Requisitos de formato  
 Você deve colocar um `String` literal entre aspas (`" "`). Se você deve incluir aspas como um dos caracteres na cadeia de caracteres, você use duas aspas contíguas (`""`). O exemplo a seguir ilustra essa situação.  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Observe que as aspas contíguas que representam as aspas na cadeia de caracteres são independentes das aspas que começam e terminam o `String` literal.  
  
## <a name="string-manipulations"></a>Manipulações de cadeia de caracteres  
 Depois de atribuir uma cadeia de caracteres para um `String` variável, essa cadeia de caracteres é *imutável*, que significa que você não pode alterar seu comprimento ou conteúdo. Quando você altera uma cadeia de caracteres de qualquer forma, o Visual Basic cria uma nova cadeia de caracteres e abandona a anterior. O `String` variável aponta para a nova cadeia de caracteres.  
  
 Você pode manipular o conteúdo de um `String` variável usando uma variedade de funções de cadeia de caracteres. O exemplo a seguir ilustra o <xref:Microsoft.VisualBasic.Strings.Left%2A> função  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Uma cadeia de caracteres criada por outro componente pode ser preenchida com espaços à direita ou. Se você receber uma cadeia de caracteres, você pode usar o <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, e <xref:Microsoft.VisualBasic.Strings.RTrim%2A> funções para remover esses espaços.  
  
 Para obter mais informações sobre a manipulação de cadeia de caracteres, consulte [cadeias de caracteres](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Números negativos.** Lembre-se de que os caracteres mantidos por `String` não são assinados e não pode representar valores negativos. Em qualquer caso, você não deve usar `String` para armazenar valores numéricos.  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, lembre-se de que os caracteres de cadeia de caracteres têm uma largura de dados diferente (8 bits) em outros ambientes. Se você estiver passando um argumento de cadeia de caracteres de 8 bits para tal componente, declare-o como `Byte()`, uma matriz de `Byte` elementos, em vez de `String` no seu novo código do Visual Basic.  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo identificador `$` a qualquer identificador força-o `String` tipo de dados. `String` não tem nenhum caractere de tipo literal. No entanto, o compilador trata literais entre aspas (`" "`) como `String`.  
  
-   **Tipo de estrutura.** O tipo correspondente do .NET Framework é o <xref:System.String?displayProperty=nameWithType> classe.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.String?displayProperty=nameWithType>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tipo de Dados de Caractere](../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Como chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
