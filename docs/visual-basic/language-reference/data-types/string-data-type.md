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
ms.openlocfilehash: 6d2fd226735622de5cd7197060c05b8ac12b69f1
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696837"
---
# <a name="string-data-type-visual-basic"></a>Tipo de dados da cadeia de caracteres (Visual Basic)
Retém sequências de pontos de código não assinados de 16 bits (2 bytes) que variam em valor de 0 a 65535. Cada *ponto de código*, ou código de caractere, representa um único caractere Unicode. Uma cadeia de caracteres pode conter de 0 a aproximadamente 2.000.000.000 (2 ^ 31) caracteres Unicode.  
  
## <a name="remarks"></a>Comentários  
 Use o tipo de dados `String` para conter vários caracteres sem a sobrecarga de gerenciamento de matriz de `Char()`, uma matriz de elementos `Char`.  
  
 O valor padrão de `String` é `Nothing` (uma referência nula). Observe que isso não é o mesmo que a cadeia de caracteres vazia (valor `""`).  
  
## <a name="unicode-characters"></a>Caracteres Unicode  
 Os primeiros 128 pontos de código (0 – 127) de Unicode correspondem às letras e aos símbolos em um teclado americano padrão. Esses primeiros 128 pontos de código são os mesmos que os conjuntos de caracteres ASCII define. Os segundos pontos de código 128 (128 – 255) representam caracteres especiais, como letras do alfabeto, acentos, símbolos de moeda e frações baseados em latim. O Unicode usa os pontos de código restantes (256-65535) para uma grande variedade de símbolos. Isso inclui caracteres de texto em todo o mundo, sinais diacríticos e símbolos técnicos e matemáticos.  
  
 Você pode usar métodos como <xref:System.Char.IsDigit%2A> e <xref:System.Char.IsPunctuation%2A> em um caractere individual em uma variável `String` para determinar sua classificação Unicode.  
  
## <a name="format-requirements"></a>Requisitos de formato  
 Você deve colocar um literal `String` entre aspas (`" "`). Se você precisar incluir uma aspa como um dos caracteres na cadeia de caracteres, use duas aspas contíguas (`""`). O exemplo a seguir ilustra essa situação.  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Observe que as aspas contíguas que representam uma aspa na cadeia de caracteres são independentes das aspas que começam e terminam o literal `String`.  
  
## <a name="string-manipulations"></a>Manipulações de cadeia de caracteres  
 Depois de atribuir uma cadeia de caracteres a uma variável `String`, essa cadeia de caracteres é *imutável*, o que significa que você não pode alterar seu comprimento ou conteúdo. Quando você altera uma cadeia de caracteres de qualquer forma, Visual Basic cria uma nova cadeia de caracteres e abandona a anterior. A variável `String`, em seguida, aponta para a nova cadeia de caracteres.  
  
 Você pode manipular o conteúdo de uma variável `String` usando uma variedade de funções de cadeia de caracteres. O exemplo a seguir ilustra a função <xref:Microsoft.VisualBasic.Strings.Left%2A>  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Uma cadeia de caracteres criada por outro componente pode ser preenchida com espaços à esquerda ou à direita. Se você receber essa cadeia de caracteres, poderá usar as funções <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A> e <xref:Microsoft.VisualBasic.Strings.RTrim%2A> para remover esses espaços.  
  
 Para obter mais informações sobre manipulações de cadeias de caracteres, consulte [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Dicas de programação  
  
- **Números negativos.** Lembre-se de que os caracteres mantidos por `String` não são assinados e não podem representar valores negativos. Em qualquer caso, você não deve usar `String` para armazenar valores numéricos.  
  
- **Considerações sobre interoperabilidade.** Se você estiver fazendo a interface com componentes não escritos para o .NET Framework, por exemplo, automação ou objetos COM, lembre-se de que os caracteres da cadeia de caracteres têm uma largura de dados diferente (8 bits) em outros ambientes. Se você estiver passando um argumento de cadeia de caracteres de 8 bits para esse componente, declare-o como `Byte()`, uma matriz de elementos `Byte`, em vez de `String` em seu novo código de Visual Basic.  
  
- **Digite os caracteres.** Acrescentar o caractere de tipo de identificador `$` a qualquer identificador força-o para o tipo de dados `String`. `String` não tem nenhum caractere de tipo literal. No entanto, o compilador trata literais delimitados entre aspas (`" "`) como `String`.  
  
- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a classe <xref:System.String?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.String?displayProperty=nameWithType>
- [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)
- [Tipo de Dados de Caractere](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Como: chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
