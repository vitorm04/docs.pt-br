---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: ee3877ca256eb3847b0284ac2a7362a4a60aad48
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="deref-entity-sql"></a>DEREF (Entity SQL)
Desreferencia um valor de referência e gera o resultado dessa desreferência.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão de consulta válida que retorna uma coleção.  
  
## <a name="return-value"></a>Valor de retorno  
 O valor de entidade que é referenciada.  
  
## <a name="remarks"></a>Comentários  
 O operador de DEREF desreferencia um valor de referência e gerencia o resultado do desreferencia. Por exemplo, se `r` uma referência de referência do tipo\<T >, `Deref``(r)` é uma expressão do tipo `T` que gera a entidade referenciada por `r`. Se o valor de referência é zero, ou está oscilando (isto é, o destino de referência não existir), o resultado do operador de DEREF é nulo.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa o operador de DEREF para desreferenciar um valor de referência e para gerar o resultado do desreferenciar. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Passe a seguinte consulta como um argumento para o método de ExecutePrimitiveTypeQuery:  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [Tipos estruturados anulável](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
