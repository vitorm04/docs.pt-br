---
title: "as (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "as_CSharpKeyword"
  - "as"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave as [C#]"
  - "conversão de tipo [C#], palavra-chave as"
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# as (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode usar o operador para executar `as` de certos tipos de conversões entre tipos compatíveis de referência ou [tipos anuláveis](../../../csharp/programming-guide/nullable-types/index.md).  O código a seguir mostra um exemplo.  
  
 [!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## Comentários  
 O operador de `as` é como uma operação de conversão.  No entanto, se a conversão não é possível, `as` retorna `null` em vez de gerar uma exceção.  Considere o exemplo a seguir:  
  
```  
expression as type  
```  
  
 O código é equivalente à seguinte expressão exceto que a variável de `expression` é avaliado apenas uma vez.  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 Observe que o operador de `as` somente executa conversões de referência, conversões anulável, e conversões boxing de.  O operador de `as` não pode executar outras conversões, como as conversões definidos pelo usuário, em vez de que devem ser executadas usando o converter expressões.  
  
## Exemplo  
 [!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [Operador ?:](../../../csharp/language-reference/operators/conditional-operator.md)   
 [Palavras\-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md)