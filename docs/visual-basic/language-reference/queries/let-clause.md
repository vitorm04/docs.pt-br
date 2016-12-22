---
title: "Cl&#225;usula Let (Visual Basic) | Microsoft Docs"
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
  - "vb.QueryLet"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "cláusula Let"
  - "instrução Let"
  - "consultas [Visual Basic], Let"
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Let (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Calcula um valor e o atribui a uma nova variável dentro da consulta.  
  
## Sintaxe  
  
```  
Let variable = expression [, ...]  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`variable`|Obrigatório.  Um alias que pode ser usado para referenciar os resultados da expressão fornecida.|  
|`expression`|Obrigatório.  Uma expressão que será avaliada e atribuída à variável especificada.|  
  
## Comentários  
 A cláusula `Let` permite que você calcule valores para cada resultado de consulta e referência\-los usando um alias.  O alias pode ser usado em outras cláusulas, como a cláusula `Where`.  A cláusula `Let` permite que você crie uma instrução de consulta que é mais fácil de ler, pois você pode especificar um alias para uma cláusula de expressão incluída na consulta e substituir o alias cada vez que a cláusula de expressão for usada.  
  
 Você pode incluir qualquer número de atribuições `variable` e `expression` na cláusula `Let`.  Separe cada atribuição com uma vírgula \(,\).  
  
## Exemplo  
 O exemplo de código a seguir utiliza a cláusula `Let` para calcular 10% de desconto em produtos.  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)