---
title: "Operador &amp;= (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "&=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador &= [C#]"
  - "Operador de atribuição AND (&=) [C#]"
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador &amp;= (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador de atribuição E.  
  
## Comentários  
 Uma expressão usando o `&=` o operador de atribuição, como  
  
```  
x &= y  
```  
  
 Equivale a  
  
```  
x = x & y  
```  
  
 exceto pelo fato de `x` é avaliada apenas uma vez.  O  [& operador](../../../visual-basic/language-reference/operators/and-operator.md) executa uma operação lógica AND bit a bit em operandos integrais e e lógico em `bool` operandos.  
  
 O `&=` operador não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o binário  [& operador de](../../../visual-basic/language-reference/operators/and-operator.md) \(consulte  [operador](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Exemplo  
 [!CODE [csRefOperators#34](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#34)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)