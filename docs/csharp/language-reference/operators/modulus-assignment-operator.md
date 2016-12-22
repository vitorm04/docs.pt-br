---
title: "Operador %= (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "%=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador de atribuição %= (atribuição de módulo) [C#]"
  - "Operador de atribuição de módulo (=%) [C#]"
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador %= (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador de atribuição do restante.  
  
## Comentários  
 Uma expressão usando o `%=` o operador de atribuição, como  
  
```  
x %= y  
```  
  
 Equivale a  
  
```  
x = x % y  
```  
  
 exceto pelo fato de `x` é avaliada apenas uma vez.  O  [operador %](../../../csharp/language-reference/operators/modulus-operator.md) predefinido de tipos numéricos calcular o resto após a divisão.  
  
 O `%=` operador não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o  [operador %](../../../csharp/language-reference/operators/modulus-operator.md) \(consulte [operator](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Exemplo  
 [!CODE [csRefOperators#4](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#4)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)