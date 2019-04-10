---
title: MULTICONJUNTO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 44e411b8ae2f43bf3a729ac091ffd1eb4c462c63
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303031"
---
# <a name="multiset-entity-sql"></a>MULTICONJUNTO (Entity SQL)
Cria uma instância de um multiset de uma lista de valores. Todos os valores no construtor de MULTISET devem ser de um tipo compatível `T`. Não são permitidos construtores vazios de multiset.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Uma lista de valores válido.  
  
## <a name="return-value"></a>Valor de retorno  
 Uma coleção do tipo MULTISET\<T >.  
  
## <a name="remarks"></a>Comentários  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece três tipos dos construtores: construtores, construtores de objeto e construtores de multiset (ou a coleção) de linha. Para obter mais informações, consulte [construindo tipos](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
 O construtor de multiset cria uma instância de um multiset de uma lista de valores. Todos os valores no construtor devem ser de um tipo correspondente.  
  
 Por exemplo, a expressão a seguir cria um multiset de inteiros.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  Literais aninhados de multiset são suportados apenas quando um multiset de automática tem um único elemento de multiset; Por exemplo, `{{1, 2, 3}}`. Quando o multiset de automática tem vários elementos de multiset (por exemplo, `{{1, 2}, {3, 4}}`), não há suporte para literais de multiset aninhados.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa o operador de MULTISET para criar uma instância de um multiset de uma lista de valores. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>Consulte também

- [Construir tipos](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
