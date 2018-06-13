---
title: LINHA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: eb5062399eec9d8453d8922e05698ca9124d94d7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765601"
---
# <a name="row-entity-sql"></a>LINHA (Entity SQL)
Constrói registros anônimos e tipados estruturalmente de um ou mais valores.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão de consulta válida que retorna um valor para construir em seguida o tipo.  
  
 `alias`  
 Especifica um alias para uma linha no tipo especificado valor. Se não for fornecido um alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta gerar um alias com base no [!INCLUDE[esql](../../../../../../includes/esql-md.md)] regras de geração de alias.  
  
## <a name="return-value"></a>Valor de retorno  
 Um tipo de linha.  
  
## <a name="remarks"></a>Comentários  
 Usar construtores de linha no [!INCLUDE[esql](../../../../../../includes/esql-md.md)] para construir estruturalmente tipados, anônimos registros de um ou mais valores. O tipo do resultado de um construtor de linha é um tipo de linha cujos tipos de campo correspondem aos tipos de valores que foram usados para construir a linha. Por exemplo, a expressão a seguir constrói um valor do tipo `Record(a int, b string, c int)`.  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 Se você não fornecer um alias para um construtor de expressão em seguida, Entity Framework tentará gerar um. Para obter mais informações, consulte a seção "Regras de alias" o [identificadores](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) tópico.  
  
 As seguintes regras se aplicam para o construtor de serrilha de expressão em uma linha:  
  
-   O construtor das expressões em uma linha não pode referenciar outras alias no mesmo construtor.  
  
-   Duas expressões no mesmo construtor de linha não podem ter as mesmas alias.  
  
 Para obter mais informações sobre os construtores de consulta, consulte [construindo tipos](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa o operador de LINHA para construir registros anônimos, estrutural tipados. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a>Consulte também  
 [Construindo tipos](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Definições de tipo](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
