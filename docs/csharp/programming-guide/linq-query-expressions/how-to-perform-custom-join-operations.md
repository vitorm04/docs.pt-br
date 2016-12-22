---
title: "Como executar opera&#231;&#245;es de jun&#231;&#227;o personalizadas (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "junções personalizadas [C#]"
  - "junções [C#], personalizado"
  - "consultas [LINQ in C#], junções"
  - "expressões de consulta [LINQ em C#], junções"
ms.assetid: a05e2ab1-410d-4a1d-8ada-af93539682c9
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como executar opera&#231;&#245;es de jun&#231;&#227;o personalizadas (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como executar operações de associação que não são possíveis com o `join` cláusula.  Em uma expressão de consulta, o `join` cláusula está limitada a, e otimizado para, digite de equijoins, que são de longe mais comuns da operação join.  Ao realizar uma equijoin, você provavelmente sempre obter o melhor desempenho usando o `join` cláusula.  
  
 No entanto, o `join` cláusula não pode ser usada nos seguintes casos:  
  
-   Quando a associação está vinculada em uma expressão de desigualdade \(um não\-equijoin\).  
  
-   Quando a associação depende mais de uma expressão de igualdade ou desigualdade.  
  
-   Quando você tem que apresentar uma variável de intervalo temporário para a seqüência da direita \(interno\) antes da operação de associação.  
  
 Para realizar associações que não são equijoins, você pode usar várias `from` cláusulas apresentar cada fonte de dados de forma independente.  Em seguida, aplicar uma expressão de predicado em um `where` cláusula para a variável de intervalo para cada fonte.  A expressão também pode assumir a forma de uma chamada de método.  
  
> [!NOTE]
>  Não confunda esse tipo de operação de associação personalizado com o uso de vários `from` cláusulas para acessar coleções internas.  Para obter mais informações, consulte [Cláusula join](../../../csharp/language-reference/keywords/join-clause.md).  
  
## Exemplo  
 O primeiro método no exemplo a seguir mostra uma junção cruzada simple.  Junções cruzadas devem ser usadas com cautela, porque elas podem produzir conjuntos de resultados muito grande.  No entanto, elas podem ser úteis em algumas situações para criação de seqüências de código\-fonte em relação à qual as consultas adicionais que são executadas.  
  
 O segundo método produz uma seqüência de todos os produtos cujo ID da categoria está listado na lista Categoria à esquerda.  Observe o uso da `let` cláusula e a `Contains` método para criar uma matriz temporária.  Também é possível criar a matriz antes da consulta e eliminar o primeiro `from` cláusula.  
  
 [!code-cs[csProgGuideLINQ#64](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-perform-custom-join-operations_1.cs)]  
  
## Exemplo  
 No exemplo a seguir, a consulta deve associar\-se duas seqüências com base na correspondência de chaves que, no caso da seqüência interna \(lado direito\), não podem ser obtidas antes da cláusula join propriamente dito.  Se esta associação foram realizada com um `join` cláusula, em seguida, a `Split` método teria de ser chamado para cada elemento.  O uso de vários `from` cláusulas permite que a consulta evitar a sobrecarga da chamada do método repetidas.  No entanto, como `join` é otimizado, neste caso específico, pode ser mais rápido do que o uso de várias `from` cláusulas.  Os resultados irão variar dependendo principalmente a chamada de método é como cara.  
  
 [!code-cs[csProgGuideLINQ#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-perform-custom-join-operations_2.cs)]  
  
## Compilando o código  
  
-   Criar um [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] projeto de aplicativo de console que atinge [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 3.5 ou posterior.  Por padrão, o projeto tem uma referência a System.Core.dll e um `using` diretriz para o namespace System. LINQ.  
  
-   Substituir o `Program` a classe com o código do exemplo anterior.  
  
-   Siga as instruções de [Como unir conteúdo a partir de arquivos diferentes \(LINQ\)](../Topic/How%20to:%20Join%20Content%20from%20Dissimilar%20Files%20\(LINQ\).md) para configurar os arquivos de dados, scores.csv e names.csv.  
  
-   Pressione F5 para compilar e executar o programa.  
  
-   Pressione qualquer tecla para sair da janela do console.  
  
## Consulte também  
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Cláusula join](../../../csharp/language-reference/keywords/join-clause.md)   
 [Operações join](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [Como ordenar os resultados de uma cláusula join](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)