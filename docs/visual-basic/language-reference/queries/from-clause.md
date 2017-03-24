---
title: "Cláusula From (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic], From
- From clause
- From statement
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 52d085be3c8e694f49fa0660489e9fc9e8945234
ms.lasthandoff: 03/13/2017

---
# <a name="from-clause-visual-basic"></a>Cláusula From (Visual Basic)
Especifica uma ou mais variáveis intervalo e uma coleção para consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`element`|Necessário. A *variável de intervalo* usado para percorrer os elementos da coleção. Uma variável de alcance é usada para se referir a cada membro do `collection` como a consulta itera por meio de `collection`. Deve ser um tipo enumerável.|  
|`type`|Opcional. O tipo de `element`. Se nenhum `type` for especificado, o tipo de `element` é inferido do `collection`.|  
|`collection`|Necessário. Refere-se à coleção a ser consultado. Deve ser um tipo enumerável.|  
  
## <a name="remarks"></a>Comentários  
 O `From` cláusula é usada para identificar a fonte de dados para uma consulta e as variáveis que são usadas para se referir a um elemento da coleção de origem. Essas variáveis são chamadas *variáveis de alcance*. O `From` cláusula é necessária para uma consulta, exceto quando o `Aggregate` cláusula é usada para identificar uma consulta que retorna somente resultados agregados. Para obter mais informações, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Você pode especificar várias `From` cláusulas em uma consulta para identificar várias coleções a serem unidas. Quando várias coleções são especificadas, elas são iterados através de maneira independente, ou você pode associá-los se eles estão relacionados. Você pode associar coleções implicitamente usando a `Select` cláusula, ou explicitamente, usando o `Join` ou `Group Join` cláusulas. Como alternativa, você pode especificar diversas variáveis de alcance e coleções em uma única `From` cláusula, com cada variável de alcance e coleção separados dos outros por uma vírgula. O exemplo de código a seguir mostra as duas opções de sintaxe para o `From` cláusula.  
  
 [!code-vb[VbSimpleQuerySamples&#21;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 O `From` cláusula define o escopo de uma consulta, que é semelhante ao escopo de um `For` loop. Portanto, cada `element` variável de intervalo no escopo de uma consulta deve ter um nome exclusivo. Porque você pode especificar várias `From` cláusulas para uma consulta, subsequentes `From` cláusulas podem fazer referência a variáveis de alcance no `From` cláusula, ou eles podem consultar variáveis de alcance na anterior `From` cláusula. Por exemplo, o exemplo a seguir mostra uma construção `From` cláusula onde a coleção na segunda cláusula é baseada em uma propriedade da variável de intervalo na primeira cláusula.  
  
 [!code-vb[VbSimpleQuerySamples&#22;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 Cada `From` cláusula pode ser seguida por qualquer combinação de cláusulas de consulta adicionais para refinar a consulta. Você pode refinar a consulta das seguintes maneiras:  
  
-   Combinar várias coleções implicitamente usando a `From` e `Select` cláusulas, ou explicitamente, usando o `Join` ou `Group Join` cláusulas.  
  
-   Use o `Where` cláusula para filtrar o resultado da consulta.  
  
-   Classifique os resultados usando o `Order By` cláusula.  
  
-   Agrupar resultados semelhantes usando a `Group By` cláusula.  
  
-   Use o `Aggregate` cláusula para identificar as funções agregadas para avaliar para o resultado da consulta inteira.  
  
-   Use o `Let` cláusula para introduzir uma variável de iteração cujo valor é determinado por uma expressão em vez de uma coleção.  
  
-   Use o `Distinct` cláusula para ignorar os resultados da consulta duplicados.  
  
-   Identificar partes do que o resultado retornar usando o `Skip`, `Take`, `Skip While`, e `Take While` cláusulas.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta expressão utiliza um `From` cláusula para declarar uma variável de intervalo `cust` para cada `Customer` objeto o `customers` coleção. O `Where` cláusula usa a variável de intervalo para restringir a saída para os clientes da região especificada. O `For Each` loop exibe o nome da empresa para cada cliente no resultado da consulta.  
  
 [!code-vb[VbSimpleQuerySamples&#23;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Onde cláusula](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Cláusula DISTINCT](../../../visual-basic/language-reference/queries/distinct-clause.md)   
 [Cláusula JOIN](../../../visual-basic/language-reference/queries/join-clause.md)   
 [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)   
 [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Cláusula Let](../../../visual-basic/language-reference/queries/let-clause.md)   
 [Cláusula Skip](../../../visual-basic/language-reference/queries/skip-clause.md)   
 [Cláusula Take](../../../visual-basic/language-reference/queries/take-clause.md)   
 [Cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)
