---
title: Funções agregadas (SqlClient para Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 8ed9a58da9914724fe312876d6594cb526f2e0e9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452893"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="89bcf-102">Funções agregadas (SqlClient para Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="89bcf-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="89bcf-103">O provedor de dados. NET Framework para SQL Server (SqlClient) fornece funções agregadas.</span><span class="sxs-lookup"><span data-stu-id="89bcf-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="89bcf-104">Funções agregadas executam cálculos em um conjunto de valores de entrada e retornam um valor.</span><span class="sxs-lookup"><span data-stu-id="89bcf-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="89bcf-105">Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="89bcf-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="89bcf-106">A propriedade de namespace de um provedor permite que o Entity Framework descubra qual prefixo é usado por esse provedor para construções específicas, como tipos e funções.</span><span class="sxs-lookup"><span data-stu-id="89bcf-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="89bcf-107">A seguir estão as funções agregadas SqlClient.</span><span class="sxs-lookup"><span data-stu-id="89bcf-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="89bcf-108">Avg(Expression)</span><span class="sxs-lookup"><span data-stu-id="89bcf-108">AVG(expression)</span></span>

<span data-ttu-id="89bcf-109">Retorna a média dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="89bcf-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="89bcf-110">Valores nulos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="89bcf-110">Null values are ignored.</span></span>

<span data-ttu-id="89bcf-111">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="89bcf-111">**Arguments**</span></span>

<span data-ttu-id="89bcf-112">Uma `Int32`, `Int64`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="89bcf-113">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="89bcf-113">**Return Value**</span></span>

<span data-ttu-id="89bcf-114">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-114">The type of `expression`.</span></span>

<span data-ttu-id="89bcf-115">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="89bcf-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksumaggcollection"></a><span data-ttu-id="89bcf-116">CHECKSUM_AGG(Collection)</span><span class="sxs-lookup"><span data-stu-id="89bcf-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="89bcf-117">Retorna a soma de verificação dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="89bcf-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="89bcf-118">Valores nulos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="89bcf-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="89bcf-119">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="89bcf-119">**Arguments**</span></span>
 
 <span data-ttu-id="89bcf-120">Uma coleção (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="89bcf-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="89bcf-121">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="89bcf-121">**Return Value**</span></span>
 
 <span data-ttu-id="89bcf-122">Um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-122">An `Int32`.</span></span>
 
 <span data-ttu-id="89bcf-123">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="89bcf-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="89bcf-124">Count(Expression)</span><span class="sxs-lookup"><span data-stu-id="89bcf-124">COUNT(expression)</span></span>

<span data-ttu-id="89bcf-125">Retorna o número de itens em uma coleção como `Int32`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="89bcf-126">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="89bcf-126">**Arguments**</span></span>

<span data-ttu-id="89bcf-127">Uma coleção\<T >, onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="89bcf-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="89bcf-128">`Guid` (não retornado no SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="89bcf-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="89bcf-129">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="89bcf-129">**Return Value**</span></span>

<span data-ttu-id="89bcf-130">Um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-130">An `Int32`.</span></span>

<span data-ttu-id="89bcf-131">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="89bcf-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="89bcf-132">[! código sql[DP EntityServices conceitos #SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="89bcf-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="countbigexpression"></a><span data-ttu-id="89bcf-133">COUNT_BIG(Expression)</span><span class="sxs-lookup"><span data-stu-id="89bcf-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="89bcf-134">Retorna o número de itens em uma coleção como `bigint`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="89bcf-135">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="89bcf-135">**Arguments**</span></span>
 
 <span data-ttu-id="89bcf-136">Collection(T), onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="89bcf-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="89bcf-137">`Guid` (não retornado no SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="89bcf-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="89bcf-138">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="89bcf-138">**Return Value**</span></span>

<span data-ttu-id="89bcf-139">Um `Int64`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-139">An `Int64`.</span></span>

<span data-ttu-id="89bcf-140">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="89bcf-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="89bcf-141">Max(Expression)</span><span class="sxs-lookup"><span data-stu-id="89bcf-141">MAX(expression)</span></span>

<span data-ttu-id="89bcf-142">Retorna o valor médio a coleção.</span><span class="sxs-lookup"><span data-stu-id="89bcf-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="89bcf-143">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="89bcf-143">**Arguments**</span></span>

<span data-ttu-id="89bcf-144">Collection(T), onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="89bcf-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="89bcf-145">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="89bcf-145">**Return Value**</span></span>

<span data-ttu-id="89bcf-146">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-146">The type of `expression`.</span></span>

<span data-ttu-id="89bcf-147">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="89bcf-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="89bcf-148">MIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="89bcf-148">MIN(expression)</span></span>

<span data-ttu-id="89bcf-149">Retorna o valor médio em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="89bcf-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="89bcf-150">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="89bcf-150">**Arguments**</span></span>

<span data-ttu-id="89bcf-151">Collection(T), onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="89bcf-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="89bcf-152">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="89bcf-152">**Return Value**</span></span>

<span data-ttu-id="89bcf-153">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-153">The type of `expression`.</span></span>

<span data-ttu-id="89bcf-154">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="89bcf-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="89bcf-155">StDev(Expression)</span><span class="sxs-lookup"><span data-stu-id="89bcf-155">STDEV(expression)</span></span>

<span data-ttu-id="89bcf-156">Retorna o desvio padrão estatístico de todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="89bcf-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="89bcf-157">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="89bcf-157">**Arguments**</span></span>

<span data-ttu-id="89bcf-158">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="89bcf-158">A Collection(`Double`).</span></span>

<span data-ttu-id="89bcf-159">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="89bcf-159">**Return Value**</span></span>

<span data-ttu-id="89bcf-160">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-160">A `Double`.</span></span>

<span data-ttu-id="89bcf-161">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="89bcf-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="89bcf-162">STDEVP(Expression)</span><span class="sxs-lookup"><span data-stu-id="89bcf-162">STDEVP(expression)</span></span>

<span data-ttu-id="89bcf-163">Retorna o desvio padrão estatístico para a população para todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="89bcf-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="89bcf-164">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="89bcf-164">**Arguments**</span></span>

<span data-ttu-id="89bcf-165">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="89bcf-165">A Collection(`Double`).</span></span>

<span data-ttu-id="89bcf-166">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="89bcf-166">**Return Value**</span></span>

<span data-ttu-id="89bcf-167">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-167">A `Double`.</span></span>

<span data-ttu-id="89bcf-168">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="89bcf-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="89bcf-169">SUM(Expression)</span><span class="sxs-lookup"><span data-stu-id="89bcf-169">SUM(expression)</span></span>

<span data-ttu-id="89bcf-170">Retorna a soma de todos os valores na coleção.</span><span class="sxs-lookup"><span data-stu-id="89bcf-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="89bcf-171">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="89bcf-171">**Arguments**</span></span>

<span data-ttu-id="89bcf-172">Um Collection(T) onde T é um dos seguintes tipos: `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="89bcf-173">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="89bcf-173">**Return Value**</span></span>

<span data-ttu-id="89bcf-174">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-174">The type of `expression`.</span></span>

<span data-ttu-id="89bcf-175">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="89bcf-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="89bcf-176">VAR(Expression)</span><span class="sxs-lookup"><span data-stu-id="89bcf-176">VAR(expression)</span></span>

<span data-ttu-id="89bcf-177">Retorna a estatística variação de todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="89bcf-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="89bcf-178">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="89bcf-178">**Arguments**</span></span>

<span data-ttu-id="89bcf-179">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="89bcf-179">A Collection(`Double`).</span></span>

<span data-ttu-id="89bcf-180">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="89bcf-180">**Return Value**</span></span>

<span data-ttu-id="89bcf-181">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-181">A `Double`.</span></span>

<span data-ttu-id="89bcf-182">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="89bcf-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="89bcf-183">VARP(Expression)</span><span class="sxs-lookup"><span data-stu-id="89bcf-183">VARP(expression)</span></span>

<span data-ttu-id="89bcf-184">Retorna a variação estatística para a população para todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="89bcf-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="89bcf-185">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="89bcf-185">**Arguments**</span></span>

<span data-ttu-id="89bcf-186">Uma coleção (`Double`).</span><span class="sxs-lookup"><span data-stu-id="89bcf-186">A Collection(`Double`).</span></span>

<span data-ttu-id="89bcf-187">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="89bcf-187">**Return Value**</span></span>

<span data-ttu-id="89bcf-188">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="89bcf-188">A `Double`.</span></span>

<span data-ttu-id="89bcf-189">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="89bcf-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="89bcf-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89bcf-190">See also</span></span>

<span data-ttu-id="89bcf-191">Para obter mais informações sobre funções agregadas que suporta SqlClient, consulte a documentação para a versão do SQL Server que você especificou no manifesto do provedor SqlClient:</span><span class="sxs-lookup"><span data-stu-id="89bcf-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="89bcf-192">**SQL Server 2005**: [agregar funções (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="89bcf-192">**SQL Server 2005**: [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>  
<span data-ttu-id="89bcf-193">**SQL Server 2008 e posterior**: [funções agregadas (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="89bcf-193">**SQL Server 2008 and later**:  [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>  
<span data-ttu-id="89bcf-194">[Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="89bcf-194">[Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)</span></span>  
[<span data-ttu-id="89bcf-195">Funções canônicas agregadas</span><span class="sxs-lookup"><span data-stu-id="89bcf-195">Aggregate Canonical Functions</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
