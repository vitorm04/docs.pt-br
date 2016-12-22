---
title: "Operador () (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "()_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador () [C#]"
  - "Operador cast [C#]"
  - "conversão de tipo [C#], Operador ()"
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador () (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Além de que está sendo usado para especificar a ordem das operações em uma expressão, parênteses são usados para realizar as seguintes tarefas:  
  
1.  Especifique a projeções ou conversões de tipos.  
  
     [!CODE [csRefOperators#1](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#1)]  
  
2.  Chame métodos ou delegados.  
  
     [!CODE [csRefOperators#2](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#2)]  
  
## Comentários  
 Uma projeção chame explicitamente o operador de conversão de um tipo para outro; a conversão falhará se nenhum operador conversão for definida.  Para definir um operador de conversão, consulte  [explícita](../../../csharp/language-reference/keywords/explicit.md) e  [implícita](../../../csharp/language-reference/keywords/implicit.md).  
  
 O `()` operador não pode ser sobrecarregado.  
  
 Para obter mais informações, consulte [Conversões cast e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
 Uma expressão de conversão pode levar à sintaxe ambíguo.  Por exemplo, a expressão `(x)–y` poderia ser interpretadas como uma expressão de conversão \(um elenco – y tipo x\) ou como um aditivo expressão combinado com uma expressão entre parênteses, que calcula o valor de x\-y.  
  
 Para obter mais informações sobre a chamada do método, consulte [Métodos](../../../fsharp/language-reference/members/methods.md).  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)