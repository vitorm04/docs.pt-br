---
title: "Cl&#225;usula Distinct (Visual Basic) | Microsoft Docs"
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
  - "vb.QueryDistinct"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "cláusula Distinct"
  - "instrução Distinct"
  - "consultas [Visual Basic], Distinct"
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Distinct (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Restringe os valores da variável atual de intervalo para eliminar valores duplicados nas cláusulas de consulta subsequentes.  
  
## Sintaxe  
  
```  
Distinct  
```  
  
## Comentários  
 Você pode usar a cláusula `Distinct` para retornar uma lista de itens exclusivos.  A cláusula `Distinct` faz a consulta ignorar resultados de consulta duplicados.  A cláusula `Distinct` aplica\-se a valores duplicados para todos os campos de retorno especificados pela cláusula `Select`.  Se nenhuma cláusula `Select` é especificada, a cláusula `Distinct` é aplicada à variável de intervalo para a consulta identificada na cláusula `From`.  Se o intervalo variável é um tipo não imutável, a consulta irá apenas ignorar um resultado de consulta se todos os membros do tipo coincidirem com um resultado da consulta existente.  
  
## Exemplo  
 A expressão de consulta a seguir associa uma lista de clientes e uma lista de pedidos de clientes.  A cláusula `Distinct` está incluída para retornar uma lista de nomes exclusivos de clientes e datas de pedido.  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)