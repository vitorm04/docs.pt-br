---
title: "Operador | (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "|_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador | [C#]"
  - "Operador binário (|) [C#]"
  - "Operador OR bit a bit [C#]"
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador | (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Binário        `|`  operadores são predefinidas para os tipos integrais e `bool`.  Para tipos integrais,  `|`Calcula o OR bit a bit dos operandos.  Para `bool` operandos,  `|` Calcula o OR lógico dos operandos; ou seja, o resultado é `false` se e somente se ambos os operandos são `false`.  
  
## Comentários  
 Tipos definidos pelo usuário podem sobrecarregar o          `|` operador \(consulte  [operador](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Exemplo  
 [!CODE [csRefOperators#31](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#31)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)