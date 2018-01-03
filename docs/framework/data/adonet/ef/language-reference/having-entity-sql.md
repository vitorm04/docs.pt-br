---
title: TENDO (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 92949205801e5bc498fdaaa67c2fa228140a2eb5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="having-entity-sql"></a>TENDO (Entity SQL)
Especifica um critério de pesquisa para um grupo ou uma agregação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Arguments  
 `search_condition`  
 Especifica o critério de pesquisa para o grupo ou a agregação encontre-se. Quando HAVING foi usado com GROUP BY ALL, a cláusula HAVING substitui ALL.  
  
## <a name="remarks"></a>Comentários  
 A cláusula HAVING é usada para especificar uma condição adicional de filtragem no resultado de um agrupamento. Se nenhum GRUPO é especificado pela cláusula a expressão de consulta, um único grupo implícito definido será adotado.  
  
> [!NOTE]
>  HAVING pode ser usado apenas com o [selecione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrução. Quando [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) não é usado, HAVING se comporta como uma cláusula WHERE.  
  
 A cláusula HAVING funciona como a cláusula WHERE exceto que são aplicados após a operação GROUP BY. Isso significa que a cláusula HAVING só pode fazer referências a agrupar alias e agregados, conforme ilustrado no exemplo a seguir.  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 O anterior restringe os grupos somente aquelas que incluem mais de um produto.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa HAVING e o GROUP BY operadores especificar um critério de pesquisa para um grupo ou uma agregação. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Expressões de Consulta](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
