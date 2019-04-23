---
title: DEFINIR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 4e2a387cf400a881dfd91c61b36ee3ce0f5a4431
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59309427"
---
# <a name="set-entity-sql"></a>DEFINIR (Entity SQL)
A expressão SET é usada para converter uma coleção de objetos em um conjunto rendendo uma nova coleção com todos os elementos duplicados removidos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão de consulta válida que retorna uma coleção.  
  
## <a name="remarks"></a>Comentários  
 A expressão de `SET(c)` é logicamente equivalente à instrução select seguinte:  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET` é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita. Ver [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) para obter informações de precedência para a [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operadores definidos.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa a expressão SET para converter uma coleção de objetos em um dataset. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como: Executar uma consulta que retorna resultados PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
