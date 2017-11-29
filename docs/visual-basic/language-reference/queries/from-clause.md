---
title: "Cláusula From (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ecdc8b70fb1ae164a6c78998ce11db9938fbb56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="from-clause-visual-basic"></a>Cláusula From (Visual Basic)
Especifica uma ou mais variáveis de intervalo e uma coleção para consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`element`|Necessário. Um *variável de intervalo* usado para iterar os elementos da coleção. Uma variável de intervalo é usada para fazer referência a cada membro do `collection` como a consulta itera por meio de `collection`. Deve ser um tipo enumerável.|  
|`type`|Opcional. O tipo de `element`. Se nenhum `type` for especificado, o tipo de `element` é inferido do `collection`.|  
|`collection`|Necessário. Refere-se à coleção a ser consultado. Deve ser um tipo enumerável.|  
  
## <a name="remarks"></a>Comentários  
 O `From` cláusula é usada para identificar a fonte de dados de uma consulta e as variáveis que são usadas para se referir a um elemento da coleção de origem. Essas variáveis são chamadas *variáveis de intervalo*. O `From` cláusula é necessária para uma consulta, exceto quando o `Aggregate` cláusula é usada para identificar uma consulta que retorna somente resultados agregados. Para obter mais informações, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Você pode especificar vários `From` cláusulas em uma consulta para identificar várias coleções a serem agrupadas. Quando várias coleções são especificadas, elas são iteradas independentemente ou você pode associá-los se eles estão relacionados. Você pode associar coleções implicitamente usando o `Select` cláusula, ou explicitamente, usando o `Join` ou `Group Join` cláusulas. Como alternativa, você pode especificar diversas variáveis de intervalo e coleções em uma única `From` cláusula, com cada variável de alcance e coleção separados dos outros por uma vírgula. O exemplo de código a seguir mostra as duas opções de sintaxe para a `From` cláusula.  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 O `From` cláusula define o escopo de uma consulta, que é semelhante ao escopo de um `For` loop. Portanto, cada `element` variável de intervalo no escopo de uma consulta deve ter um nome exclusivo. Porque você pode especificar vários `From` cláusulas para uma consulta, subsequentes `From` cláusulas podem fazer referência a variáveis de intervalo no `From` cláusula, ou eles podem consultar variáveis de alcance no anterior `From` cláusula. Por exemplo, o exemplo a seguir mostra um aninhada `From` cláusula onde a coleção na segunda cláusula é baseada em uma propriedade da variável de intervalo na primeira cláusula.  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 Cada `From` cláusula pode ser seguida por qualquer combinação de cláusulas de consulta adicionais para refinar a consulta. Você pode refinar a consulta das seguintes maneiras:  
  
-   Combinar várias coleções implicitamente, usando o `From` e `Select` cláusulas, ou explicitamente, usando o `Join` ou `Group Join` cláusulas.  
  
-   Use o `Where` cláusula para filtrar o resultado da consulta.  
  
-   Classifique os resultados usando o `Order By` cláusula.  
  
-   Agrupar resultados semelhantes usando a `Group By` cláusula.  
  
-   Use o `Aggregate` cláusula para identificar as funções de agregação a ser avaliada para o resultado da consulta inteira.  
  
-   Use o `Let` cláusula apresentar uma variável de iteração cujo valor é determinado por uma expressão em vez de uma coleção.  
  
-   Use o `Distinct` cláusula para ignorar os resultados da consulta duplicada.  
  
-   Identificar partes do que o resultado retornar usando o `Skip`, `Take`, `Skip While`, e `Take While` cláusulas.  
  
## <a name="example"></a>Exemplo  
 A consulta a seguir usa expressões um `From` cláusula para declarar uma variável de intervalo `cust` para cada `Customer` objeto o `customers` coleção. O `Where` cláusula usa a variável de intervalo para restringir a saída para os clientes da região especificada. O `For Each` loop exibe o nome da empresa para cada cliente no resultado da consulta.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Cláusula Distinct](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [Cláusula Join](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Cláusula Let](../../../visual-basic/language-reference/queries/let-clause.md)  
 [Cláusula Skip](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Cláusula Take](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)
