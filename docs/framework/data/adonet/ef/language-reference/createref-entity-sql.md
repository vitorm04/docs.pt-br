---
title: CRIARREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: cbaea82108dd3debcca972ca15dea248227330ac
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251112"
---
# <a name="createref-entity-sql"></a>CRIARREF (Entity SQL)
Fabrica referências a uma entidade em um entityset.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 `entityset_identifier`  
 O identificador de entityset, não um literal de cadeia de caracteres.  
  
 `row_typed_expression`  
 Uma expressão linha tipada que corresponde a propriedades chave do tipo de objeto.  
  
## <a name="remarks"></a>Comentários  
 `row_typed_expression` deve ser estrutural equivalente ao tipo principal para a entidade. Isto é, deve ter o mesmo número e tipos de campos na mesma ordem como as chaves de entidade.  
  
 No exemplo abaixo, os pedidos e BadOrders são ambos os entitysets ordem de tipo, e é a identificação assumida para ser a única propriedade de chave pedido. O exemplo ilustra como nós podemos gerar uma referência a uma entidade em BadOrders. Observe que a referência pode oscilar.  Isto é, a referência não pode realmente identificar uma entidade específica. Nesses casos, uma operação de `DEREF` na referência retorna um zero.  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa o operador de CREATEREF para fabricar referências a uma entidade em um conjunto de entidades. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como: Executar uma consulta que retorna resultados](../how-to-execute-a-query-that-returns-structuraltype-results.md)de estruturaistype.  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
- [DEREF](deref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [REF](ref-entity-sql.md)
