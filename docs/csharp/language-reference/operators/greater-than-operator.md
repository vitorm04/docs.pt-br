---
title: "Operador &gt; (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - ">_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador > [C#]"
  - "Operador greater than (>) [C#]"
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador &gt; (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Todos os tipos numéricos e enumeração definem um operador relacional "maior que" \(`>`\) que retorna `true` se o primeiro operando for maior que o segundo, `false` contrário.  
  
## Comentários  
 Tipos definidos pelo usuário podem sobrecarregar o `>` operador \(consulte  [operador](../../../csharp/language-reference/keywords/operator.md)\).  Se `>` está sobrecarregado,  [\<](../Topic/%3C%20Operator%20\(C%23%20Reference\).md) também deve ser sobrecarregados.  Se houver, quando um operador binário está sobrecarregado, o operador de atribuição correspondente, também será implicitamente sobrecarregado.  
  
## Exemplo  
 [!CODE [csRefOperators#29](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#29)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)