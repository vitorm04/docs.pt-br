---
title: "Cl&#225;usula Skip (Visual Basic) | Microsoft Docs"
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
  - "vb.QuerySkip"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "consultas [Visual Basic] Skip"
  - "instrução Skip"
  - "cláusula Skip"
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Skip (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Ignora um número especificado de elementos em uma coleção e, em seguida, retorna os elementos restantes.  
  
## Sintaxe  
  
```  
Skip count  
```  
  
## Partes  
 `count`  
 Obrigatório. Um valor ou uma expressão que retorna o número de elementos da sequência de ignorar.  
  
## Comentários  
 O `Skip` cláusula faz uma consulta ignorar os elementos no início de uma lista de resultados e retorna os elementos restantes. O número de elementos a serem ignorados é identificado pelo `count` parâmetro.  
  
 Você pode usar o `Skip` cláusula com o `Take` cláusula para retornar um intervalo de dados de qualquer segmento de uma consulta. Para fazer isso, passe o índice do primeiro elemento do intervalo para o `Skip` cláusula e o tamanho do intervalo para o `Take` cláusula.  
  
 Quando você usa o `Skip` cláusula em uma consulta, você também precisará garantir que os resultados são retornados em uma ordem que permitirá que o `Skip` cláusula para ignorar os resultados pretendidos. Para obter mais informações sobre a ordenação de resultados da consulta, consulte [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Você pode usar o `SkipWhile` cláusula para especificar que apenas determinados elementos são ignorados, dependendo de uma condição fornecida.  
  
## Exemplo  
 O seguinte exemplo de código usa o `Skip` cláusula junto com o `Take` cláusula para retornar dados de uma consulta em páginas. O `GetCustomers` função usa o `Skip` cláusula para ignorar os clientes na lista até que o de índice inicial fornecido valor e usa o `Take` cláusula para retornar uma página de clientes a partir desse valor de índice.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Ignorar cláusula While](../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Cláusula Take](../../../visual-basic/language-reference/queries/take-clause.md)