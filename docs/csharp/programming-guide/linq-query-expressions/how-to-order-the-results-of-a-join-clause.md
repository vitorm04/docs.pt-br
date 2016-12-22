---
title: "Como ordenar os resultados de uma cl&#225;usula join (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "cláusula join [C#]"
  - "junções [C#], ordenando resultados"
  - "consultas [LINQ in C#], junções"
  - "expressões de consulta [LINQ em C#], junções"
ms.assetid: 83f36f16-2ba3-453f-8b9f-7d02b415610e
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como ordenar os resultados de uma cl&#225;usula join (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como a ordem dos resultados de uma operação de associação.  Observe que a ordenação é executada após o ingresso.  Embora você possa usar um `orderby` as seqüências de cláusula com um ou mais de origem antes da associação, geralmente não é recomendável\-lo.  Alguns [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] provedores não podem preservar esse pedido após o ingresso.  
  
## Exemplo  
 Esta consulta cria uma associação de grupo e, em seguida, classifica os grupos com base em que o elemento de categoria, que ainda está no escopo.  O inicializador de tipo anônimo, dentro de uma subconsulta ordens de todos os elementos correspondentes da seqüência de produtos.  
  
 [!code-cs[csProgGuideLINQ#81](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-order-the-results-of-a-join-clause_1.cs)]  
  
## Compilando o código  
  
-   Criar um [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] o projeto que se destina a.NET Framework versão 3.5.  Por padrão, o projeto tem uma referência a System.Core.dll e um `using` diretriz para o namespace System. LINQ.  
  
-   Copie o código em seu projeto.  
  
-   Pressione F5 para compilar e executar o programa.  
  
-   Pressione qualquer tecla para sair da janela do console.  
  
## Consulte também  
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Cláusula orderby](../../../csharp/language-reference/keywords/orderby-clause.md)   
 [Cláusula join](../../../csharp/language-reference/keywords/join-clause.md)   
 [Operações join](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)