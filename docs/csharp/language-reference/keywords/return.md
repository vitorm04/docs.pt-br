---
title: "return (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "return_CSharpKeyword"
  - "return"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave return [C#]"
  - "instrução return [C#]"
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# return (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `return` instrução Finaliza a execução do método no qual ele aparece e devolve o controle para o método de chamada.  Ele também pode retornar um valor opcional.  Se o método é um `void` tipo, o `return` pode ser omitida a instrução.  
  
 Se a instrução return está dentro de um `try` bloco, o `finally` bloco, se houver, será executado antes que o controle retorna para o método de chamada.  
  
## Exemplo  
 No exemplo a seguir, o método `A()` retorna a variável `Area` como um  [double](../../../csharp/language-reference/keywords/double.md) valor.  
  
 [!code-cs[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Instrução return](/visual-cpp/cpp/return-statement-cpp)   
 [Instruções de salto](../../../csharp/language-reference/keywords/jump-statements.md)