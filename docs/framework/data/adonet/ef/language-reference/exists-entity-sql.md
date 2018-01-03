---
title: EXISTE (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0807be69419465a3d79f162e9738361a6ce8051a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="exists-entity-sql"></a>EXISTE (Entity SQL)
Determina se uma coleção está vazia.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão válida que retorna uma coleção.  
  
 NOT  
 Especifica que o resultado EXISTS seja negado.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` se a coleção é não vazio; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 EXISTS é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita. Para obter informações de precedência para o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operadores de conjunto, consulte [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa EXISTE operador para determinar se a coleção está vazia. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
