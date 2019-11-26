---
title: ACHATAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 84b846e3db86c664bc42363f3d983a1001f5c318
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833814"
---
# <a name="flatten-entity-sql"></a>ACHATAR (Entity SQL)
Converte uma coleção de coleções em uma coleção combinada. A nova coleção contém todos os mesmos elementos que a coleção antiga, mas sem uma estrutura aninhada.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a>Arguments  
 `collection`  
 Qualquer expressão válida que retorna uma coleção de coleções valor de ajuste em uma única coleção.  
  
## <a name="remarks"></a>Comentários  
 `FLATTEN` é um dos operadores de conjunto de [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita. Consulte [exceto](except-entity-sql.md) para obter informações de precedência para os operadores de conjunto de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 A seguinte consulta SQL Entity usa o operador de `FLATTEN` para converter uma coleção das coleções em uma coleção aplainada. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
