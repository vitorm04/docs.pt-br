---
title: Funções agregadas (SqlClient para Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1fad25f2229b4fa810cf82a96dcb8c50a9de3070
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150643"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Funções agregadas (SqlClient para Entity Framework)
O provedor de dados. NET Framework para SQL Server (SqlClient) fornece funções agregadas. Funções agregadas executam cálculos em um conjunto de valores de entrada e retornam um valor. Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient. A propriedade de namespace de um provedor permite que o Entity Framework descubra qual prefixo é usado por esse provedor para construções específicas, como tipos e funções.  
  
 A seguir estão as funções agregadas sqlClient.  

## <a name="avgexpression"></a>AVG(expressão)

Retorna a média dos valores em uma coleção. Valores nulos são ignorados.

**Argumentos**

Um `Int32` `Int64`, `Double`, `Decimal`e .

**Valor de Retorno**

O tipo de `expression`.

**Exemplo**

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a>CHECKSUM_AGG(coleção)

 Retorna a soma de verificação dos valores em uma coleção. Valores nulos são ignorados.

 **Argumentos**

 Uma Coleção.`Int32`

 **Valor de Retorno**

 Um `Int32`.

 **Exemplo**

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a>CONTAGEM (expressão)

Retorna o número de itens em uma coleção como `Int32`.

**Argumentos**

Uma\<coleção T>, onde T é um dos seguintes tipos:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid`(não retornado no SQL Server 2000)|

**Valor de Retorno**

Um `Int32`.

**Exemplo**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a>COUNT_BIG(expressão)

Retorna o número de itens em uma coleção como `bigint`.

 **Argumentos**

 Uma Coleção(T), onde T é um dos seguintes tipos:

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid`(não retornado no SQL Server 2000)|

**Valor de Retorno**

Um `Int64`.

**Exemplo**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a>MAX (expressão)

Retorna o valor médio a coleção.

**Argumentos**

Uma Coleção(T), onde T é um dos seguintes tipos:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Valor de Retorno**

O tipo de `expression`.

**Exemplo**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a>MIN (expressão)

Retorna o valor médio em uma coleção.

**Argumentos**

Uma Coleção(T), onde T é um dos seguintes tipos:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Valor de Retorno**

O tipo de `expression`.

**Exemplo**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>STDEV(expressão)

Retorna o desvio padrão estatístico de todos os valores da expressão especificada.

**Argumentos**

Uma Coleção.`Double`

**Valor de Retorno**

Um `Double`.

**Exemplo**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>STDEVP (expressão)

Retorna o desvio padrão estatístico para a população de todos os valores na expressão especificada.

**Argumentos**

Uma Coleção.`Double`

**Valor de Retorno**

Um `Double`.

**Exemplo**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SOMA (expressão)

Retorna a soma de todos os valores na coleção.

**Argumentos**

Uma Coleção(T) onde T é um `Int32` `Int64`dos `Double` `Decimal`seguintes tipos: , , . .

**Valor de Retorno**

O tipo de `expression`.

**Exemplo**

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR (expressão)

Retorna a variância estatística de todos os valores da expressão especificada.

**Argumentos**

Uma Coleção.`Double`

**Valor de Retorno**

Um `Double`.

**Exemplo**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>VARP (expressão)

Retorna a variância estatística para o preenchimento de todos os valores da expressão especificada.

**Argumentos**

Uma Coleção.`Double`

**Valor de Retorno**

Um `Double`.

**Exemplo**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a>Confira também

- [Funções de agregação (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [Entity SQL Language](./language-reference/entity-sql-language.md) (Linguagem SQL de entidade)
- [Funções agregadas canônicas](./language-reference/aggregate-canonical-functions.md)
