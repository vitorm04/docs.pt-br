---
title: "Cl&#225;usula Take (Visual Basic) | Microsoft Docs"
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
  - "vb.QueryTake"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "consultas [Visual Basic], Take"
  - "cláusula Take"
  - "instrução Take"
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Take (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Retorna um número especificado de elementos contíguos do início de uma coleção.  
  
## Sintaxe  
  
```  
Take count  
```  
  
## Partes  
 `count`  
 Obrigatório.  Um valor ou uma expressão que avalia ao número de elementos da sequência a retornar.  
  
## Comentários  
 A cláusula `Take` faz com que uma dúvida inclua um número especificado de elementos contíguos do início de uma lista de resultados.  O número de elementos para incluir é especificado pelo parâmetro `count`.  
  
 Você pode usar a cláusula `Take` com a cláusula `Skip` para retornar um intervalo de dados de qualquer segmento de uma consulta.  Para fazer isso, passe o índice do primeiro elemento do intervalo para a cláusula `Skip` e o tamanho do intervalo para a cláusula `Take`.  Nesse caso, a cláusula `Take` deve ser especificada após a cláusula `Skip`.  
  
 Ao usar a cláusula `Take` em uma pergunta, você também precisará garantir que os resultados são retornados em uma ordem que permitirá que a cláusula `Take` inclua os resultados pretendidos.  Para obter mais informações sobre pedido resultados de pergunta, consulte [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Você pode usar a cláusula `TakeWhile` para especificar que apenas determinados elementos serão retornado, dependendo  de uma condição fornecida.  
  
## Exemplo  
 O exemplo de código a seguir utiliza a cláusula `Take` juntamente com a cláusula `Skip` para retornar dados de uma consulta em páginas.  A função GetCustomers usa a cláusula `Skip` para circundar os clientes na lista até que o valor de índice inicial fornecido e a cláusula `Take` para retornar uma página de clientes a partir desse valor de índice.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)   
 [Cláusula Skip](../../../visual-basic/language-reference/queries/skip-clause.md)