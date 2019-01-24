---
title: CHAVE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 68ee7d512e0a3b5d912dc12c55be6f0135129225
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509192"
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
  
1.  Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a>Consulte também
- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
