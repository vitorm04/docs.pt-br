---
title: "Operador || (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "||_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador || [C#]"
  - "Operador OR condicional (||) [C#]"
  - "Operador OR lógico [C#]"
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador || (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

OPERADOR condicional operador \(`||`\) executa um OR lógico dos operandos de `bool` .  Se o primeiro operando obtém a `true`, o segundo operando não é avaliada.  Se o primeiro operando obtém a `false`, o segundo operador determina se a expressão avaliará OU todo a `true` ou a `false`.  
  
## Comentários  
 a operação  
  
```  
x || y  
```  
  
 corresponde à operação  
  
```  
x | y  
```  
  
 exceto que se `x` é `true`, `y` não é analisada pois a operação OU é `true` independentemente do valor de `y`.  Esse conceito é conhecido como “short\-circuiting” a avaliação.  
  
 OPERADOR condicional operador não pode ser sobrecarregado, mas as sobrecargas de operadores lógicos e normais dos operadores de [true](../../../csharp/language-reference/keywords/true.md) e de [false](../../../csharp/language-reference/keywords/false.md) , com algumas limitações, são consideradas também ser sobrecargas de operadores lógicos condicionais.  
  
## Exemplo  
 Em os exemplos a seguir, a expressão que avalia `||` usa somente o primeiro operando.  A expressão que usa `|`avalia ambos os operandos.  Em o segundo exemplo, uma exceção em tempo de execução ocorre se ambos os operandos forem avaliados.  
  
 [!CODE [csRefOperators#52](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#52)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)