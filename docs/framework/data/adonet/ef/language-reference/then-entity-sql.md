---
title: ENTÃO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: f038f242bc0873df3d72700aa05fca2f76f777ff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161666"
---
# <a name="then-entity-sql"></a>ENTÃO (Entity SQL)

O resultado de QUANDO cláusula quando avaliar a `true`.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>Argumentos  

 `when_expression`  
 Qualquer expressão boolean válido.  
  
 `then_expression`  
 Qualquer expressão de consulta válida que retorna uma coleção.  
  
## <a name="remarks"></a>Comentários  

 Se `when_expression` avalia para o valor `true`, o resultado é `then-expression`correspondente. Se nenhum de QUANDO as condições sejam atendidas, `else-expression` é avaliado. No entanto, se não há `else-expression`, o resultado é nulo.  
  
 Para obter um exemplo, consulte [Case](case-entity-sql.md).  
  
## <a name="example"></a>Exemplo  

 A seguinte consulta SQL Entity usa a expressão de CASOS para avaliar um conjunto de expressões de `Boolean` . A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como executar uma consulta que retorna os resultados de primitivatype](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
## <a name="see-also"></a>Confira também

- [CASE](case-entity-sql.md)
- [Referência de Entity SQL](entity-sql-reference.md)
