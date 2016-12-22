---
title: "Cl&#225;usula Join (Visual Basic) | Microsoft Docs"
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
  - "vb.QueryJoinIn"
  - "vb.QueryJoin"
  - "vb.QueryJoinOn"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "cláusula Join"
  - "instrução Join"
  - "consultas [Visual Basic], Join"
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Join (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Combina duas coleções numa única.  O operador adicionar é baseado em chaves combinadas e usa o operador `Equals`.  
  
## Sintaxe  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## Partes  
 `element`  
 Obrigatório.  A variável de controle para a coleção sendo juntada.  
  
 `collection`  
 Obrigatório.  A coleção a combinar com a coleção identificada no lado esquerdo do operador `Join`.  A cláusula `Join` pode ser acomodada em outra cláusula `Join` ou `Group Join`.  
  
 `joinClause`  
 Opcional.  Uma ou mais cláusulas `Join` adicionais para refinar a pergunta mais adiante.  
  
 `groupJoinClause`  
 Opcional.  Uma ou mais cláusulas `Group Join` adicionais para refinar a consulta mais adiante.  
  
 `key1` `Equals` `key2`  
 Obrigatório.  Identifica chaves para as coleções que estão sendo combinadas.  Você deve usar o operador `Equals` para comparar chaves das coleções que estão sendo combinadas.  Você pode combinar condições de associação, usando o operador `And` para identificar várias chaves.  `key1` deve ser do coleção no lado esquerdo do operador de `Join` .  `key2` deve ser do coleção no lado direito do operador de `Join` .  
  
 As chavesa usadas na condição de adição podem ser expressões que incluem mais de um item da coleção.  Entretanto, cada expressão chave pode conter somente itens da sua respectiva coleção  
  
## Comentários  
 A cláusula `Join` combina duas coleções baseadas nos valores das chaves que combinam das coleções sendo combinadas.  A coleção resultante pode conter qualquer combinação de valores da coleção no lado esquerdo do operador `Join` e na coleção identificada na cláusula `Join`.  A consulta retorna apenas resultados para os quais a condição especificada pelo operador `Equals` é satisfeita.  Isso é equivalente a um `INNER JOIN` no SQL.  
  
 Você pode usar várias cláusulas `Join` numa consulta para unir dois ou mais coleções numa coleção única.  
  
 Você pode realizar uma adição implícita para combinar coleções sem a cláusula `Join`.  Para fazer isso, inlcua várias cláusulas `In` na sua cláusula `From` e especifique uma cláusula `Where` que identifica as chaves que você deseja usar para a adição.  
  
 Você pode usar a cláusula `Group Join` para combinar coleções em uma única coleção hierárquica.  É como um `LEFT OUTER JOIN` no SQL.  
  
## Exemplo  
 O exemplo de código a seguir realiza uma adição implícita para combinar uma lista de clientes com seus pedidos.  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## Exemplo  
 O exemplo de código a seguir une duas coleções usando a cláusula `Join`.  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 Este exemplo produzirá saída igual à seguinte:  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## Exemplo  
 O exemplo de código a seguir une duas coleções usando a cláusula `Join` com duas colunas de chaves.  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 Este exemplo produzirá saída igual à seguinte:  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)   
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)