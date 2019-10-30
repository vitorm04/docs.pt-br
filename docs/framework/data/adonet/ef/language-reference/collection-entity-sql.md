---
title: COLEÇÃO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 5a1af1aab8a084b19e48fbdbb159d7ddd8a8dd7c
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039902"
---
# <a name="collection-entity-sql"></a>COLEÇÃO (Entity SQL)
A palavra-chave de COLEÇÃO é usado somente na definição de uma função in-line. Funções de coleção são as funções que operam em um conjunto de valores e gerenciar uma saída escalares.  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp  
COLLECTION(type_definition)
```  
  
## <a name="arguments"></a>Arguments  
 `type_definition`  
 Uma expressão que retorna uma coleção de tipos suportados, de linhas, ou de referências.  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre a palavra-chave COLLECTION, consulte [definições de tipo](type-definitions-entity-sql.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar a palavra-chave de COLEÇÃO para declarar uma coleção de decimais como um argumento para uma função in-line de consulta.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
