---
title: "try-finally (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "finally"
  - "finally_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave finally [C#]"
  - "instrução try-finally [C#]"
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# try-finally (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Usando um bloco `finally`, você pode limpar os recursos que são alocados em um bloco [try](../../../csharp/language-reference/keywords/try-catch.md) e pode executar o código mesmo se uma exceção ocorrer no bloco  `try`.  Em geral, as instruções de um bloco `finally` são executadas quando o controle deixa uma instrução de `try`.  A transferência de controle pode ocorrer como resultado da execução normal, da execução de uma declaração `break`, `continue`,  `goto` ou `return` ou da propagação de uma exceção fora da declaração `try` .  
  
 Dentro de uma exceção manipulada, é garantido que o bloco associado `finally` seja executado.  No entanto, se a exceção não for tratada, a execução do bloco `finally` será dependente de como a operação de desenrolamento da exceção será acionada.  Isso, por sua vez, depende de como seu computador está configurado.  Para obter mais informações, consulte [Processamento de exceção sem tratamento no CLR](http://go.microsoft.com/fwlink/?LinkId=128371).  
  
 Em geral, quando uma exceção não tratada encerrar um aplicativo, mesmo que o bloco `finally` seja ou não executado, isso não é importante.  No entanto, se você tiver instruções em um bloco `finally` que deve ser executado mesmo nessa situação, uma solução é adicionar um bloco `catch` à declaração `try`\-`finally`.  Como alternativa, você pode capturar a exceção que pode ser apresentada no bloco `try` de uma instrução `try`\-`finally` maior à pilha de chamadas.  Ou seja, você pode capturar a exceção no método que chama o método que contém a instrução `try`\- de`finally` ou o método que chama esse método, ou em qualquer método na pilha de chamadas.  Se a exceção não é detectada, a execução do bloco `finally` depende se o sistema operacional escolhe acionar uma operação de desenrolamento da exceção.  
  
## Exemplo  
 No exemplo a seguir, uma declaração inválida de conversão causa uma exceção de `System.InvalidCastException`.  A exceção não é tratada.  
  
 [!code-cs[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 No exemplo a seguir, uma exceção do método `TryCast` é detectada em um método extremo à pilha de chamadas.  
  
 [!code-cs[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 Para obter mais informações sobre `finally`, consulte [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
 C\# também contém a [instrução using](../../../visual-basic/language-reference/statements/using-statement.md), que fornece funcionalidade semelhante para objetos <xref:System.IDisposable> em uma sintaxe conveniente.  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Instruções try, throw e catch \(C\+\+\)](/visual-cpp/cpp/try-throw-and-catch-statements-cpp)   
 [Instruções para manipulação de exceções](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [Como lançar exceções explicitamente](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)