---
title: '|| (OU) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 6437b17fe1c1277701f06988ef6c02f4caf70e62
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319465"
---
# <a name="-or-entity-sql"></a>|| (OU) (Entity SQL)
Combina duas expressões de `Boolean` .  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
boolean_expression OR boolean_expression  
-- or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Qualquer expressão válida que retorna `Boolean`.  
  
## <a name="return-value"></a>Valor retornado  
 `true` quando uma das condições for `true`; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 OR é um operador lógico de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . É usada para combinar duas condições. Quando mais de um operador lógico é usado em uma declaração, OU de operadores são avaliados em seguida E operadores. No entanto, você pode alterar a ordem de classificação usando parênteses.  
  
 As barras verticais duplas (&#124;&#124;) têm a mesma funcionalidade que o operador OR.  
  
 A tabela a seguir mostra valores e tipos de retorno de entrada possíveis.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|TRUE|TRUE|  
|`FALSE`|TRUE|FALSE|NULL|  
|`NULL`|TRUE|NULL|NULL|  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa o operador OR para combinar duas expressões de `Boolean` . A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
