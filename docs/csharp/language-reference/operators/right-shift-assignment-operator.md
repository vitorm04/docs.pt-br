---
title: "Operador &gt;&gt;= (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - ">>=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador >>= (atribuição right-shift) [C#]"
  - "Operador de atribuição right-shift) (>>=) [C#]"
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador &gt;&gt;= (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador de atribuição de shift direita.  
  
## Comentários  
 Uma expressão do formulário  
  
```  
x >>= y  
```  
  
 é avaliado como  
  
```  
x = x >> y  
```  
  
 exceto pelo fato de `x` é avaliada apenas uma vez.  O  [\>\> operador](../Topic/%3E%3E%20Operator%20\(C%23%20Reference\).md) desloca `x` direita em um valor especificado pelo `y`.  
  
 O \>\> \= operador não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o  [\>\> operador de](../Topic/%3E%3E%20Operator%20\(C%23%20Reference\).md) \(consulte  [operador](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Exemplo  
 [!CODE [csRefOperators#11](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#11)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)