---
title: "Tipo de dados Char (Visual Basic) | Microsoft Docs"
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
  - "vb.Char"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "caractere de tipo literal C"
  - "tipo de dados Char"
  - "tipo de dados Char, literais de caracteres"
  - "tipos de dados [Visual Basic], atribuindo"
  - "caracteres de tipo literal, C"
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de dados Char (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Pontos de código \(2 bytes\) de 16 bits não assinado de suspensões cujo valor varia de 0 a 65535.  Cada  *código aponte*, ou o código de caractere, representa um único caractere Unicode.  
  
## Comentários  
 Use o `Char` quando você precisa manter um único tipo de dados de caracteres e não precisa a sobrecarga de `String`.  Em alguns casos, você pode usar `Char()`, uma matriz de `Char` elementos, para manter vários caracteres.  
  
 O valor padrão de `Char` é o caractere com um ponto de código 0.  
  
## Caracteres Unicode  
 Os primeiro 128 pontos de código \(0–127\) do Unicode correspondem às letras e símbolos em um padrão EUA  teclado.  Esses primeiros pontos de 128 código são as mesmas que as define de conjunto de caracteres ASCII.  Os 128 pontos de código seguintes \(128–255\) representam caracteres especiais, como letras do alfabeto baseadas no latim, acentos, símbolos de moeda e frações.  Unicode usa os pontos de código \(256\-65535\) restantes para uma ampla variedade de símbolos, incluindo símbolos matemáticos e técnicos, diacríticos e caracteres textuais em todo o mundo.  
  
 Você pode usar métodos como <xref:System.Char.IsDigit%2A> e <xref:System.Char.IsPunctuation%2A> em um `Char` variável para determinar sua classificação de Unicode.  
  
## Conversão de Tipos  
 Visual Basic não converte diretamente entre `Char` e os tipos numéricos.  Você pode usar o <xref:Microsoft.VisualBasic.Strings.Asc%2A> ou <xref:Microsoft.VisualBasic.Strings.AscW%2A> função para converter um `Char` valor para um `Integer` que representa o seu ponto de código.  Você pode usar o <xref:Microsoft.VisualBasic.Strings.Chr%2A> ou <xref:Microsoft.VisualBasic.Strings.ChrW%2A> função para converter um `Integer` valor para um `Char` que tem esse ponto de código.  
  
 Se o tipo de verificação Alternar \([Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)\) está ativada, você deve acrescentar o caractere de tipo literal em uma seqüência de caractere único literal para identificá\-lo como o `Char` tipo de dados.  O exemplo a seguir ilustra isto:  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## Dicas de Programação  
  
-   **Negativos números.** `Char` é um tipo não assinado e não pode representar um valor negativo.  Em qualquer caso, você não deve usar `Char` para armazenar valores numéricos.  
  
-   **Considerações de Interoperabilidade.** Se você interface com componentes não escritos para o.NET Framework, por exemplo automação ou COM objetos, lembre\-se de que tipos de caracteres tem uma largura de dados diferentes \(8 bits\) em outros ambientes.  Se você passar um argumento de 8 bits para tal componente, declará\-lo como `Byte` em vez de `Char` em seu novo código de Visual Basic.  
  
-   **Tipos de dados.** O `Char` tipo de dados amplia a `String`.  Isso significa que você pode converter `Char` para `String` e não encontrarão uma <xref:System.OverflowException?displayProperty=fullName> erro.  
  
-   **Caracteres de Tipo.** Acrescentando o caractere de tipo literal `C` para uma seqüência de caractere único literal força\-o para o `Char` tipo de dados.  `Char`não tem nenhum caractere de tipo de identificador.  
  
-   **Tipo de Framework.** O tipo correspondente na.NET Framework é o <xref:System.Char?displayProperty=fullName> estrutura.  
  
## Consulte também  
 <xref:System.Char?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipo de dados da cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Como chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)