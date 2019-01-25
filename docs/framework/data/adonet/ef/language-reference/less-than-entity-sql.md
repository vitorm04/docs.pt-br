---
title: '&lt; (Menor que) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: 0c2185f824cfbe201b4138d0082e3edcf93e6a7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598264"
---
# <a name="lt-less-than-entity-sql"></a>&lt; (Menor que) (Entity SQL)
Compara duas expressões para determinar se a expressão da esquerda tem um valor menor que a expressão da direita.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão válida. As duas expressões devem ter os tipos de dados implicitamente conversíveis.  
  
## <a name="result-types"></a>Tipos de resultado  
 `true` se a expressão esquerda tem um valor menor do que a expressão direita; caso contrário, `false`.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa < o operador de comparação para comparar duas expressões para determinar se a expressão esquerda tem um valor menor do que a expressão direita. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a>Consulte também
- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
