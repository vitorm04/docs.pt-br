---
title: Funções agregadas (SqlClient para Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 55a10b82ffc189f5cf4118cb225a96963226256e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724181"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="501df-102">Funções agregadas (SqlClient para Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="501df-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="501df-103">O provedor de dados. NET Framework para SQL Server (SqlClient) fornece funções agregadas.</span><span class="sxs-lookup"><span data-stu-id="501df-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="501df-104">Funções agregadas executam cálculos em um conjunto de valores de entrada e retornam um valor.</span><span class="sxs-lookup"><span data-stu-id="501df-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="501df-105">Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="501df-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="501df-106">A propriedade de namespace de um provedor permite que o Entity Framework descubra qual prefixo é usado por esse provedor para construções específicas, como tipos e funções.</span><span class="sxs-lookup"><span data-stu-id="501df-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="501df-107">A seguir estão as funções agregadas SqlClient.</span><span class="sxs-lookup"><span data-stu-id="501df-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="501df-108">AVG(expression)</span><span class="sxs-lookup"><span data-stu-id="501df-108">AVG(expression)</span></span>

<span data-ttu-id="501df-109">Retorna a média dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="501df-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="501df-110">Valores nulos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="501df-110">Null values are ignored.</span></span>

<span data-ttu-id="501df-111">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="501df-111">**Arguments**</span></span>

<span data-ttu-id="501df-112">Uma `Int32`, `Int64`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="501df-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="501df-113">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="501df-113">**Return Value**</span></span>

<span data-ttu-id="501df-114">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="501df-114">The type of `expression`.</span></span>

<span data-ttu-id="501df-115">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="501df-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksumaggcollection"></a><span data-ttu-id="501df-116">CHECKSUM_AGG(Collection)</span><span class="sxs-lookup"><span data-stu-id="501df-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="501df-117">Retorna a soma de verificação dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="501df-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="501df-118">Valores nulos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="501df-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="501df-119">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="501df-119">**Arguments**</span></span>
 
 <span data-ttu-id="501df-120">Uma coleção (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="501df-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="501df-121">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="501df-121">**Return Value**</span></span>
 
 <span data-ttu-id="501df-122">Um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="501df-122">An `Int32`.</span></span>
 
 <span data-ttu-id="501df-123">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="501df-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="501df-124">Count(Expression)</span><span class="sxs-lookup"><span data-stu-id="501df-124">COUNT(expression)</span></span>

<span data-ttu-id="501df-125">Retorna o número de itens em uma coleção como `Int32`.</span><span class="sxs-lookup"><span data-stu-id="501df-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="501df-126">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="501df-126">**Arguments**</span></span>

<span data-ttu-id="501df-127">Uma coleção\<T >, onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="501df-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="501df-128">`Guid` (não retornado no SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="501df-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="501df-129">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="501df-129">**Return Value**</span></span>

<span data-ttu-id="501df-130">Um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="501df-130">An `Int32`.</span></span>

<span data-ttu-id="501df-131">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="501df-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="501df-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="501df-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="countbigexpression"></a><span data-ttu-id="501df-133">COUNT_BIG(expression)</span><span class="sxs-lookup"><span data-stu-id="501df-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="501df-134">Retorna o número de itens em uma coleção como `bigint`.</span><span class="sxs-lookup"><span data-stu-id="501df-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="501df-135">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="501df-135">**Arguments**</span></span>
 
 <span data-ttu-id="501df-136">Collection(T), onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="501df-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="501df-137">`Guid` (não retornado no SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="501df-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="501df-138">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="501df-138">**Return Value**</span></span>

<span data-ttu-id="501df-139">Um `Int64`.</span><span class="sxs-lookup"><span data-stu-id="501df-139">An `Int64`.</span></span>

<span data-ttu-id="501df-140">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="501df-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="501df-141">Max(Expression)</span><span class="sxs-lookup"><span data-stu-id="501df-141">MAX(expression)</span></span>

<span data-ttu-id="501df-142">Retorna o valor médio a coleção.</span><span class="sxs-lookup"><span data-stu-id="501df-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="501df-143">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="501df-143">**Arguments**</span></span>

<span data-ttu-id="501df-144">Collection(T), onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="501df-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="501df-145">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="501df-145">**Return Value**</span></span>

<span data-ttu-id="501df-146">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="501df-146">The type of `expression`.</span></span>

<span data-ttu-id="501df-147">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="501df-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="501df-148">MIN(expression)</span><span class="sxs-lookup"><span data-stu-id="501df-148">MIN(expression)</span></span>

<span data-ttu-id="501df-149">Retorna o valor médio em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="501df-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="501df-150">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="501df-150">**Arguments**</span></span>

<span data-ttu-id="501df-151">Collection(T), onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="501df-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="501df-152">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="501df-152">**Return Value**</span></span>

<span data-ttu-id="501df-153">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="501df-153">The type of `expression`.</span></span>

<span data-ttu-id="501df-154">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="501df-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="501df-155">STDEV(expression)</span><span class="sxs-lookup"><span data-stu-id="501df-155">STDEV(expression)</span></span>

<span data-ttu-id="501df-156">Retorna o desvio padrão estatístico de todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="501df-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="501df-157">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="501df-157">**Arguments**</span></span>

<span data-ttu-id="501df-158">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="501df-158">A Collection(`Double`).</span></span>

<span data-ttu-id="501df-159">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="501df-159">**Return Value**</span></span>

<span data-ttu-id="501df-160">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="501df-160">A `Double`.</span></span>

<span data-ttu-id="501df-161">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="501df-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="501df-162">STDEVP(expression)</span><span class="sxs-lookup"><span data-stu-id="501df-162">STDEVP(expression)</span></span>

<span data-ttu-id="501df-163">Retorna o desvio padrão estatístico para a população para todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="501df-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="501df-164">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="501df-164">**Arguments**</span></span>

<span data-ttu-id="501df-165">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="501df-165">A Collection(`Double`).</span></span>

<span data-ttu-id="501df-166">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="501df-166">**Return Value**</span></span>

<span data-ttu-id="501df-167">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="501df-167">A `Double`.</span></span>

<span data-ttu-id="501df-168">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="501df-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="501df-169">SUM(Expression)</span><span class="sxs-lookup"><span data-stu-id="501df-169">SUM(expression)</span></span>

<span data-ttu-id="501df-170">Retorna a soma de todos os valores na coleção.</span><span class="sxs-lookup"><span data-stu-id="501df-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="501df-171">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="501df-171">**Arguments**</span></span>

<span data-ttu-id="501df-172">Um Collection(T) onde T é um dos seguintes tipos: `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="501df-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="501df-173">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="501df-173">**Return Value**</span></span>

<span data-ttu-id="501df-174">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="501df-174">The type of `expression`.</span></span>

<span data-ttu-id="501df-175">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="501df-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="501df-176">VAR(expression)</span><span class="sxs-lookup"><span data-stu-id="501df-176">VAR(expression)</span></span>

<span data-ttu-id="501df-177">Retorna a estatística variação de todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="501df-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="501df-178">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="501df-178">**Arguments**</span></span>

<span data-ttu-id="501df-179">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="501df-179">A Collection(`Double`).</span></span>

<span data-ttu-id="501df-180">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="501df-180">**Return Value**</span></span>

<span data-ttu-id="501df-181">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="501df-181">A `Double`.</span></span>

<span data-ttu-id="501df-182">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="501df-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="501df-183">VARP(Expression)</span><span class="sxs-lookup"><span data-stu-id="501df-183">VARP(expression)</span></span>

<span data-ttu-id="501df-184">Retorna a variação estatística para a população para todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="501df-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="501df-185">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="501df-185">**Arguments**</span></span>

<span data-ttu-id="501df-186">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="501df-186">A Collection(`Double`).</span></span>

<span data-ttu-id="501df-187">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="501df-187">**Return Value**</span></span>

<span data-ttu-id="501df-188">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="501df-188">A `Double`.</span></span>

<span data-ttu-id="501df-189">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="501df-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="501df-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="501df-190">See also</span></span>

<span data-ttu-id="501df-191">Para obter mais informações sobre funções agregadas que suporta SqlClient, consulte a documentação para a versão do SQL Server que você especificou no manifesto do provedor SqlClient:</span><span class="sxs-lookup"><span data-stu-id="501df-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  

<span data-ttu-id="501df-192">**SQL Server 2005**: [Funções agregadas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="501df-192">**SQL Server 2005**: [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>  
<span data-ttu-id="501df-193">**SQL Server 2008 e posterior**:  [Funções agregadas (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="501df-193">**SQL Server 2008 and later**:  [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>  
- <span data-ttu-id="501df-194">[Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="501df-194">[Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)</span></span>
- [<span data-ttu-id="501df-195">Funções canônicas agregadas</span><span class="sxs-lookup"><span data-stu-id="501df-195">Aggregate Canonical Functions</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
