---
title: "Operador &lt;&lt; (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "<<_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador << [C#]"
  - "Operador left shift (<<) [C#]"
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador &lt;&lt; (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador shift esquerda \(`<<`\) turnos seu primeiro operando esquerdo pelo número de bits especificado pelo seu segundo operando.  O tipo do segundo deve ser um  [int](../../../csharp/language-reference/keywords/int.md) ou um tipo que tem uma conversão numérica de implícita predefinida para `int`.  
  
## Comentários  
 Se o primeiro operando for um  [int](../../../csharp/language-reference/keywords/int.md) ou  [uint](../../../csharp/language-reference/keywords/uint.md) \(quantidade de 32 bits\), a contagem shift é dado pelos bits de ordem baixa cinco do segundo.  Ou seja, a contagem real shift é bits de 0 a 31.  
  
 Se o primeiro operando for um  [longo](../../../csharp/language-reference/keywords/long.md) ou  [ulong](../../../csharp/language-reference/keywords/ulong.md) \(quantidade de 64 bits\), a contagem shift é dado pelos seis bits de ordem inferior do segundo.  Ou seja, a contagem real shift é bits de 0 a 63.  
  
 Qualquer bits de ordem superior que não são dentro do intervalo do tipo do primeiro operando após a mudança são descartados e os bits de ordem inferior vazios são preenchidas com zero.  SHIFT operações nunca causam estouros.  
  
 Tipos definidos pelo usuário podem sobrecarregar o `<<` operador \(consulte  [operador](../../../csharp/language-reference/keywords/operator.md)\); o tipo do primeiro operando deve ser o tipo definido pelo usuário e o tipo do segundo deve ser `int`.  Se houver, quando um operador binário está sobrecarregado, o operador de atribuição correspondente, também será implicitamente sobrecarregado.  
  
## Exemplo  
 [!CODE [csRefOperators#14](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#14)]  
  
## Comentários  
 Observe que `i<<1` e `i<<33` dar o mesmo resultado, como 1 e 33 têm os mesmos cinco bits de ordem inferior.  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)