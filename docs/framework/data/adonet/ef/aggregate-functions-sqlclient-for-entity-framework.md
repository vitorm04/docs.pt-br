---
title: "Funções agregadas (SqlClient para Entity Framework)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 11779c07661edb8bfecda3b8ef955c35989294be
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Funções agregadas (SqlClient para Entity Framework)
O provedor de dados. NET Framework para SQL Server (SqlClient) fornece funções agregadas. Funções agregadas executam cálculos em um conjunto de valores de entrada e retornam um valor. Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient. A propriedade de namespace de um provedor permite que o Entity Framework descubra qual prefixo é usado por esse provedor para construções específicas, como tipos e funções.  
  
 A tabela a seguir mostra as funções agregadas SqlClient.  
  
|Função|Descrição|  
|--------------|-----------------|  
|`AVG(``expression``)`|Retorna a média dos valores em uma coleção.<br /><br /> Valores nulos são ignorados.<br /><br /> **Argumentos**<br /><br /> Um `Int32`, `Int64`, `Double`, e `Decimal`.<br /><br /> **Valor retornado**<br /><br /> O tipo de `expression`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]|  
|`CHECKSUM_AGG(``collection``)`|Retorna a soma de verificação dos valores em uma coleção.<br /><br /> Valores nulos são ignorados.<br /><br /> **Argumentos**<br /><br /> Uma coleção (`Int32`).<br /><br /> **Valor retornado**<br /><br /> Um `Int32`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]|  
|`COUNT(``expression``)`|Retorna o número de itens em uma coleção como `Int32`.<br /><br /> **Argumentos**<br /><br /> Uma coleção (T) onde T é um dos seguintes tipos:<br /><br /> `Guid` (não retornado no SQL Server 2000),<br /><br /> `Boolean`, `Double`, `DateTime`, `DateTimeOffset`, `Time`, `String`, ou `Binary`.<br /><br /> **Valor retornado**<br /><br /> Um `Int32`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]|  
|`COUNT_BIG(``expression``)`|Retorna o número de itens em uma coleção como `bigint`.<br /><br /> **Argumentos**<br /><br /> Uma coleção (T) onde T é um dos seguintes tipos:<br /><br /> `Guid` (não retornado no SQL Server 2000), `Boolean`, `Double`, `DateTime`, `DateTimeOffset`, `Time`, `String`, ou `Binary`.<br /><br /> **Valor retornado**<br /><br /> Um `Int64`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]|  
|`MAX(``expression``)`|Retorna o valor médio a coleção.<br /><br /> **Argumentos**<br /><br /> Uma coleção (T) onde T é um dos seguintes tipos: `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.<br /><br /> **Valor retornado**<br /><br /> O tipo de `expression`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]|  
|`MIN(``expression``)`|Retorna o valor médio em uma coleção.<br /><br /> **Argumentos**<br /><br /> Uma coleção (T) onde T é um dos seguintes tipos: `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`,<br /><br /> `Binary`.<br /><br /> **Valor retornado**<br /><br /> O tipo de `expression`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]|  
|`STDEV(``expression``)`|Retorna o desvio padrão estatístico de todos os valores na expressão especificada.<br /><br /> **Argumentos**<br /><br /> Uma coleção (`Double`).<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]|  
|`STDEVP(``expression``)`|Retorna o desvio padrão estatístico para a população para todos os valores na expressão especificada.<br /><br /> **Argumentos**<br /><br /> Uma coleção (`Double`).<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]|  
|`SUM(``expression``)`|Retorna a soma de todos os valores na coleção.<br /><br /> **Argumentos**<br /><br /> Uma coleção (T) onde T é um dos seguintes tipos: `Int32`, `Int64`, `Double`, `Decimal`.<br /><br /> **Valor retornado**<br /><br /> O tipo de `expression`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]|  
|`VAR(``expression``)`|Retorna a estatística variação de todos os valores na expressão especificada.<br /><br /> **Argumentos**<br /><br /> Uma coleção (`Double`).<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]|  
|`VARP(``expression``)`|Retorna a variação estatística para a população para todos os valores na expressão especificada.<br /><br /> **Argumentos**<br /><br /> Uma coleção (`Double`).<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]|  
  
 Para obter mais informações sobre funções agregadas que suporta SqlClient, consulte a documentação para a versão do SQL Server que você especificou no manifesto do provedor SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Funções de agregação (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115906)|[Funções de agregação (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=115903)|[Funções de agregação (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115907)|  
  
## <a name="see-also"></a>Consulte também  
 [Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) (Linguagem SQL de entidade)  
 [Funções canônicas agregadas](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
