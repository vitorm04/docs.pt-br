---
title: "Cl&#225;usula Take While (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.QueryTakeWhile"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "consultas [Visual Basic], Take While"
  - "cláusula Take While"
  - "instrução Take While"
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Take While (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Ignora elementos numa coleção desde que uma condição especificada seja `true` e então retorna os elementos restantes.  
  
## Sintaxe  
  
```  
Take While expression  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`expression`|Obrigatório.  Uma expressão que representa uma condição para a qual para testar elementos.  A expressão deve retornar um valor `Boolean` ou um funcional equivalente, como um `Integer` para ser avaliado como um `Boolean`.|  
  
## Comentários  
 O `Take While` cláusula inclui elementos desde o início do resultado de uma consulta até que o fornecido `expression` retorna `false`.  Após a `expression` retorna `false`, a consulta irá ignorar todos os elementos restantes.  A `expression` é ignorada para os resultados restantes.  
  
 O `Take While` cláusula difere do `Where` cláusula em que o `Where` cláusula pode ser usada para incluir todos os elementos de uma consulta que atendam a uma determinada condição.  O `Take While` cláusula inclui elementos somente até a primeira vez que a condição não for satisfeita.  A cláusula `Take While` é útil quando você está trabalhando com um resultado de consulta ordenado.  
  
## Exemplo  
 O seguinte exemplo de código usa a `Take While` cláusula para recuperar os resultados até que o primeiro cliente sem qualquer pedido seja encontrado.  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Take](../../../visual-basic/language-reference/queries/take-clause.md)   
 [Ignorar cláusula While](../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)