---
title: "Como manipular valores nulos em express&#245;es de consulta (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "valores nulos [LINQ em C#]"
  - "consultas [LINQ in C#], valores nulos"
  - "expressões de consulta [LINQ em C#], valores nulos"
ms.assetid: cb34f7a1-7ef5-466a-90ba-91da30ab525d
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como manipular valores nulos em express&#245;es de consulta (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como lidar com possíveis valores nulos em coleções de origem.  Uma coleção de objetos, como um <xref:System.Collections.Generic.IEnumerable%601> podem conter elementos cujo valor é  [Nulo](../../../csharp/language-reference/keywords/null.md).  Se uma coleção de origem é nula ou contém um elemento cujo valor é nulo e sua consulta não lidar com valores nulos, um <xref:System.NullReferenceException> será gerada quando você executa a consulta.  
  
## Exemplo  
 Você pode codificar na defensiva para evitar uma exceção de referência nula, conforme mostrado no exemplo a seguir:  
  
 [!code-cs[csProgGuideLINQ#82](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 No exemplo anterior, o `where` cláusula filtra todos os elementos nulos na seqüência de categorias.  Essa técnica é independente do cheque nulo na cláusula join.  A expressão condicional com null neste exemplo funciona porque `Products.CategoryID` é do tipo `int?` que é a abreviação de `Nullable<int>`.  
  
## Exemplo  
 Em uma cláusula de associação, se apenas uma das teclas de comparação é um tipo de valor nulo, você pode converter o outro para um tipo anulável na expressão de consulta.  O exemplo a seguir, suponha que `EmployeeID` é uma coluna que contém os valores do tipo `int?`:  
  
 [!code-cs[csProgGuideLINQ#83](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## Consulte também  
 <xref:System.Nullable%601>   
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Tipos anuláveis](../../../csharp/programming-guide/nullable-types/index.md)