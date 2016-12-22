---
title: "Operador -= (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "-=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador -= (atribuição de subtração) [C#]"
  - "Operador de atribuição de subtração) (-=) [C#]"
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador -= (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador de atribuição de subtração.  
  
## Comentários  
 Uma expressão usando o `-=` o operador de atribuição, como  
  
```  
x -= y  
```  
  
 Equivale a  
  
```  
x = x - y  
```  
  
 exceto pelo fato de `x` é avaliada apenas uma vez.  O significado da  [\-operador](../../../csharp/language-reference/operators/subtraction-operator.md) depende dos tipos de `x` e `y` \(subtração para operandos numéricos, delegar a remoção para o delegado operandos e assim por diante\).  
  
 O `-=` operador não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o  [\-operador](../../../csharp/language-reference/operators/subtraction-operator.md) \(consulte  [operador](../../../csharp/language-reference/keywords/operator.md)\).  
  
 O\-\= operador também é usado no C\# a inscrição de um evento.  Para obter mais informações, consulte [Como realizar e cancelar a assinatura de eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## Exemplo  
 [!CODE [csRefOperators#6](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#6)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)