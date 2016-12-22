---
title: "do (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "do_CSharpKeyword"
  - "do"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave [C#]"
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# do (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `do` instrução executa uma instrução ou um bloco de instruções repetidamente até que uma expressão especificada for avaliada como `false`.  O corpo do loop deve ser colocado entre chaves, `{}`, a menos que consiste em uma única instrução.  Nesse caso, as chaves são opcionais.  
  
## Exemplo  
 No exemplo a seguir, o `do-while` instruções de loop executadas desde que a variável `x` for menor que 5.  
  
 [!code-cs[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 Ao contrário do  [enquanto](../../../csharp/language-reference/keywords/while.md) declaração, uma `do-while` loop é executado uma vez antes que a expressão condicional for avaliada.  
  
 Em qualquer point\-in a `do-while` bloco, você pode quebrar fora do loop usando o  [quebra](../../../csharp/language-reference/keywords/break.md) instrução.  Você pode entrar diretamente para o `while` instrução de avaliação de expressão usando o  [continuar](../../../csharp/language-reference/keywords/continue.md) instrução.  Se a `while` expressão for avaliada como true, a execução continua na primeira instrução no loop.  Se a expressão for avaliada como false, a execução continua na primeira instrução após a `do-while` loop.  
  
 A `do-while` loop também pode ser encerrado pela  [goto](../../../csharp/language-reference/keywords/goto.md),  [retornar](../../../csharp/language-reference/keywords/return.md), ou  [lança](../../../csharp/language-reference/keywords/throw.md) instruções.  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Instrução do\-while \(C\+\+\)](/visual-cpp/cpp/do-while-statement-cpp)   
 [Instruções de iteração](../../../csharp/language-reference/keywords/iteration-statements.md)