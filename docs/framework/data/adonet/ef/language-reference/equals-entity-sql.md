---
title: = (Igual a) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 5cdfd35450514a9699a39cf78f64c0fa6b7d5f39
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833846"
---
# <a name="-equals-entity-sql"></a>= (Igual a) (Entity SQL)
Compara a igualdade de duas expressões.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
expression = expression  
-- or   
expression == expression  
```  
  
## <a name="arguments"></a>Argumentos  
 `expression`  
 Qualquer expressão válida. As duas expressões devem ter os tipos de dados implicitamente conversíveis.  
  
## <a name="result-types"></a>Tipos de resultado  
 `true` se a expressão esquerda é igual a expressão direita; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 O operador == do é equivalente a =.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa = operador de comparação para comparar a igualdade de duas expressões. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [How para: Executa uma consulta que retorna os resultados de Estruturaistype @ no__t-0.  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
