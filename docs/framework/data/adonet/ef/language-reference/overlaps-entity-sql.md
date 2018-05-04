---
title: SOBREPÕE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: 9b67e6824317b032f420501ffba385ec6fd651b9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="overlaps-entity-sql"></a>SOBREPÕE (Entity SQL)
Determina se duas coleções têm elementos comuns.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão de consulta válida que retornar uma coleção para comparar com a coleção retornada de outra expressão de consulta. Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `expression`.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` se as duas coleções possuem elementos comuns; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 SOBREPOSIÇÕES fornece funcionalmente equivalente à seguinte:  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 As OVERLAPS são um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita. Para obter informações de precedência para o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operadores de conjunto, consulte [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa as OVERLAPS que o operador determina se duas coleções possuem um valor comum. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar isso, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
