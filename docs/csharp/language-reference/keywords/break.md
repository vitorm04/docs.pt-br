---
title: "break (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "break"
  - "break_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave break [C#]"
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# break (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A declaração de `break` finaliza o mais próximo loop ou instrução incluindo de [alterne](../../../csharp/language-reference/keywords/switch.md) no qual ele aparece.  O controle é passado para a declaração que segue a declaração finalizada, se houver.  
  
## Exemplo  
 Em esse exemplo, a declaração condicional contém um contador suponha que é para contar 1 a 100; no entanto, a instrução de `break` finaliza o loop após 4 pontuações.  
  
 [!code-cs[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]  
  
## Exemplo  
 Em esse exemplo, a instrução de `break` é usada para quebrar de um loop aninhado interno, e retorna o controle para o loop mais externo.  
  
 [!code-cs[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]  
  
## Exemplo  
 este exemplo demonstra o uso de `break` em uma instrução de [alterne](../../../csharp/language-reference/keywords/switch.md) .  
  
 [!code-cs[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]  
  
 Se você inseriu em `4`, a saída é:  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [switch](../../../csharp/language-reference/keywords/switch.md)   
 [Instruções de salto](../../../csharp/language-reference/keywords/jump-statements.md)   
 [Instruções de iteração](../../../csharp/language-reference/keywords/iteration-statements.md)