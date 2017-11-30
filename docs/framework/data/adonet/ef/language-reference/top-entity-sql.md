---
title: TOPO (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9b1d3d1b07a349ab1a5efb4a7c41f9b9b34fc55f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="top-entity-sql"></a>TOPO (Entity SQL)
A cláusula SELECT pode ter uma cláusula as subjanelas TOP opcional após o modificador opcional de ALL/DISTINCT. A cláusula subpropriedades TOP especifica que apenas definir primeiro as linhas será retornado do resultado da consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 A expressão numérica que especifica o número de linhas a serem retornadas. `n` pode ser um único literal numérico ou um único parâmetro.  
  
## <a name="remarks"></a>Comentários  
 A expressão TOP deve ser um único literal numérico ou um único parâmetro. Se um literal constante é usado, o tipo literal deve ser implicitamente promotable a Edm.Int64 (byte, int16 ou int32, int64 ou qualquer tipo de provedor que o mapeamento para um tipo que é promotable a Edm.Int64) e seu valor deve ser maior ou igual a zero. Se não uma exceção será lançada. Se um parâmetro é usado como uma expressão, o tipo de parâmetro deve também ser implicitamente promotable a Edm.Int64, mas não haverá validação do valor do parâmetro real durante a compilação porque valores de parâmetro são delimitados tarde.  
  
 A seguir está um exemplo da expressão de TOP da constante:  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 O seguinte é um exemplo de expressão TOP parametrized:  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 A TOP é não determinística a menos que a consulta é classificada. Se você precisar de um resultado determinístico, use o [ignorar](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) e [limite](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) subcláusulas no [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) cláusula. A TOP e os SKIP/LIMIT são mutuamente exclusivos.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa a TOP para especificar a uma linha superior a ser retornado do resultado da consulta. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## <a name="see-also"></a>Consulte também  
 [SELECIONE](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [IGNORAR](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [LIMITE](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [ORDENAR POR](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
