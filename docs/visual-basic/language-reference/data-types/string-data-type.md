---
title: "Tipo de dados da cadeia de caracteres (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.String"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "literais de String ""
  - "caractere de tipo identificador $"
  - "tipos de dados [Visual Basic], atribuindo"
  - "cadeias de caracteres de comprimento fixo"
  - "cadeias de caracteres de comprimento fixo, tipo de dados de cadeia de caracteres"
  - "caracteres de tipo identificador, $"
  - "literais, string"
  - "tipo de dados String"
  - "palavra-chave cadeia de caracteres [Visual Basic]"
  - "literais String"
  - "cadeias de caracteres {Visual Basic], caractere"
  - "cadeias de caracteres {Visual Basic], comprimento fixo"
  - "texto [Visual Basic], tipo de dados String"
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de dados da cadeia de caracteres (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Contém seqüências de pontos de código \(2 bytes\) de 16 bits não assinado que variam de 0 a 65535.  Cada  *código aponte*, ou o código de caractere, representa um único caractere Unicode.  Uma cadeia de caracteres pode conter de 0 a aproximadamente dois bilhões \(2 ^ 31\) de caracteres Unicode.  
  
## Comentários  
 Use o tipo de dados `String` para reter vários caracteres sem a sobrecarga de gerenciamento de matriz de `Char()`, uma matriz de elementos `Char`.  
  
 O valor padrão da `String` é `Nothing` \(uma referência nula\).  Observe que isso não é o mesmo que a cadeia de caracteres vazia \(valor `""`\).  
  
## Caracteres Unicode  
 Os primeiro 128 pontos de código \(0–127\) do Unicode correspondem às letras e símbolos em um padrão EUA  teclado.  Esses primeiros pontos de 128 código são as mesmas que as define de conjunto de caracteres ASCII.  Os 128 pontos de código seguintes \(128–255\) representam caracteres especiais, como letras do alfabeto baseadas no latim, acentos, símbolos de moeda e frações.  O Unicode usa os pontos de código restantes \(256\-65535\) para uma ampla variedade de símbolos.  Isso inclui caracteres textuais de todo o mundo, sinais diacríticos e símbolos matemáticos e técnicos.  
  
 Você pode usar métodos como <xref:System.Char.IsDigit%2A> e <xref:System.Char.IsPunctuation%2A> em um caractere individual em uma variável `String` para determinar sua classificação Unicode.  
  
## Requisitos de Formato  
 Você deve colocar uma `String` literal entre aspas \(`" "`\).  Se você deve incluir aspas como um dos caracteres na cadeia de caracteres, use duas aspas contíguas \(`""`\).  O exemplo a seguir ilustra isto:  
  
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
  
## Manipulações de cadeias de caracteres  
 Depois de atribuir uma cadeia de caracteres a uma variável `String`, essa cadeia de caracteres se torna *imutável*, o que significa que não é possível alterar seu comprimento ou conteúdo.  Quando você altera uma cadeia de caracteres de qualquer forma, o Visual Basic cria uma nova cadeia de caracteres e abandona a anterior.  A variável `String`, então, aponta para a nova cadeia de caracteres.  
  
 Você pode manipular o conteúdo de uma variável `String` usando uma variedade de funções de cadeia de caracteres.  O exemplo a seguir ilustra o <xref:Microsoft.VisualBasic.Strings.Left%2A> função  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Uma cadeia de caracteres criada por outro componente pode ser preenchida com espaços à direita ou à esquerda.  Se você receber uma seqüência de caracteres, você pode usar o <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, e <xref:Microsoft.VisualBasic.Strings.RTrim%2A> funções para remover esses espaços.  
  
 Para obter mais informações sobre manipulação de cadeias de caracteres, consulte [Cadeias de caracteres](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## Dicas de Programação  
  
-   **Números negativos.** Lembre\-se de que os caracteres mantido por `String` não estão assinadas e não pode representar valores negativos.  Em qualquer caso, você não deve usar `String` para armazenar valores numéricos.  
  
-   **Considerações de Interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, lembre\-se de que caracteres de cadeias de caracteres possuem uma largura de dados diferente \(8 bits\) em outros ambientes.  Se você estiver passando um argumento de cadeia de caracteres de 8 bits para tal componente, declare\-o como `Byte()`, uma matriz de elementos `Byte`, em vez de `String` no novo código Visual Basic.  
  
-   **Caracteres de Tipo.** Acrescentando o caractere de tipo de identificador `$` para qualquer identificador força\-o para o `String` tipo de dados.  `String`não tem nenhum caractere de tipo literal.  No entanto, o compilador trata literais entre aspas \(`" "`\) como `String`.  
  
-   **Tipo de Framework.** O tipo correspondente na.NET Framework é o <xref:System.String?displayProperty=fullName> classe.  
  
## Consulte também  
 <xref:System.String?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipo de dados Char](../../../visual-basic/language-reference/data-types/char-data-type.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Como chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)