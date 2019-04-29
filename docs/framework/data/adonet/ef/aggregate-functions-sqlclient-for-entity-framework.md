---
title: Funções agregadas (SqlClient para Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: f2f2b557cd9f126ddd513a0f42d3ac95114c3822
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606760"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="5666b-102">Funções agregadas (SqlClient para Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="5666b-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="5666b-103">O provedor de dados. NET Framework para SQL Server (SqlClient) fornece funções agregadas.</span><span class="sxs-lookup"><span data-stu-id="5666b-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="5666b-104">Funções agregadas executam cálculos em um conjunto de valores de entrada e retornam um valor.</span><span class="sxs-lookup"><span data-stu-id="5666b-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="5666b-105">Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="5666b-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="5666b-106">A propriedade de namespace de um provedor permite que o Entity Framework descubra qual prefixo é usado por esse provedor para construções específicas, como tipos e funções.</span><span class="sxs-lookup"><span data-stu-id="5666b-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="5666b-107">A seguir estão as funções agregadas SqlClient.</span><span class="sxs-lookup"><span data-stu-id="5666b-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="5666b-108">AVG(expression)</span><span class="sxs-lookup"><span data-stu-id="5666b-108">AVG(expression)</span></span>

<span data-ttu-id="5666b-109">Retorna a média dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="5666b-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="5666b-110">Valores nulos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="5666b-110">Null values are ignored.</span></span>

<span data-ttu-id="5666b-111">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="5666b-111">**Arguments**</span></span>

<span data-ttu-id="5666b-112">Uma `Int32`, `Int64`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="5666b-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="5666b-113">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="5666b-113">**Return Value**</span></span>

<span data-ttu-id="5666b-114">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="5666b-114">The type of `expression`.</span></span>

<span data-ttu-id="5666b-115">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="5666b-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksumaggcollection"></a><span data-ttu-id="5666b-116">CHECKSUM_AGG(Collection)</span><span class="sxs-lookup"><span data-stu-id="5666b-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="5666b-117">Retorna a soma de verificação dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="5666b-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="5666b-118">Valores nulos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="5666b-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="5666b-119">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="5666b-119">**Arguments**</span></span>
 
 <span data-ttu-id="5666b-120">Uma coleção (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="5666b-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="5666b-121">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="5666b-121">**Return Value**</span></span>
 
 <span data-ttu-id="5666b-122">Um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="5666b-122">An `Int32`.</span></span>
 
 <span data-ttu-id="5666b-123">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="5666b-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="5666b-124">Count(Expression)</span><span class="sxs-lookup"><span data-stu-id="5666b-124">COUNT(expression)</span></span>

<span data-ttu-id="5666b-125">Retorna o número de itens em uma coleção como `Int32`.</span><span class="sxs-lookup"><span data-stu-id="5666b-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="5666b-126">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="5666b-126">**Arguments**</span></span>

<span data-ttu-id="5666b-127">Uma coleção\<T >, onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="5666b-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="5666b-128">`Guid` (não retornado no SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="5666b-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="5666b-129">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="5666b-129">**Return Value**</span></span>

<span data-ttu-id="5666b-130">Um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="5666b-130">An `Int32`.</span></span>

<span data-ttu-id="5666b-131">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="5666b-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="5666b-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="5666b-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="countbigexpression"></a><span data-ttu-id="5666b-133">COUNT_BIG(expression)</span><span class="sxs-lookup"><span data-stu-id="5666b-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="5666b-134">Retorna o número de itens em uma coleção como `bigint`.</span><span class="sxs-lookup"><span data-stu-id="5666b-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="5666b-135">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="5666b-135">**Arguments**</span></span>
 
 <span data-ttu-id="5666b-136">Collection(T), onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="5666b-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="5666b-137">`Guid` (não retornado no SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="5666b-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="5666b-138">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="5666b-138">**Return Value**</span></span>

<span data-ttu-id="5666b-139">Um `Int64`.</span><span class="sxs-lookup"><span data-stu-id="5666b-139">An `Int64`.</span></span>

<span data-ttu-id="5666b-140">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="5666b-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="5666b-141">Max(Expression)</span><span class="sxs-lookup"><span data-stu-id="5666b-141">MAX(expression)</span></span>

<span data-ttu-id="5666b-142">Retorna o valor médio a coleção.</span><span class="sxs-lookup"><span data-stu-id="5666b-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="5666b-143">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="5666b-143">**Arguments**</span></span>

<span data-ttu-id="5666b-144">Collection(T), onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="5666b-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="5666b-145">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="5666b-145">**Return Value**</span></span>

<span data-ttu-id="5666b-146">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="5666b-146">The type of `expression`.</span></span>

<span data-ttu-id="5666b-147">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="5666b-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="5666b-148">MIN(expression)</span><span class="sxs-lookup"><span data-stu-id="5666b-148">MIN(expression)</span></span>

<span data-ttu-id="5666b-149">Retorna o valor médio em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="5666b-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="5666b-150">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="5666b-150">**Arguments**</span></span>

<span data-ttu-id="5666b-151">Collection(T), onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="5666b-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="5666b-152">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="5666b-152">**Return Value**</span></span>

<span data-ttu-id="5666b-153">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="5666b-153">The type of `expression`.</span></span>

<span data-ttu-id="5666b-154">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="5666b-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="5666b-155">STDEV(expression)</span><span class="sxs-lookup"><span data-stu-id="5666b-155">STDEV(expression)</span></span>

<span data-ttu-id="5666b-156">Retorna o desvio padrão estatístico de todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="5666b-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="5666b-157">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="5666b-157">**Arguments**</span></span>

<span data-ttu-id="5666b-158">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="5666b-158">A Collection(`Double`).</span></span>

<span data-ttu-id="5666b-159">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="5666b-159">**Return Value**</span></span>

<span data-ttu-id="5666b-160">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="5666b-160">A `Double`.</span></span>

<span data-ttu-id="5666b-161">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="5666b-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="5666b-162">STDEVP(expression)</span><span class="sxs-lookup"><span data-stu-id="5666b-162">STDEVP(expression)</span></span>

<span data-ttu-id="5666b-163">Retorna o desvio padrão estatístico para a população para todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="5666b-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="5666b-164">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="5666b-164">**Arguments**</span></span>

<span data-ttu-id="5666b-165">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="5666b-165">A Collection(`Double`).</span></span>

<span data-ttu-id="5666b-166">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="5666b-166">**Return Value**</span></span>

<span data-ttu-id="5666b-167">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="5666b-167">A `Double`.</span></span>

<span data-ttu-id="5666b-168">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="5666b-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="5666b-169">SUM(Expression)</span><span class="sxs-lookup"><span data-stu-id="5666b-169">SUM(expression)</span></span>

<span data-ttu-id="5666b-170">Retorna a soma de todos os valores na coleção.</span><span class="sxs-lookup"><span data-stu-id="5666b-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="5666b-171">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="5666b-171">**Arguments**</span></span>

<span data-ttu-id="5666b-172">Um Collection(T) onde T é um dos seguintes tipos: `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="5666b-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="5666b-173">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="5666b-173">**Return Value**</span></span>

<span data-ttu-id="5666b-174">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="5666b-174">The type of `expression`.</span></span>

<span data-ttu-id="5666b-175">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="5666b-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="5666b-176">VAR(expression)</span><span class="sxs-lookup"><span data-stu-id="5666b-176">VAR(expression)</span></span>

<span data-ttu-id="5666b-177">Retorna a estatística variação de todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="5666b-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="5666b-178">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="5666b-178">**Arguments**</span></span>

<span data-ttu-id="5666b-179">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="5666b-179">A Collection(`Double`).</span></span>

<span data-ttu-id="5666b-180">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="5666b-180">**Return Value**</span></span>

<span data-ttu-id="5666b-181">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="5666b-181">A `Double`.</span></span>

<span data-ttu-id="5666b-182">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="5666b-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="5666b-183">VARP(Expression)</span><span class="sxs-lookup"><span data-stu-id="5666b-183">VARP(expression)</span></span>

<span data-ttu-id="5666b-184">Retorna a variação estatística para a população para todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="5666b-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="5666b-185">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="5666b-185">**Arguments**</span></span>

<span data-ttu-id="5666b-186">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="5666b-186">A Collection(`Double`).</span></span>

<span data-ttu-id="5666b-187">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="5666b-187">**Return Value**</span></span>

<span data-ttu-id="5666b-188">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="5666b-188">A `Double`.</span></span>

<span data-ttu-id="5666b-189">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="5666b-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="5666b-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5666b-190">See also</span></span>

<span data-ttu-id="5666b-191">Para obter mais informações sobre funções agregadas que suporta SqlClient, consulte a documentação para a versão do SQL Server que você especificou no manifesto do provedor SqlClient:</span><span class="sxs-lookup"><span data-stu-id="5666b-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="5666b-192">**SQL Server 2005:** [Funções agregadas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="5666b-192">**SQL Server 2005:** [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>
- <span data-ttu-id="5666b-193">**SQL Server 2008 e posterior:** [Funções agregadas (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="5666b-193">**SQL Server 2008 and later:** [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>

- <span data-ttu-id="5666b-194">[Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="5666b-194">[Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)</span></span>
- [<span data-ttu-id="5666b-195">Funções canônicas agregadas</span><span class="sxs-lookup"><span data-stu-id="5666b-195">Aggregate Canonical Functions</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
