---
title: "Operador ^= (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "^=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador ^= [C#]"
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador ^= (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador de atribuição de exclusivas\-OR.  
  
## Comentários  
 Uma expressão do formulário  
  
```  
x ^= y  
```  
  
 é avaliado como  
  
```  
x = x ^ y  
```  
  
 exceto pelo fato de `x` é avaliada apenas uma vez.  O  [^ operador](../../../visual-basic/language-reference/operators/xor-operator.md) realiza uma exclusivas\-OR operação bit a bit em operandos integrais e lógico exclusivas\-OR em  [bool](../../../csharp/language-reference/keywords/bool.md) operandos.  
  
 O ^ \= operador não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o  [^ operador](../../../visual-basic/language-reference/operators/xor-operator.md) \(consulte  [operador](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Exemplo  
 [!CODE [csRefOperators#23](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#23)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)