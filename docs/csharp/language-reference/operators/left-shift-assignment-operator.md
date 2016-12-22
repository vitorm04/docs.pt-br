---
title: "Operador &lt;&lt;= (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "<<=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador <<= (atribuição left-shift) [C#]"
  - "Operador de atribuição left shift (<<=) [C#]"
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador &lt;&lt;= (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador de atribuição de shift esquerda.  
  
## Comentários  
 Uma expressão do formulário  
  
```  
x <<= y  
```  
  
 é avaliado como  
  
```  
x = x << y  
```  
  
 exceto pelo fato de `x` é avaliada apenas uma vez.  O  [\<\< operador](../../../csharp/language-reference/operators/left-shift-operator.md) desloca `x` esquerda pelo número de bits especificado pelo `y`.  
  
 O `<<=` operador não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o  [\<\< operador de](../../../csharp/language-reference/operators/left-shift-operator.md) \(consulte  [operador](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Exemplo  
 [!CODE [csRefOperators#12](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#12)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)