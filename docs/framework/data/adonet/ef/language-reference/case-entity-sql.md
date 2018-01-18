---
title: CASO (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9afc5e3bbf8e6fe732aca9e65c8ba5bd5f620c85
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="case-entity-sql"></a>CASO (Entity SQL)
Avalia um conjunto de expressões de `Boolean` para determinar o resultado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 É um espaço reservado que indica que várias QUANDO as cláusulas de `Boolean_expression` ENTÃO `result_expression` podem ser usadas.  
  
 ENTÃO `result_expression`  
 A expressão é retornada quando `Boolean_expression` avalia a `true`. `result expression` é qualquer expressão válida.  
  
 `else_result_expression`OUTRO  
 A expressão é retornada se qualquer operação de comparação avalia a `true`. Se esse argumento é omitido e nenhuma operação de comparação avalia a `true`, os CASOS retornam o zero. `else_result_expression` é qualquer expressão válida. Os tipos de dados de `else_result_expression` e qualquer `result_expression` devem ser os mesmos ou devem ser uma conversão implícita.  
  
 QUANDO `Boolean_expression`  
 A expressão é avaliada de `Boolean` quando o formato pesquisada de CASOS é usado. `Boolean_expression` é qualquer expressão válida de `Boolean` .  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna o tipo mais alto de precedência de conjunto de tipos em `result_expression` e `else_result_expression`opcional.  
  
## <a name="remarks"></a>Comentários  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressão case é semelhante a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] caso a expressão. Você usa a expressão dos casos para fazer uma série de teste condicional para determinar qual expressão renderá o resultado apropriado. Este formulário da expressão dos casos se aplica a uma série de uma ou mais expressões de `Boolean` para determinar a expressão resultante correta.  
  
 A função de CASOS avaliar `Boolean_expression` para o QUANDO cada cláusula na ordem especificada, e retornar `result_expression` de primeiro `Boolean_expression` que avalia para `true`. As expressões restantes não são avaliadas. Se nenhum `Boolean_expression` avalia a `true`, o mecanismo de base de dados retorna `else_result_expression` se uma cláusula OUTRA for especificada, ou um valor nulo se nenhuma cláusula OUTRA é especificado.  
  
 Uma declaração de CASOS não pode retornar um multiset.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa a expressão de CASOS para avaliar um conjunto de expressões de `Boolean` para determinar o resultado. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Consulte também  
 [THEN](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)  
 [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
