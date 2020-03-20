---
title: = (Igual a) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 101dccd40e9197c7cf0795ccb80ded367676842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150306"
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
 Qualquer expressão válida. Ambas as expressões devem ter tipos de dados implicitamente conversíveis.  
  
## <a name="result-types"></a>Tipos de resultado  
 `true` se a expressão esquerda é igual a expressão direita; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 O operador == do é equivalente a =.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa = operador de comparação para comparar a igualdade de duas expressões. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [Como: Executar uma consulta que retorna resultados do tipo estrutural](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a>Confira também

- [Referência de Entity SQL](entity-sql-reference.md)
