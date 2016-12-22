---
title: "Operador ?: (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "?:_CSharpKeyword"
  - "?_CSharpKeyword"
  - ":_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador ?: [C#]"
  - "Operador condicional (?:) [C#]"
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador ?: (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador condicional \(`?:`\) retorna um de dois valores, dependendo do valor de uma expressão booleana. A seguir está a sintaxe para o operador condicional.  
  
```  
condition ? first_expression : second_expression;  
```  
  
## Comentários  
 O `condition` deve ser avaliada como `true` ou `false`. Se `condition` for `true`, `first_expression` é avaliada e torna\-se o resultado. Se `condition` for `false`, `second_expression` é avaliada e torna\-se o resultado. Apenas uma das duas expressões é avaliada.  
  
 O tipo de `first_expression` e `second_expression` deve ser o mesmo, ou uma conversão implícita deve existir de um tipo para outro.  
  
 Você pode expressar cálculos que caso contrário, podem exigir um `if-else` construção de forma mais concisa usando o operador condicional. Por exemplo, o código a seguir usa primeiro uma `if` instrução e, em seguida, um operador condicional para classificar um inteiro positivo ou negativo.  
  
```  
  
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
  
```  
  
 O operador condicional é associativo direito. A expressão `a ? b : c ? d : e` é avaliada como `a ? b : (c ? d : e)`, não como `(a ? b : c) ? d : e`.  
  
 O operador condicional não pode ser sobrecarregado.  
  
## Exemplo  
 [!CODE [csRefOperators#41](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#41)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)   
 [if\-else](../../../csharp/language-reference/keywords/if-else.md)   
 [Operadores ?. e ?](../../../csharp/language-reference/operators/null-conditional-operators.md)   
 [Operador ??](../../../csharp/language-reference/operators/null-conditional-operator.md)