---
title: "Como pesquisar cadeias de caracteres usando express&#245;es regulares (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "pesquisando cadeias de caracteres [C#]"
  - "cadeias de caracteres [c#], pesquisando com RegEx"
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como pesquisar cadeias de caracteres usando express&#245;es regulares (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A classe de <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> pode ser usada para cadeias de caracteres de pesquisa.  Essas pesquisas podem variar em complexidade de muito simples para fazer uso completo de expressões regulares.  Os seguintes são dois exemplos de cadeia de caracteres que eles pesquisam usando a classe de <xref:System.Text.RegularExpressions.Regex> .  Para obter mais informações, consulte [Expressões regulares do .NET Framework](../Topic/.NET%20Framework%20Regular%20Expressions.md).  
  
## Exemplo  
 O código a seguir é um aplicativo de console que executa uma pesquisa sem diferenciação de maiúsculas e minúsculas simples de cadeias de caracteres em uma matriz.  O <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=fullName> estática do método executa a pesquisa dada a cadeia de caracteres para a pesquisa e uma cadeia de caracteres que contém o padrão de pesquisa.  Nesse caso, um terceiro argumento é usado para indicar que os casos devem ser ignorados.  Para obter mais informações, consulte <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>.  
  
 [!code-cs[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## Exemplo  
 O código a seguir é um aplicativo de console que usa expressões regulares para validar o formato de cada cadeia de caracteres em uma matriz.  A validação requer que cada cadeia de caracteres assume a forma de um número de telefone em que três grupos de dígitos são separados por traços, os primeiros dois grupos contém três dígitos, e o terceiro grupo contém quatro dígitos.  Isso é feito usando a expressão regular `^\\d{3}-\\d{3}-\\d{4}$`.  Para obter mais informações, consulte [Linguagem de expressões regulares \- referência rápida](../Topic/Regular%20Expression%20Language%20-%20Quick%20Reference.md).  
  
 [!code-cs[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## Consulte também  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Cadeias de caracteres](../../../csharp/programming-guide/strings/index.md)   
 [Expressões regulares do .NET Framework](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [Linguagem de expressões regulares \- referência rápida](../Topic/Regular%20Expression%20Language%20-%20Quick%20Reference.md)