---
title: "Como consultar uma cole&#231;&#227;o de objetos (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "consulta de coleção de objetos [C#]"
  - "consultas [LINQ in C#], coleções de objetos"
  - "expressões de consulta [LINQ em C#], coleções de objetos"
ms.assetid: 122d1e3b-1604-4add-b6b4-b84530a77b6b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como consultar uma cole&#231;&#227;o de objetos (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como executar uma consulta simples sobre uma lista de `Student` objetos.  Cada `Student` objeto contém algumas informações básicas sobre o aluno e uma lista que representa a pontuação do aluno em quatro exames.  
  
 Este aplicativo serve como a estrutura para muitos outros exemplos nesta seção que usam o mesmo `students` fonte de dados.  
  
## Exemplo  
 A consulta a seguir retorna os alunos que receberam uma pontuação de 90 ou mais em seu primeiro exame.  
  
 [!code-cs[csProgGuideLINQ#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-query-a-collection-of-objects_1.cs)]  
  
 Esta consulta é intencionalmente simple para que você possa experimentar.  Por exemplo, você pode tentar mais predicados na `where` cláusula ou use um `orderby` cláusula para classificar os resultados.  
  
## Compilando o código  
  
-   Criar um [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] o projeto que se destina a.NET Framework versão 3.5.  Por padrão, o projeto tem uma referência a System.Core.dll e um `using` diretriz para o namespace System. LINQ.  
  
-   Copie o código em seu projeto.  
  
-   Pressione F5 para compilar e executar o programa.  
  
-   Pressione qualquer tecla para sair da janela do console.  
  
## Consulte também  
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)