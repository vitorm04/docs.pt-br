---
title: "Operador &lt;= (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "<=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador <= [C#]"
  - "Operador menor ou igual a (<=) [C#]"
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador &lt;= (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Todos os tipos numéricos e enumeração definem um "menor que ou igual" operador relacional \(`<=`\) que retorna `true` se o primeiro operando for menor ou igual ao segundo, `false` contrário.  
  
## Comentários  
 Tipos definidos pelo usuário podem sobrecarregar o `<=` operador.  Para obter mais informações, consulte  [operador](../../../csharp/language-reference/keywords/operator.md).  Se `<=` está sobrecarregado,  [\> \=](../Topic/%3E=%20Operator%20\(C%23%20Reference\).md) também deve ser sobrecarregados.  Geralmente, as operações em tipos integrais são permitidas na enumeração.  
  
## Exemplo  
 [!CODE [csRefOperators#32](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#32)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)