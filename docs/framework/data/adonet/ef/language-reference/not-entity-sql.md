---
title: '! (NÃO) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 0eb9be9ed4cbce45a51d15eea68e9fb1a26f0107
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191834"
---
# <a name="-not-entity-sql"></a>! (NÃO) (Entity SQL)

Nega uma expressão de `Boolean` .  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a>Argumentos  

 `boolean_expression`  
 Qualquer expressão válida que retorna um valor booleano.  
  
## <a name="remarks"></a>Comentários  

 O ponto de exclamação (!) tem a mesma funcionalidade que o operador NOT.  
  
## <a name="example"></a>Exemplo  

 A seguinte consulta SQL Entity usa o operador NOT nega uma expressão de `Boolean` . A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a>Veja também

- [Referência de Entity SQL](entity-sql-reference.md)
