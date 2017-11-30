---
title: CHAVE (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ccc13599889eb91755c775600f2386d1812880b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="key-entity-sql"></a>CHAVE (Entity SQL)
Extraia a chave de uma referência ou uma expressão de entidade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Comentários  
 Uma chave de entidade contém os valores chave na ordem correta de entidade ou de referência de entidade especificada. Porque os vários conjuntos de entidades podem ser baseados no mesmo tipo, a mesma chave pode aparecer em cada conjunto de entidades. Para obter uma referência única, use `REF`. O tipo de retorno de operador- de CHAVE é um tipo da linha que inclui um campo para cada tecla de entidade, na mesma ordem.  
  
 No exemplo a seguir, o operador- de chave é passado uma referência para a entidade de BadOrder, e retorna a parte principal da referência. Nesse caso, um tipo de registro com o exatamente um campo que corresponde à propriedade de `Id` .  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa o operador- de CHAVE para extrair a parte principal de uma expressão com referência de tipo. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
