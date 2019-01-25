---
title: COLEÇÃO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: d4e52bb62412e61e1a71e0fe9a8555068ca18dbd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506453"
---
# <a name="collection-entity-sql"></a>COLEÇÃO (Entity SQL)
A palavra-chave de COLEÇÃO é usado somente na definição de uma função in-line. Funções de coleção são as funções que operam em um conjunto de valores e gerenciar uma saída escalares.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a>Arguments  
 `type_definition`  
 Uma expressão que retorna uma coleção de tipos suportados, de linhas, ou de referências.  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre a palavra-chave de COLEÇÃO, consulte [definições de tipo](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar a palavra-chave de COLEÇÃO para declarar uma coleção de decimais como um argumento para uma função in-line de consulta.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>Consulte também
- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
