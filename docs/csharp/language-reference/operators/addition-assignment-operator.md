---
title: "Operador += (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "+=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador += [C#]"
  - "Operador de atribuição de adição (+=) [C#]"
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador += (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador de atribuição de adição.  
  
## Comentários  
 Uma expressão usando o `+=` o operador de atribuição, como  
  
```  
x += y  
```  
  
 Equivale a  
  
```  
x = x + y  
```  
  
 exceto pelo fato de `x` é avaliada apenas uma vez.  O significado da  [operador \+](../../../csharp/language-reference/operators/addition-operator.md) depende dos tipos de `x` e `y` \(adição de operandos numéricos, a concatenação de operandos de cadeia de caracteres e assim por diante\).  
  
 O `+=` operador não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o  [operador \+](../../../csharp/language-reference/operators/addition-operator.md) \(consulte  [operador](../../../csharp/language-reference/keywords/operator.md)\).  
  
 O `+=` é também usado para especificar um método que será chamado em resposta a um evento; Esses métodos são chamados de manipuladores de eventos.  O uso da `+=` operador nesse contexto é conhecido como  *Assinando um evento*.  Para obter mais informações, consulte [Como realizar e cancelar a assinatura de eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  e [Delegados](../../../csharp/programming-guide/delegates/index.md).  
  
## Exemplo  
 [!CODE [csRefOperators#35](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#35)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)