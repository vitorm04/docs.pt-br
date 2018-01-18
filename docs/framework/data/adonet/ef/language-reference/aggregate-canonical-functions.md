---
title: "Funções agregadas canônicas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4539d73479ed05111f0d59b56403fd98bd311f61
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="aggregate-canonical-functions"></a>Funções agregadas canônicas

Agregados são as expressões em que reduz uma série de valores de entrada, por exemplo, um único valor. Agregados são normalmente usadas em conjunto com o cláusula GROUP BY de expressão SELECT, e há restrições em onde eles podem ser usados.

A tabela a seguir mostra a [!INCLUDE[esql](../../../../../../includes/esql-md.md)] agregado funções canônicas.

| Função | Descrição |
| -------- | ----------- |
| `Avg(expression)` | Retorna a média dos valores não anuláveis.<br><br>**Argumentos**<br><br>Um `Int32`, `Int64`, `Double`, e `Decimal`.<br><br>**Valor retornado**<br><br>O tipo de `expression`. `Null`, se todos os valores de entrada são valores de `null` .<br><br>**Exemplo** [!code-csharp [DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)][!code-sql[DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)] |
| `BigCount(expression)` | Retorna o tamanho do agregado que inclui valores nulos e duplicados.<br><br>**Argumentos**<br><br>Qualquer tipo.<br><br>**Valor retornado**<br><br>Um `Int64`.<br><br>**Exemplo** [!code-csharp [DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)][!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)] |
| `Count(expression)` | Retorna o tamanho do agregado que inclui valores nulos e duplicados.<br><br>**Argumentos**<br><br>Qualquer tipo.<br><br>**Valor retornado**<br><br>Um `Int32`.<br><br>**Exemplo** [!code-csharp [DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)][!code-sql[DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)] |
| `Max(expression)` | Retorna o máximo dos valores não anuláveis.<br><br>**Argumentos**<br><br>`Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.<br><br>**Valor retornado**<br><br>O tipo de `expression`. `Null`, se todos os valores de entrada são valores de `null` .<br><br>**Exemplo** [!code-csharp [DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)][!code-sql[DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)] |
| `Min(expression)` | Retorna o mínimo dos valores não anuláveis.<br><br>**Argumentos**<br><br>`Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.<br><br>**Valor retornado**<br><br>O tipo de `expression`. `Null`, se todos os valores de entrada são valores de `null` .<br><br>**Exemplo** [!code-csharp [DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)][!code-sql[DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)] |
| `StDev(expression)` | Retorna o desvio padrão de valores não anuláveis.<br><br>**Argumentos**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Valor retornado**<br><br>Um `Double`. `Null`, se todos os valores de entrada são valores de `null` .<br><br>**Exemplo** [!code-csharp [DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)][!code-sql[DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)] |
| `StDevP(expression)` | Retorna o desvio padrão para a população de todos os valores.<br><br>**Argumentos**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Valor retornado**<br><br>Um `Double`. `Null`, se todos os valores de entrada são valores de `null` .<br><br>**Exemplo** [!code-csharp [DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)][!code-sql[DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)] |
| `Sum(expression)` | Retorna a soma dos valores não anuláveis.<br><br>**Argumentos**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Valor retornado**<br><br>Um `Double`. `Null`, se todos os valores de entrada são valores de `null` .<br><br>**Exemplo** [!code-csharp [DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)][!code-sql[DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)] |
| `Var(expression)` | Retorna a variação de todos os valores não anuláveis.<br><br>**Argumentos**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Valor retornado**<br><br>Um `Double`. `Null`, se todos os valores de entrada são valores de `null` .<br><br>**Exemplo** [!code-csharp [DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)][!code-sql[DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)] |
| `VarP(expression)` | Retorna a variação para a população de todos os valores não anuláveis.<br><br>**Argumentos**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Valor retornado**<br><br>Um `Double`. `Null`, se todos os valores de entrada são valores de `null` .<br><br>**Exemplo** [!code-csharp [DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)][!code-sql[DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)] |

Funcionalidade equivalente está disponível no provedor gerenciado cliente do Microsoft SQL. Para obter mais informações, consulte [SqlClient para funções de Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).

## <a name="collection-based-aggregates"></a>Agregações de coleção

Agregados coleção com base (funções de coleção) operam em coleções e retornam um valor. Por exemplo se pedidos é uma coleção de todos os pedidos, você pode calcular a data de remessa com a seguinte expressão:

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

Agregados coleções baseadas dentro de expressões são avaliadas dentro do escopo ambiente atual de resolução.

## <a name="group-based-aggregates"></a>Agregações com base em grupo

Agregados Grupo- com base são calculadas sobre um grupo como definidas por cláusula GROUP BY. Para cada grupo em resultado, uma agregação separada é calculada usando elementos em cada grupo como entrada ao cálculo agregado. Quando a grupo- pela cláusula é usado em uma expressão selecionar, simplesmente agrupamento nomes de expressão, agregados, ou expressões constantes podem acessar estar presente na projeção ou ordem- pela cláusula.

O exemplo a seguir calcula a média quantidade ordenada para cada produto:

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol 
  group by ol.Product as p
```

É possível ter uma agregação baseado em grupos sem uma cláusula group-by explícita na expressão SELECT. Nesse caso, todos os elementos são tratados como um único grupo. Isso é equivalente a especificar um agrupamento com base em uma constante. Tomada, por exemplo, a expressão a seguir:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

Isso é equivalente ao seguinte:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

As expressões na agregação grupo- base são avaliadas dentro do escopo de resolução que seria visível para a cláusula WHERE expressão.

Como em [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], agregações de grupo também podem especificar todos ou modificador distinto. Se o modificador DISTINCT é especificado, as duplicatas são eliminadas de coleção de entrada aggregate, antes que a agregação é calculada apenas. Se TODOS OS modificador é especificado (ou se nenhum modificador é especificado), nenhuma descarte duplicado é executada.  

## <a name="see-also"></a>Consulte também

[Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) (Funções canônicas)
