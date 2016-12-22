---
title: "Como armazenar os resultados de uma consulta na mem&#243;ria (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "armazenamento de resultados da consulta LINQ [LINQ em C#]"
  - "expressões de consulta [LINQ em c#], armazenando os resultados"
ms.assetid: 7271597f-3523-4f7b-b088-1eeffe913b2d
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como armazenar os resultados de uma consulta na mem&#243;ria (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma consulta é basicamente um conjunto de instruções sobre como recuperar e organizar dados.  Para executar a consulta requer uma chamada para o método de <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> .  Esta chamada é feito quando você usa um loop de `foreach` para iterar sobre os elementos.  Para avaliar uma consulta e armazenar seus resultados sem executar um loop de `foreach` , chamar apenas um dos seguintes métodos na variável de consulta:  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 Recomendamos que quando você armazena a resultados de consulta, você atribuímos o objeto retornado da coleção para uma nova variável como mostrado no exemplo o seguir:  
  
## Exemplo  
 [!code-cs[csProgGuideLINQ#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  
## Compilando o código  
  
-   Crie um projeto de [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] que tem como alvo o.NET Framework versão 3,5.  Por padrão, o projeto possui uma referência a System.Core.dll e uma política de `using` para o namespace para System.Linq.  
  
-   Copie o código em seu projeto.  
  
-   Pressione F5 para compilar e executar o programa.  
  
-   Pressione qualquer chave para sair da janela do console.  
  
## Consulte também  
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)