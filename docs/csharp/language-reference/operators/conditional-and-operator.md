---
title: "Operador &amp;&amp; (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "&&_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador && [C#]"
  - "Operador AND lógico [C#]"
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador &amp;&amp; (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A condicional\- E operador \(`&&`\) executa uma lógica\- E de sua `bool` operandos, mas somente avalia o seu segundo operando se necessário.  
  
## Comentários  
 A operação  
  
```  
x && y  
```  
  
 corresponde à operação  
  
```  
x & y  
```  
  
 exceto que se `x` é `false`, `y` não é avaliada, porque o resultado da operação e é `false` não importa que o valor de `y`  é.  Isso é conhecido como "" avaliação de circuito curto.  
  
 A condicional\- E o operador não pode ser sobrecarregado, mas sobrecargas dos operadores lógicos regulares e operadores de  [true](../../../csharp/language-reference/keywords/true.md) e  [false](../../../csharp/language-reference/keywords/false.md) , com certas restrições, também são considerados sobrecargas dos operadores lógicos condicionais.  
  
## Exemplo  
 No exemplo a seguir, a expressão condicional na segunda `if` instrução avalia apenas o primeiro operando como o operando retorna `false`.  
  
 [!CODE [csRefOperators#48](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#48)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)