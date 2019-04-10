---
title: ENTRE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: eae4387bcd5cbaf381ebf7169b6bc54d60328377
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309297"
---
# <a name="between-entity-sql"></a>ENTRE (Entity SQL)
Determina se uma expressão resulta em um valor em um intervalo especificado. O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ENTER expressão tem a mesma funcionalidade que a expressão Transact-SQL entre.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão válida para testar no intervalo definido por `begin_expression` e por `end_expression`. `expression` deve ser o mesmo tipo que `begin_expression` e `end_expression`.  
  
 `begin_expression`  
 Qualquer expressão válida. `begin_expression` deve ser o mesmo tipo que `expression` e `end_expression`. `begin_expression` deve ser menor que `end_expression`, caso contrário o valor retornado será negado.  
  
 `end_expression`  
 Qualquer expressão válida. `end_expression` deve ser o mesmo tipo que `expression` e `begin_expression`.  
  
 NOT  
 Especifica que o resultado de ENTER é negado.  
  
 AND  
 Atua como um espaço reservado que indica que `expression` deve estar dentro do intervalo indicado por `begin_expression` e por `end_expression`.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` Se `expression` está entre o intervalo indicado por `begin_expression` e `end_expression`; caso contrário, `false`. `null` será retornado se `expression` está `null` ou se `begin_expression` ou `end_expression` é `null`.  
  
## <a name="remarks"></a>Comentários  
 Para especificar um intervalo exclusivo, use o maior que (>) e menor que (<) operadores em vez de BETWEEN.  
  
## <a name="example"></a>Exemplo  
 Os seguintes usos da consulta SQL Entity ENTER o operador determinar se uma expressão resulta em um valor em um intervalo especificado. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
