---
title: Tipo de dados (Visual Basic) de cadeia de caracteres | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.String
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings, string data type
- literals, string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals
- data types [Visual Basic], assigning
- String literals
- identifier type characters, $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
caps.latest.revision: 19
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
ms.openlocfilehash: 9221a89a1fb46609b4b8550968e3a2bbe874772c
ms.lasthandoff: 03/13/2017

---
# <a name="string-data-type-visual-basic"></a>Tipo de dados da cadeia de caracteres (Visual Basic)
Contém sequências de pontos de código de (2 bytes) de 16 bits sem sinal que variam em valor de 0 a 65535. Cada *ponto de código*, ou código de caractere, representa um único caractere Unicode. Uma cadeia de caracteres pode conter de 0 a aproximadamente dois bilhões (2 ^ 31) caracteres Unicode.  
  
## <a name="remarks"></a>Comentários  
 Use o `String` tipo de dados para reter vários caracteres sem a sobrecarga de gerenciamento de matriz de `Char()`, uma matriz de `Char` elementos.  
  
 O valor padrão de `String` é `Nothing` (uma referência nula). Observe que isso não é a mesma cadeia de caracteres vazia (valor `""`).  
  
## <a name="unicode-characters"></a>Caracteres Unicode  
 Os primeiro 128 pontos de código (0 – 127) do Unicode correspondem às letras e símbolos de um teclado americano padrão. Esses pontos de 128 código primeiro são as mesmas que as define o conjunto de caracteres ASCII. Os 128 pontos de código (128 – 255) representam caracteres especiais, como letras do alfabeto latino, acentos, símbolos monetários e frações. O Unicode usa os pontos de código restantes (256-65535) para uma ampla variedade de símbolos. Isso inclui caracteres textuais em todo o mundo, sinais diacríticos e símbolos matemáticos e técnicos.  
  
 Você pode usar métodos como <xref:System.Char.IsDigit%2A>e <xref:System.Char.IsPunctuation%2A>em um caractere individual em uma `String` variável para determinar sua classificação Unicode.</xref:System.Char.IsPunctuation%2A> </xref:System.Char.IsDigit%2A>  
  
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
  
 Observe que as aspas contíguas que representam as aspas na cadeia de caracteres são independentes das aspas que começam e terminam a `String` literal.  
  
## <a name="string-manipulations"></a>Manipulações de cadeia de caracteres  
 Depois de atribuir uma cadeia de caracteres para um `String` variável, essa cadeia de caracteres é *imutável*, que significa que você não pode alterar seu comprimento ou conteúdo. Quando você altera uma cadeia de caracteres de qualquer forma, o Visual Basic cria uma nova cadeia de caracteres e abandona a anterior. O `String` variável aponta para a nova cadeia de caracteres.  
  
 Você pode manipular o conteúdo de um `String` variável usando uma variedade de funções de cadeia de caracteres. O exemplo a seguir ilustra a <xref:Microsoft.VisualBasic.Strings.Left%2A>função</xref:Microsoft.VisualBasic.Strings.Left%2A>  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Uma cadeia de caracteres criada por outro componente pode ser preenchida com espaços iniciais ou finais. Se você receber uma cadeia de caracteres, você pode usar o <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, e <xref:Microsoft.VisualBasic.Strings.RTrim%2A>funções para remover esses espaços.</xref:Microsoft.VisualBasic.Strings.RTrim%2A> </xref:Microsoft.VisualBasic.Strings.LTrim%2A> </xref:Microsoft.VisualBasic.Strings.Trim%2A>  
  
 Para obter mais informações sobre como manipular cadeias de caracteres, consulte [cadeias de caracteres](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Números negativos.** Lembre-se de que os caracteres mantidos pela `String` não são assinados e não pode representar valores negativos. Em qualquer caso, você não deve usar `String` para armazenar valores numéricos.  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, lembre-se de que caracteres de cadeia de caracteres possuem uma largura de dados diferente (8 bits) em outros ambientes. Se você estiver passando um argumento de cadeia de caracteres de 8 bits para tal um componente, declare-o como `Byte()`, uma matriz de `Byte` elementos, em vez de `String` em seu novo código Visual Basic.  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo identificador `$` a qualquer identificador o força ao `String` tipo de dados. `String`não tem nenhum caractere de tipo literal. No entanto, o compilador trata literais entre aspas (`" "`) como `String`.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a <xref:System.String?displayProperty=fullName>classe.</xref:System.String?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.String?displayProperty=fullName></xref:System.String?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipo de dados char](../../../visual-basic/language-reference/data-types/char-data-type.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Como: chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

