---
title: ACHATAR (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 467277a1697f9f6ca4da7278045cbec34202eed5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="flatten-entity-sql"></a>ACHATAR (Entity SQL)
Converte uma coleção de coleções em uma coleção combinada. A nova coleção contém todos os mesmos elementos que a coleção antiga, mas sem uma estrutura aninhada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a>Arguments  
 `collection`  
 Qualquer expressão válida que retorna uma coleção de coleções valor de ajuste em uma única coleção.  
  
## <a name="remarks"></a>Comentários  
 `FLATTEN` é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita. Consulte [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) para obter informações de precedência para o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operadores de conjunto.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa o operador de `FLATTEN` para converter uma coleção das coleções em uma coleção aplainada. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
