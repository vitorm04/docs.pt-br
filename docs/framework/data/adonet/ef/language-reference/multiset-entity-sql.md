---
title: MULTICONJUNTO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: a81787da9ee1af084a903dcb50b024f3d26d18fc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175688"
---
# <a name="multiset-entity-sql"></a>MULTICONJUNTO (Entity SQL)

Cria uma instância de um multiset de uma lista de valores. Todos os valores no Construtor multiconjunto devem ser de um tipo compatível `T` . Não são permitidos construtores vazios de multiset.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
MULTISET ( expression [{, expression }] )  
-- or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>Argumentos  

 `expression`  
 Uma lista de valores válido.  
  
## <a name="return-value"></a>Valor Retornado  

 Uma coleção do tipo multiconjunto \<T> .  
  
## <a name="remarks"></a>Comentários  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece três tipos de construtores: construtores de linha, construtores de objeto e construtores de vários conjuntos (ou de coleção). Para obter mais informações, consulte [construindo tipos](constructing-types-entity-sql.md).  
  
 O construtor de multiset cria uma instância de um multiset de uma lista de valores. Todos os valores no construtor devem ser de um tipo correspondente.  
  
 Por exemplo, a expressão a seguir cria um multiset de inteiros.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> Literais multiconjuntos aninhados só têm suporte quando um encapsulamento multiconjunto tem um único elemento multiconjunto; por exemplo, `{{1, 2, 3}}` . Quando o encapsulamento multiconjunto tem vários elementos multiconjunto (por exemplo, `{{1, 2}, {3, 4}}` ), literais aninhados multiconjuntos não têm suporte.  
  
## <a name="example"></a>Exemplo  

 A seguinte consulta SQL Entity usa o operador de MULTISET para criar uma instância de um multiset de uma lista de valores. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#MULTISET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiset)]  
  
## <a name="see-also"></a>Confira também

- [Construir tipos](constructing-types-entity-sql.md)
- [Referência de Entity SQL](entity-sql-reference.md)
