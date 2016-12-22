---
title: "Cl&#225;usula Where (Visual Basic) | Microsoft Docs"
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
  - "vb.QueryWhere"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "consultas [Visual Basic], Where"
  - "cláusula Where"
  - "instrução Where"
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Where (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica a condição de filtragem para uma consulta.  
  
## Sintaxe  
  
```  
Where condition  
```  
  
## Partes  
 `condition`  
 Obrigatório.  Uma expressão que determina se os valores para o item atual na coleção sNº do itemão incluídos na coleção de saída.  A expressão deve ser avaliada como um valor `Boolean` ou o equivalente de um valor `Boolean`.  Se a condição for avaliada como `True`,o elemento é incluído no resultado da consulta; caso contrário, o elemento é excluído do resultado da consulta.  
  
## Comentários  
 A cláusula `Where` permite que você filtre dados da consulta selecionando apenas os elementos que atendam a certos critérios.  Elementos cujos valores fazem com que a cláusula `Where` seja avaliada como `True` são incluídos no resultado da consulta; outros elementos serão excluídos.  A expressão que é usada em uma cláusula `Where` deve ser avaliada como um `Boolean` ou o equivalente de um `Boolean`, como um número inteiro que é avaliada como `False` quando seu valor é zero.  Você pode combinar várias expressões em uma cláusula `Where` usando os operadores lógicos, como `And`,`Or`,`AndAlso`,`OrElse`,`Is` e `IsNot`.  
  
 Por padrão, expressões de consulta não são avaliadas até que elas sejam acessadas — por exemplo, quando elas são ligadas a dados ou repetidas através de um loop `For`.  Como resultado, a cláusula `Where` não é avaliada até que a consulta seja acessada.  Se você tiver valores externos a consulta que são usados na cláusula `Where`,certifique\-se de que o valor apropriado é usado na cláusula `Where` no momento que a consulta é executada.  Para obter mais informações sobre a execução de consulta, consulte [Escrevendo a primeira consulta LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Você pode chamar funções em uma cláusula `Where` para executar um cálculo ou operação em um valor do elemento atual na coleção.  Chamar uma função em uma cláusula `Where` pode fazer com que a consulta seja executada imediatamente quando ela é definida em vez de quando ela é acessada.  Para obter mais informações sobre a execução de consulta, consulte [Escrevendo a primeira consulta LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## Exemplo  
 A expressão de consulta a seguir usa uma cláusula `From` para declarar uma variável de intervalo `cust` para cada objeto `Customer` na coleção `customers`.  A cláusula `Where` usa a variável de intervalo para restringir a saída para os clientes da região especificada.  O loop `For Each` exibe o nome da empresa para cada cliente no resultado da consulta.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## Exemplo  
 O exemplo a seguir usa `And` e `Or` operadores lógicos na `Where` cláusula.  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)