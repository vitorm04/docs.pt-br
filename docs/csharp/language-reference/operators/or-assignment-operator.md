---
title: "Operador |= (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "|=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador |= (atribuição OR) [C#]"
  - "Operador de atribuição OR (|=) [C#]"
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador |= (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador de atribuição ou.  
  
## Comentários  
 Uma expressão usando o `|=` o operador de atribuição, como  
  
```  
x |= y  
```  
  
 Equivale a  
  
```  
x = x | y  
```  
  
 exceto pelo fato de `x` é avaliada apenas uma vez.  O  [&#124; operador](../../../csharp/language-reference/operators/or-operator.md) executa uma operação lógica OR bit a bit em operandos integrais e lógica OR em operandos bool.  
  
 O `|=` operador não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o  [&#124; operador](../../../csharp/language-reference/operators/or-operator.md) \(consulte  [operador](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Exemplo  
 [!CODE [csRefOperators#10](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#10)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)