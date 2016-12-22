---
title: "throw (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "throw"
  - "throw_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave throw [C#]"
  - "instrução throw [C#]"
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# throw (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A instrução `throw` é usada para sinalizar a ocorrência de uma situação anômala \(exceção\) durante a execução do programa.  
  
## Comentários  
 A exceção acionada é um objeto cuja classe é derivada de <xref:System.Exception?displayProperty=fullName> conforme mostrado no exemplo a seguir.  
  
```  
class MyException : System.Exception {}  
// ...  
throw new MyException();  
```  
  
 Geralmente, a instrução `throw` é usada com `try-catch` ou instruções `try-finally`.  Uma instrução [throw](../../../csharp/language-reference/keywords/throw.md) pode ser usada em um bloco `catch` para acionar novamente a exceção que o bloco `catch` identificou.  Nesse caso, a instrução [throw](../../../csharp/language-reference/keywords/throw.md) não usa um operando de exceção.  Para obter mais informações e exemplos, consulte [try\-catch](../../../csharp/language-reference/keywords/try-catch.md) e [Como lançar exceções explicitamente](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md).  
  
## Exemplo  
 Este exemplo demonstra como acionar uma exceção usando a instrução `throw`.  
  
 [!code-cs[csrefKeywordsExceptions#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/throw_1.cs)]  
  
## Exemplo de código  
 Consulte os exemplos em [try\-catch](../../../csharp/language-reference/keywords/try-catch.md) e [Como lançar exceções explicitamente](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md).  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [As instruções try, catch e throw em C\+\+](../../../csharp/language-reference/keywords/try-catch.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Instruções para manipulação de exceções](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [Como lançar exceções explicitamente](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)