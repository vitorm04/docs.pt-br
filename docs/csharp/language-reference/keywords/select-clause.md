---
title: "Cl&#225;usula select (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "select_CSharpKeyword"
  - "select"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "cláusula select [C#]"
  - "palavra-chave select [C#]"
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Cl&#225;usula select (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Em uma expressão de consulta, o `select` cláusula Especifica o tipo de valores que será produzido quando a consulta é executada.  O resultado se baseará na avaliação de todas as cláusulas anteriores e em todas as expressões na `select` cláusula propriamente dito.  Uma expressão de consulta deve terminar com um um `select` cláusula ou um  [grupo](../../../csharp/language-reference/keywords/group-clause.md) cláusula.  
  
 O exemplo a seguir mostra um simples `select` cláusula em uma expressão de consulta.  
  
 [!CODE [cscsrefQueryKeywords#8](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#8)]  
  
 O tipo da seqüência produzido pela `select` cláusula determina o tipo de variável de consulta `queryHighScores`.  No caso mais simples, o `select` cláusula apenas Especifica a variável de intervalo.  Isso faz com que a seqüência retornada conter elementos do mesmo tipo como fonte de dados.  Para obter mais informações, consulte [Relacionamentos de tipo em operações de consulta LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  No entanto, o `select` cláusula também fornece um mecanismo eficiente para transformar \(ou  *projeção*\) em novos tipos de dados de origem.  Para obter mais informações, consulte [Transformações de dados com LINQ \(C\#\)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).  
  
## Exemplo  
 O exemplo a seguir mostra as diferentes formas que um `select` cláusula pode demorar.  Em cada consulta, observe a relação entre a `select` cláusula e o tipo da  *variável de consulta* \(`studentQuery1`, `studentQuery2`e assim por diante\).  
  
 [!CODE [cscsrefQueryKeywords#9](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#9)]  
  
 Conforme mostrado na `studentQuery8` no exemplo anterior, às vezes, convém os elementos da seqüência retornado para conter apenas um subconjunto das propriedades dos elementos de origem.  Mantendo a seqüência retornada o menor possível, você pode reduzir os requisitos de memória e aumentar a velocidade da execução da consulta.  Você pode fazer isso criando um tipo anônimo no `select` cláusula e usando um inicializador de objeto para inicializá\-lo com as propriedades adequadas do elemento de origem.  Para obter um exemplo de como fazer isso, consulte [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## Comentários  
 Em tempo de compilação, o `select` cláusula é convertida para uma chamada de método para o <xref:System.Linq.Enumerable.Select%2A> o operador de consulta padrão.  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Palavras\-chave de consulta \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Cláusula from](../../../visual-basic/language-reference/queries/from-clause.md)   
 [partial \(método\) \(Referência de C\#\)](../../../csharp/language-reference/keywords/partial-method.md)   
 [Tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Introdução a LINQ em C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)