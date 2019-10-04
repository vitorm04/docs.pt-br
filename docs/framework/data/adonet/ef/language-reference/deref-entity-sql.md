---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 27fc23a2be47ea00eff20aa8d2f559af5ae90387
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833901"
---
# <a name="deref-entity-sql"></a>DEREF (Entity SQL)
Desreferencia um valor de referência e gera o resultado dessa desreferência.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a>Argumentos  
 `expression`  
 Qualquer expressão de consulta válida que retorna uma coleção.  
  
## <a name="return-value"></a>Valor de retorno  
 O valor de entidade que é referenciada.  
  
## <a name="remarks"></a>Comentários  
 O operador de DEREF desreferencia um valor de referência e gerencia o resultado do desreferencia. Por exemplo, se `r` for uma referência do tipo ref @ no__t-1T >, `Deref(r)` será uma expressão do tipo `T` que produz a entidade referenciada por `r`. Se o valor de referência é zero, ou está oscilando (isto é, o destino de referência não existir), o resultado do operador de DEREF é nulo.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa o operador de DEREF para desreferenciar um valor de referência e para gerar o resultado do desreferenciar. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [How para: Executar uma consulta que retorna os resultados de Primitivatype @ no__t-0.  
  
2. Passe a seguinte consulta como um argumento para o método de ExecutePrimitiveTypeQuery:  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
- [REF](ref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [Tipos estruturados anulável](nullable-structured-types-entity-sql.md)
