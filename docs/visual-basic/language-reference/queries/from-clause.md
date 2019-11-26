---
title: Cláusula From
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: a63fb41fc2b0ad885acf76ad5d56e446922f5b90
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343773"
---
# <a name="from-clause-visual-basic"></a>Cláusula From (Visual Basic)
Specifies one or more range variables and a collection to query.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`element`|Necessário. A *range variable* used to iterate through the elements of the collection. A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`. Must be an enumerable type.|  
|`type`|Opcional. O tipo de `element`. If no `type` is specified, the type of `element` is inferred from `collection`.|  
|`collection`|Necessário. Refers to the collection to be queried. Must be an enumerable type.|  
  
## <a name="remarks"></a>Comentários  
 The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection. These variables are called *range variables*. The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results. For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 You can specify multiple `From` clauses in a query to identify multiple collections to be joined. When multiple collections are specified, they are iterated over independently, or you can join them if they are related. You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses. As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma. The following code example shows both syntax options for the `From` clause.  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop. Therefore, each `element` range variable in the scope of a query must have a unique name. Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause. For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 Each `From` clause can be followed by any combination of additional query clauses to refine the query. You can refine the query in the following ways:  
  
- Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.  
  
- Use the `Where` clause to filter the query result.  
  
- Sort the result by using the `Order By` clause.  
  
- Group similar results together by using the `Group By` clause.  
  
- Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.  
  
- Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.  
  
- Use the `Distinct` clause to ignore duplicate query results.  
  
- Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.  
  
## <a name="example"></a>Exemplo  
 The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection. The `Where` clause uses the range variable to restrict the output to customers from the specified region. The `For Each` loop displays the company name for each customer in the query result.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>Consulte também

- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Cláusula Distinct](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [Cláusula Join](../../../visual-basic/language-reference/queries/join-clause.md)
- [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Cláusula Let](../../../visual-basic/language-reference/queries/let-clause.md)
- [Cláusula Skip](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Cláusula Take](../../../visual-basic/language-reference/queries/take-clause.md)
- [Cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)
