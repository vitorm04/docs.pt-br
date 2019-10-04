---
title: EXISTE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 44f128a292b013fd3a3a80efdd2d10a63e3cfb07
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833832"
---
# <a name="exists-entity-sql"></a>EXISTE (Entity SQL)
Determina se uma coleção está vazia.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a>Argumentos  
 `expression`  
 Qualquer expressão válida que retorna uma coleção.  
  
 NOT  
 Especifica que o resultado EXISTS seja negado.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` se a coleção é não vazio; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 EXISTS é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita. Para obter informações de precedência para os operadores de conjunto [!INCLUDE[esql](../../../../../../includes/esql-md.md)], consulte [Except](except-entity-sql.md).  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa EXISTE operador para determinar se a coleção está vazia. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [How para: Executa uma consulta que retorna os resultados de Estruturaistype @ no__t-0.  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#EXISTS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#exists)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
