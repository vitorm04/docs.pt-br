---
title: "Como retornar uma consulta de um m&#233;todo (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "método retorna consulta [C#]"
  - "consultas [LINQ in C#], método retorna consulta"
  - "expressões de consulta [LINQ em C#], método retorna consulta"
ms.assetid: 9d6f20a7-f085-44cf-9df3-71948255ec68
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como retornar uma consulta de um m&#233;todo (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como retornar a uma consulta de um método como o valor de retorno e um `out` parâmetro.  
  
 Qualquer consulta deve ter um tipo de <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>, ou um tipo derivado, como <xref:System.Linq.IQueryable%601>.  Portanto, qualquer valor de retorno ou `out` o parâmetro de um método que retorna uma consulta também deve ter esse tipo.  Se um método materializes uma consulta em um concreto <xref:System.Collections.Generic.List%601> ou <xref:System.Array> tipo, ele é considerado estar retornando os resultados da consulta em vez da própria consulta.  Uma variável de consulta que é retornada de um método ainda pode ser composta ou modificada.  
  
## Exemplo  
 No exemplo a seguir, o primeiro método retorna uma consulta como um valor de retorno e o segundo método retorna uma consulta como um `out` parâmetro.  Observe que em ambos os casos é uma consulta que é retornado, não os resultados da consulta.  
  
 [!code-cs[csProgGuideLINQ#80](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-a-query-from-a-method_1.cs)]  
  
## Compilando o código  
  
-   Criar um [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] o projeto que se destina a.NET Framework versão 3.5 ou posterior.  Por padrão, o projeto tem uma referência a System.Core.dll e um `using` diretriz para o namespace System. LINQ.  
  
-   Substitua a classe com o código do exemplo.  
  
-   Pressione F5 para compilar e executar o programa.  
  
-   Pressione qualquer tecla para sair da janela do console.  
  
## Consulte também  
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)