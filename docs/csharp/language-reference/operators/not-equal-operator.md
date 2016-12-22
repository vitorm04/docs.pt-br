---
title: "Operador != (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "!=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador != [C#]"
  - "Operador de desigualdade (!=) [C#]"
  - "Operador not equals (!=) [C#]"
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador != (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador de desigualdade \(`!=`\) retorna falso se operandos forem iguais, caso contrário, true.  Operadores de desigualdade são predefinidas para todos os tipos, incluindo a seqüência de caracteres e objeto.  Tipos definidos pelo usuário podem sobrecarregar o `!=` operador.  
  
## Comentários  
 Para tipos de valor, o operador de desigualdade de predefinidos \(`!=`\) retorna true se os valores dos operandos forem diferentes, FALSO caso contrário.  Para referência tipos diferentes de `string`, `!=` retorna true se dois operandos se referir a objetos diferentes.  Para o `string` tipo, `!=` compara os valores das cadeias de caracteres.  
  
 Tipos de valor definido pelo usuário podem sobrecarregar o `!=` operador \(consulte  [operador](../../../csharp/language-reference/keywords/operator.md)\).  Podem então os tipos de referência definidos pelo usuário, embora por padrão `!=` se comporta como descrito acima para ambos os tipos de referência predefinidas e definidas pelo usuário.  Se `!=` está sobrecarregado,  [\= \=](../../../csharp/language-reference/operators/equality-comparison-operator.md) também deve ser sobrecarregados.  Geralmente, as operações em tipos integrais são permitidas na enumeração.  
  
## Exemplo  
 [!CODE [csRefOperators#33](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#33)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)