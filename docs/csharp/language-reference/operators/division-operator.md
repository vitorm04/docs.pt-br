---
title: "Operador / (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "/_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador / [C#]"
  - "Operador de divisão [C#]"
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador / (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador de divisão \(`/`\) divide o primeiro operando pelo seu segundo operando.  Todos os tipos numéricos têm predefinidos operadores de divisão.  
  
## Comentários  
 Tipos definidos pelo usuário podem sobrecarregar o `/` operador \(consulte  [operador](../../../csharp/language-reference/keywords/operator.md)\).  Uma sobrecarga de `/` operador implicitamente sobrecarrega o  [\= operador](../../../csharp/language-reference/operators/subtraction-assignment-operator.md).  
  
 Quando você divide dois números inteiros, o resultado é sempre um número inteiro.  Por exemplo, o resultado de 7 \/ 3 é 2.  Para determinar o restante 7 \/ 3, use o operador restante \([%](../../../csharp/language-reference/operators/modulus-operator.md)\).  Para obter um quociente como um número racional ou fração, fornecer o tipo dividendo ou divisor `float` ou `double`.  Você pode atribuir o tipo implicitamente se express o dividendo ou divisor como um decimal, colocando um dígito à direita da vírgula decimal, como mostra o exemplo a seguir.  
  
## Exemplo  
 [!CODE [csRefOperators#42](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#42)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)