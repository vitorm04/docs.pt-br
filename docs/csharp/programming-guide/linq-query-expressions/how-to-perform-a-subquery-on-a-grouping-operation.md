---
title: "Como executar uma subconsulta em uma opera&#231;&#227;o de agrupamento (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "agrupando consultas LINQ [C#]"
  - "grupos [C#], expressões de consulta LINQ"
  - "grupos [LINQ em C#], subconsultas"
  - "consultas [LINQ in C#], agrupando"
  - "consultas [LINQ in C#], subconsultas"
  - "expressões de consulta [LINQ em C#], agrupando"
  - "expressões de consulta [LINQ em C#], subconsultas"
  - "subconsultas [C#]"
ms.assetid: 7b0805cd-53b4-429d-86b6-d37fb08f2c95
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como executar uma subconsulta em uma opera&#231;&#227;o de agrupamento (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este tópico mostra duas maneiras diferentes para criar uma consulta que classifica os dados de origem em grupos e, em seguida, executa uma subconsulta sobre cada grupo individualmente.  A técnica básica em cada exemplo é agrupar elementos de origem usando um  *continuação* chamado `newGroup`e gerar uma subconsulta nova contra `newGroup`.  Esta subconsulta é executada em relação a cada novo grupo é criado pela consulta externa.  Observe que, nesse exemplo específico da saída final, não é um grupo, mas uma simples seqüência de tipos anônimos.  
  
 Para obter mais informações sobre como grupo, consulte [Cláusula group](../../../csharp/language-reference/keywords/group-clause.md).  
  
 Para obter mais informações sobre a continuação, consulte [into](../../../csharp/language-reference/keywords/into.md).  O exemplo a seguir usa uma estrutura de dados na memória como fonte de dados, mas os mesmos princípios se aplicam para qualquer tipo de [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] fonte de dados.  
  
## Exemplo  
 [!code-cs[csProgGuideLINQ#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
  
## Compilando o código  
 Este exemplo contém referências a objetos que são definidos no aplicativo de amostra em [Como consultar uma coleção de objetos](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md).  Para compilar e executar esse método, colá\-lo na `StudentClass` classe nesse aplicativo e adicione uma chamada a partir do `Main` método.  
  
 Quando você adapta este método para seu próprio aplicativo, lembre\-se de que o LINQ requer a versão 3.5 da [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], e o projeto deve conter uma referência a System.Core.dll e o uso de uma diretriz para System. LINQ.  LINQ to SQL, LINQ to XML e LINQ to DataSet tipos exigem referências e usos adicionais.  Para obter mais informações, consulte [Como criar um projeto LINQ](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Consulte também  
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)