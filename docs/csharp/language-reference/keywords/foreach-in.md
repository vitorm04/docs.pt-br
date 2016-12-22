---
title: "foreach, in (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "foreach"
  - "foreach_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave foreach [C#]"
  - "instrução foreach [C#]"
  - "em palavra-chave [C#]"
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# foreach, in (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A instrução `foreach` repete um grupo de instruções inseridas para cada elemento em uma matriz ou uma coleção de objetos que implementa a interface de <xref:System.Collections.IEnumerable?displayProperty=fullName> ou de <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>.  A instrução `foreach` é usada para iterar por meio da coleção para obter as informações que você deseja, mas não pode ser usada para adicionar ou remover itens da coleção de origem para evitar efeitos colaterais imprevisíveis.  Se você precisa adicionar ou remover itens da coleção de origem, use um loop [for](../../../csharp/language-reference/keywords/for.md).  
  
 As instruções inseridas continuam a ser executadas para cada elemento na matriz ou na coleção.  Após a iteração ter sido concluída para todos os elementos na coleção, o controle é transferido para a próxima declaração que segue o bloco de `foreach`.  
  
 Em qualquer ponto dentro do bloco de `foreach`, você pode quebrar o loop usando a palavra\-chave [break](../../../csharp/language-reference/keywords/break.md), ou pular para a próxima iteração no loop usando a palavra\-chave [continue](../../../csharp/language-reference/keywords/continue.md).  
  
 Um loop `foreach` também pode ser terminado por declarações de [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), ou de [throw](../../../csharp/language-reference/keywords/throw.md).  
  
 Para obter mais informações sobre a palavra\-chave `foreach` e exemplos de código, consulte os seguintes tópicos:  
  
 [Usando foreach com matrizes](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
 [Como acessar uma classe de coleção com foreach](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  
  
## Exemplo  
 O código a seguir mostra três exemplos:  
  
-   um loop típico de `foreach` que exibe o conteúdo de uma matriz de inteiros  
  
-   um loop [para](../../../csharp/language-reference/keywords/for.md) que faz a mesma coisa  
  
-   um loop `foreach` que mantém uma contagem do número de elementos da matriz  
  
 [!code-cs[csrefKeywordsIteration#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/foreach-in_1.cs)]  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Instruções de iteração](../../../csharp/language-reference/keywords/iteration-statements.md)   
 [for](../../../csharp/language-reference/keywords/for.md)