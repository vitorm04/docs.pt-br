---
title: ENTÃO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: 8d2d7f9a3a1d6ff9f25db3f19bf8f39781469f9f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305618"
---
# <a name="then-entity-sql"></a>ENTÃO (Entity SQL)
O resultado de QUANDO cláusula quando avaliar a `true`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `when_expression`  
 Qualquer expressão boolean válido.  
  
 `then_expression`  
 Qualquer expressão de consulta válida que retorna uma coleção.  
  
## <a name="remarks"></a>Comentários  
 Se `when_expression` avalia para o valor `true`, o resultado é `then-expression`correspondente. Se nenhum de QUANDO as condições sejam atendidas, `else-expression` é avaliado. No entanto, se não há `else-expression`, o resultado é nulo.  
  
 Por exemplo, consulte [caso](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa a expressão de CASOS para avaliar um conjunto de expressões de `Boolean` . A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como: Executar uma consulta que retorna resultados PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Consulte também

- [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)
- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
