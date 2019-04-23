---
title: EM (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: d88f79dbfcd27f0ca0d1e26815d7d2bbee731bcf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331267"
---
# <a name="in-entity-sql"></a>EM (Entity SQL)
Determina se um valor corresponde a qualquer valor em uma coleção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Arguments  
 `value`  
 Qualquer expressão válida que retorna o valor para corresponder.  
  
 [ NOT ]  
 Especifica que o resultado `Boolean` de IN seja negado.  
  
 `expression`  
 Qualquer expressão válida que retorna a coleção para testar uma correspondência. Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `value`.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` se o valor for encontrado na coleção; nulo se o valor for nulo ou a coleção for nula; caso contrário, `false`. Usar NOT IN nega os resultados de IN.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta de Entity SQL usa o operador IN para determinar se um valor corresponde a qualquer valor em uma coleção. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
