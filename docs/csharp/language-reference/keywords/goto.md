---
title: "goto (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "goto_CSharpKeyword"
  - "goto"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave goto [C#]"
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# goto (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `goto` instrução transfere o controle do programa diretamente para uma instrução rotulada.  
  
 Um uso comum do `goto` é transferir o controle para um rótulo específico do caso de opção ou o rótulo padrão em um `switch` instrução.  
  
 O `goto` instrução também é útil para sair do loops profundamente aninhados.  
  
## Exemplo  
 O exemplo a seguir demonstra o uso de `goto` em um  [Alternar](../../../csharp/language-reference/keywords/switch.md) instrução.  
  
 [!code-cs[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## Exemplo  
 O exemplo a seguir demonstra o uso de `goto` separar de loops aninhados.  
  
 [!code-cs[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Instrução goto](/visual-cpp/cpp/goto-statement-cpp)   
 [Instruções de salto](../../../csharp/language-reference/keywords/jump-statements.md)