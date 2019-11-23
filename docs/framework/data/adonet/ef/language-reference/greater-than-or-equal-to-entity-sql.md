---
title: '>= (Maior ou igual a) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 9e1d7e92097713ebdaf15523a5f99f98ed8be0b3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833741"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a>> = (maior ou igual a) (Entity SQL)
Compara duas expressões para determinar se a expressão da esquerda tem um valor maior que ou igual à expressão da direita.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
expression >= expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão válida. As duas expressões devem ter os tipos de dados implicitamente conversíveis.  
  
## <a name="result-types"></a>Tipos de resultado  
 `true` se a expressão esquerda tem um valor maior ou igual à expressão direita; caso contrário, `false`.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O Entity SQL consulta a seguir usa > = operador de comparação para comparar duas expressões para determinar se a expressão esquerda tem um valor maior ou igual à expressão direita. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#GREATER_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater_or_equals)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
