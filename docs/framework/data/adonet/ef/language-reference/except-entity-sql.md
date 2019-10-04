---
title: EXCETO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: c4df8c2b72ee60a425c98c64a13a1e2d43d4506e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833858"
---
# <a name="except-entity-sql"></a>EXCETO (Entity SQL)
Retorna uma coleção de todos os valores distintos da expressão de consulta para a esquerda do operando EXCEPT que também não são retornados da expressão de consulta à direita do operando EXCEPT. Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `expression`.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Argumentos  
 `expression`  
 Qualquer expressão de consulta válida que retornar uma coleção para comparar com a coleção retornada de outra expressão de consulta.  
  
## <a name="return-value"></a>Valor de retorno  
 Uma coleção de mesmos tipos ou uma base comum ou um tipo derivado como `expression`.  
  
## <a name="remarks"></a>Comentários  
 EXCETO é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita. A tabela a seguir mostra a precedência de operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
|Precedência|Operadores|  
|----------------|---------------|  
|O mais alto|INTERSECT|  
||UNION<br /><br /> TODOS UNION|  
||EXCEPT|  
|O menor|EXISTE<br /><br /> OVERLAPS<br /><br /> FLATTEN<br /><br /> SET|  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa A QUE operador NOT SER para retornar uma coleção de todos os valores diferentes de duas expressões de consulta. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [How para: Executa uma consulta que retorna os resultados de Estruturaistype @ no__t-0.  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
