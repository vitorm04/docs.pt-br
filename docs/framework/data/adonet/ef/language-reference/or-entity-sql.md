---
title: '|| (OU) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 09ae742f648f95819a8c6fc64d402c4f11c7748a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764613"
---
# <a name="-or-entity-sql"></a>|| (OU) (Entity SQL)
Combina duas expressões de `Boolean` .  
  
## <a name="syntax"></a>Sintaxe  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Qualquer expressão válida que retorna `Boolean`.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` quando uma das condições for `true`; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 OR é um operador lógico de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . É usada para combinar duas condições. Quando mais de um operador lógico é usado em uma declaração, OU de operadores são avaliados em seguida E operadores. No entanto, você pode alterar a ordem de classificação usando parênteses.  
  
 Barras verticais duplas (&#124;&#124;) têm a mesma funcionalidade que o operador OR.  
  
 A tabela a seguir mostra valores e tipos de retorno de entrada possíveis.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|TRUE|TRUE|  
|`FALSE`|TRUE|FALSE|NULL|  
|`NULL`|TRUE|NULL|NULL|  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa o operador OR para combinar duas expressões de `Boolean` . A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
