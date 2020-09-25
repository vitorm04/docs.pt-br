---
title: INTERSECÇÃO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: 217cd9b2a428c890d83d2b55d45321a04488398e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203638"
---
# <a name="intersect-entity-sql"></a>INTERSECÇÃO (Entity SQL)

Retorna uma coleção de todos os valores diferentes que são retornados pelas expressões de consulta nos lados esquerdo e direito do operando INTERSECT. Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `expression`.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a>Argumentos  

 `expression`  
 Qualquer expressão de consulta válida que retornar uma coleção para comparar com a coleção retornada de outra expressão de consulta.  
  
## <a name="return-value"></a>Valor Retornado  

 Uma coleção de mesmos tipos ou uma base comum ou um tipo derivado como `expression`.  
  
## <a name="remarks"></a>Comentários  

 INTERSECT é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita. Para obter informações de precedência para os [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operadores de conjunto, consulte [Except](except-entity-sql.md).  
  
## <a name="example"></a>Exemplo  

 A seguinte consulta SQL Entity usa o operador de CRUZAMENTO para retornar uma coleção de todos os valores diferentes que são retornados por expressões de consulta à esquerda e por lados direitos de operando de CRUZAMENTO. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#INTERSECT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#intersect)]  
  
## <a name="see-also"></a>Veja também

- [Referência de Entity SQL](entity-sql-reference.md)
