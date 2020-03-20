---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: a0f5dd19c439861451b1e88c3ae35f9f265288fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150487"
---
# <a name="between-entity-sql"></a>BETWEEN (Entity SQL)
Determina se uma expressão resulta em um valor em um intervalo especificado. A [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressão BETWEEN tem a mesma funcionalidade da expressão Transact-SQL BETWEEN.  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression
```  
  
## <a name="arguments"></a>Argumentos  
 `expression`  
 Qualquer expressão válida para testar no intervalo definido por `begin_expression` e por `end_expression`. `expression` deve ser do mesmo tipo de `begin_expression` e `end_expression`.  
  
 `begin_expression`  
 Qualquer expressão válida. `begin_expression` deve ser do mesmo tipo de `expression` e `end_expression`. `begin_expression` deve ser menor que `end_expression`, o valor de retorno será negado mais.  
  
 `end_expression`  
 Qualquer expressão válida. `end_expression` deve ser do mesmo tipo de `expression` e `begin_expression`.  
  
 NOT  
 Especifica que o resultado de ENTER é negado.  
  
 AND  
 Atua como um espaço reservado que indica que `expression` deve estar dentro do intervalo indicado por `begin_expression` e por `end_expression`.  
  
## <a name="return-value"></a>Valor retornado  
 `true` se `expression` está entre o intervalo indicado por `begin_expression` e `end_expression`; caso contrário, `false`. `null` será retornado se `expression` é `null` ou se `begin_expression` ou `end_expression` são `null`.  
  
## <a name="remarks"></a>Comentários  
 Para especificar um intervalo exclusivo, use os operadores maiores (>) e menores do que (<) em vez de BETWEEN.  
  
## <a name="example"></a>Exemplo  
 Os seguintes usos da consulta SQL Entity ENTER o operador determinar se uma expressão resulta em um valor em um intervalo especificado. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [Como: Executar uma consulta que retorna resultados do tipo estrutural](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Confira também

- [Referência de Entity SQL](entity-sql-reference.md)
