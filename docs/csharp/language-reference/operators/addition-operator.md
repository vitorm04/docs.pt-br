---
title: "Operador + (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "+_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador + [C#]"
  - "Operador de adição [C#]"
  - "Operador de concatenação [C#]"
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador + (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `+` operador pode funcionar como um unário ou um operador binário.  
  
## Comentários  
 Unário `+` operadores são predefinidos para todos os tipos numéricos.  O resultado de um unário `+` operação em um tipo numérico é apenas o valor do operando.  
  
 Binário `+` operadores são predefinidas para tipos numéricos e de seqüência de caracteres.  Para numérico tipos \+ calcula a soma dos dois operandos.  Quando um ou ambos os operandos são do tipo string \+ concatena as representações de seqüência de caracteres dos operandos.  
  
 Tipos de delegate também fornecem um binário `+` operador, que executa o delegate concatenação.  
  
 Tipos definidos pelo usuário podem sobrecarregar o operador unário `+` e binário `+` operadores.  Operações em tipos integrais geralmente são permitidas na enumeração.  Para mais informações, consulte [operator](../../../csharp/language-reference/keywords/operator.md).  
  
## Exemplo  
 [!CODE [csRefOperators#28](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#28)]  
  
## Especificação de linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)   
 [operator](../../../csharp/language-reference/keywords/operator.md)