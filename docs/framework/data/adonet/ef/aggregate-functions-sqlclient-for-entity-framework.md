---
title: Funções agregadas (SqlClient para Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: cf476192cf049f230c1956e390d215ad4abaa821
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251702"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="9233a-102">Funções agregadas (SqlClient para Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="9233a-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="9233a-103">O provedor de dados. NET Framework para SQL Server (SqlClient) fornece funções agregadas.</span><span class="sxs-lookup"><span data-stu-id="9233a-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="9233a-104">Funções agregadas executam cálculos em um conjunto de valores de entrada e retornam um valor.</span><span class="sxs-lookup"><span data-stu-id="9233a-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="9233a-105">Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="9233a-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="9233a-106">A propriedade de namespace de um provedor permite que o Entity Framework descubra qual prefixo é usado por esse provedor para construções específicas, como tipos e funções.</span><span class="sxs-lookup"><span data-stu-id="9233a-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="9233a-107">A seguir estão as funções de agregação SqlClient.</span><span class="sxs-lookup"><span data-stu-id="9233a-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="9233a-108">AVG (expressão)</span><span class="sxs-lookup"><span data-stu-id="9233a-108">AVG(expression)</span></span>

<span data-ttu-id="9233a-109">Retorna a média dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="9233a-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="9233a-110">Valores nulos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="9233a-110">Null values are ignored.</span></span>

<span data-ttu-id="9233a-111">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9233a-111">**Arguments**</span></span>

<span data-ttu-id="9233a-112">Um `Int32`, `Int64`, e`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="9233a-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="9233a-113">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9233a-113">**Return Value**</span></span>

<span data-ttu-id="9233a-114">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="9233a-114">The type of `expression`.</span></span>

<span data-ttu-id="9233a-115">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9233a-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="9233a-116">CHECKSUM_AGG (coleção)</span><span class="sxs-lookup"><span data-stu-id="9233a-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="9233a-117">Retorna a soma de verificação dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="9233a-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="9233a-118">Valores nulos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="9233a-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="9233a-119">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9233a-119">**Arguments**</span></span>
 
 <span data-ttu-id="9233a-120">Uma coleção (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="9233a-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="9233a-121">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9233a-121">**Return Value**</span></span>
 
 <span data-ttu-id="9233a-122">Um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="9233a-122">An `Int32`.</span></span>
 
 <span data-ttu-id="9233a-123">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9233a-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="9233a-124">CONTAGEM (expressão)</span><span class="sxs-lookup"><span data-stu-id="9233a-124">COUNT(expression)</span></span>

<span data-ttu-id="9233a-125">Retorna o número de itens em uma coleção como `Int32`.</span><span class="sxs-lookup"><span data-stu-id="9233a-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="9233a-126">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9233a-126">**Arguments**</span></span>

<span data-ttu-id="9233a-127">Uma coleção\<t >, em que t é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="9233a-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="9233a-128">`Guid`(não retornado em SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="9233a-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="9233a-129">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9233a-129">**Return Value**</span></span>

<span data-ttu-id="9233a-130">Um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="9233a-130">An `Int32`.</span></span>

<span data-ttu-id="9233a-131">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9233a-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="9233a-132">[! Code-SQL[PD entityservices Concepts # SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="9233a-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="count_bigexpression"></a><span data-ttu-id="9233a-133">COUNT_BIG (expressão)</span><span class="sxs-lookup"><span data-stu-id="9233a-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="9233a-134">Retorna o número de itens em uma coleção como `bigint`.</span><span class="sxs-lookup"><span data-stu-id="9233a-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="9233a-135">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9233a-135">**Arguments**</span></span>
 
 <span data-ttu-id="9233a-136">Uma coleção (T), em que T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="9233a-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="9233a-137">`Guid`(não retornado em SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="9233a-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="9233a-138">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9233a-138">**Return Value**</span></span>

<span data-ttu-id="9233a-139">Um `Int64`.</span><span class="sxs-lookup"><span data-stu-id="9233a-139">An `Int64`.</span></span>

<span data-ttu-id="9233a-140">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9233a-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="9233a-141">MAX (expressão)</span><span class="sxs-lookup"><span data-stu-id="9233a-141">MAX(expression)</span></span>

<span data-ttu-id="9233a-142">Retorna o valor médio a coleção.</span><span class="sxs-lookup"><span data-stu-id="9233a-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="9233a-143">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9233a-143">**Arguments**</span></span>

<span data-ttu-id="9233a-144">Uma coleção (T), em que T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="9233a-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="9233a-145">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9233a-145">**Return Value**</span></span>

<span data-ttu-id="9233a-146">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="9233a-146">The type of `expression`.</span></span>

<span data-ttu-id="9233a-147">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9233a-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="9233a-148">MIN (expressão)</span><span class="sxs-lookup"><span data-stu-id="9233a-148">MIN(expression)</span></span>

<span data-ttu-id="9233a-149">Retorna o valor médio em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="9233a-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="9233a-150">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9233a-150">**Arguments**</span></span>

<span data-ttu-id="9233a-151">Uma coleção (T), em que T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="9233a-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="9233a-152">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9233a-152">**Return Value**</span></span>

<span data-ttu-id="9233a-153">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="9233a-153">The type of `expression`.</span></span>

<span data-ttu-id="9233a-154">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9233a-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="9233a-155">DESVPAD (expressão)</span><span class="sxs-lookup"><span data-stu-id="9233a-155">STDEV(expression)</span></span>

<span data-ttu-id="9233a-156">Retorna o desvio padrão estatístico de todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9233a-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="9233a-157">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9233a-157">**Arguments**</span></span>

<span data-ttu-id="9233a-158">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="9233a-158">A Collection(`Double`).</span></span>

<span data-ttu-id="9233a-159">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9233a-159">**Return Value**</span></span>

<span data-ttu-id="9233a-160">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9233a-160">A `Double`.</span></span>

<span data-ttu-id="9233a-161">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9233a-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="9233a-162">DESVPADP (expressão)</span><span class="sxs-lookup"><span data-stu-id="9233a-162">STDEVP(expression)</span></span>

<span data-ttu-id="9233a-163">Retorna o desvio padrão estatístico para a população para todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9233a-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="9233a-164">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9233a-164">**Arguments**</span></span>

<span data-ttu-id="9233a-165">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="9233a-165">A Collection(`Double`).</span></span>

<span data-ttu-id="9233a-166">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9233a-166">**Return Value**</span></span>

<span data-ttu-id="9233a-167">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9233a-167">A `Double`.</span></span>

<span data-ttu-id="9233a-168">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9233a-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="9233a-169">SUM (expressão)</span><span class="sxs-lookup"><span data-stu-id="9233a-169">SUM(expression)</span></span>

<span data-ttu-id="9233a-170">Retorna a soma de todos os valores na coleção.</span><span class="sxs-lookup"><span data-stu-id="9233a-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="9233a-171">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9233a-171">**Arguments**</span></span>

<span data-ttu-id="9233a-172">Uma coleção ( `Int32`T) `Double`, em que T é um dos seguintes tipos: `Int64`,, `Decimal`,.</span><span class="sxs-lookup"><span data-stu-id="9233a-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="9233a-173">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9233a-173">**Return Value**</span></span>

<span data-ttu-id="9233a-174">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="9233a-174">The type of `expression`.</span></span>

<span data-ttu-id="9233a-175">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9233a-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="9233a-176">VAR (expressão)</span><span class="sxs-lookup"><span data-stu-id="9233a-176">VAR(expression)</span></span>

<span data-ttu-id="9233a-177">Retorna a estatística variação de todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9233a-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="9233a-178">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9233a-178">**Arguments**</span></span>

<span data-ttu-id="9233a-179">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="9233a-179">A Collection(`Double`).</span></span>

<span data-ttu-id="9233a-180">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9233a-180">**Return Value**</span></span>

<span data-ttu-id="9233a-181">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9233a-181">A `Double`.</span></span>

<span data-ttu-id="9233a-182">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9233a-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="9233a-183">VARP (expressão)</span><span class="sxs-lookup"><span data-stu-id="9233a-183">VARP(expression)</span></span>

<span data-ttu-id="9233a-184">Retorna a variação estatística para a população para todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9233a-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="9233a-185">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9233a-185">**Arguments**</span></span>

<span data-ttu-id="9233a-186">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="9233a-186">A Collection(`Double`).</span></span>

<span data-ttu-id="9233a-187">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9233a-187">**Return Value**</span></span>

<span data-ttu-id="9233a-188">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9233a-188">A `Double`.</span></span>

<span data-ttu-id="9233a-189">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9233a-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="9233a-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9233a-190">See also</span></span>

<span data-ttu-id="9233a-191">Para obter mais informações sobre funções agregadas que suporta SqlClient, consulte a documentação para a versão do SQL Server que você especificou no manifesto do provedor SqlClient:</span><span class="sxs-lookup"><span data-stu-id="9233a-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="9233a-192">**SQL Server 2005:** [Funções de agregação (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="9233a-192">**SQL Server 2005:** [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>
- <span data-ttu-id="9233a-193">**SQL Server 2008 e posterior:** [Funções de agregação (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="9233a-193">**SQL Server 2008 and later:** [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>

- <span data-ttu-id="9233a-194">[Entity SQL Language](./language-reference/entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="9233a-194">[Entity SQL Language](./language-reference/entity-sql-language.md)</span></span>
- [<span data-ttu-id="9233a-195">Funções canônicas agregadas</span><span class="sxs-lookup"><span data-stu-id="9233a-195">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
