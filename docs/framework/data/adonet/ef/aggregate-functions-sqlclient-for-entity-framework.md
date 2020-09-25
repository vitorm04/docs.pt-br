---
title: Funções agregadas (SqlClient para Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1c32ccfe18c67c9baeb7df0f981c9129b3bbc8bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204509"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="d7074-102">Funções agregadas (SqlClient para Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="d7074-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>

<span data-ttu-id="d7074-103">O provedor de dados. NET Framework para SQL Server (SqlClient) fornece funções agregadas.</span><span class="sxs-lookup"><span data-stu-id="d7074-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="d7074-104">Funções agregadas executam cálculos em um conjunto de valores de entrada e retornam um valor.</span><span class="sxs-lookup"><span data-stu-id="d7074-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="d7074-105">Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="d7074-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="d7074-106">A propriedade de namespace de um provedor permite que o Entity Framework descubra qual prefixo é usado por esse provedor para construções específicas, como tipos e funções.</span><span class="sxs-lookup"><span data-stu-id="d7074-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="d7074-107">A seguir estão as funções de agregação SqlClient.</span><span class="sxs-lookup"><span data-stu-id="d7074-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="d7074-108">AVG (expressão)</span><span class="sxs-lookup"><span data-stu-id="d7074-108">AVG(expression)</span></span>

<span data-ttu-id="d7074-109">Retorna a média dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="d7074-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="d7074-110">Valores nulos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="d7074-110">Null values are ignored.</span></span>

<span data-ttu-id="d7074-111">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="d7074-111">**Arguments**</span></span>

<span data-ttu-id="d7074-112">Um `Int32` , `Int64` , `Double` e `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="d7074-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="d7074-113">**Valor Retornado**</span><span class="sxs-lookup"><span data-stu-id="d7074-113">**Return Value**</span></span>

<span data-ttu-id="d7074-114">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="d7074-114">The type of `expression`.</span></span>

<span data-ttu-id="d7074-115">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="d7074-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="d7074-116">CHECKSUM_AGG (coleção)</span><span class="sxs-lookup"><span data-stu-id="d7074-116">CHECKSUM_AGG(collection)</span></span>

 <span data-ttu-id="d7074-117">Retorna a soma de verificação dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="d7074-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="d7074-118">Valores nulos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="d7074-118">Null values are ignored.</span></span>

 <span data-ttu-id="d7074-119">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="d7074-119">**Arguments**</span></span>

 <span data-ttu-id="d7074-120">Uma coleção ( `Int32` ).</span><span class="sxs-lookup"><span data-stu-id="d7074-120">A Collection(`Int32`).</span></span>

 <span data-ttu-id="d7074-121">**Valor Retornado**</span><span class="sxs-lookup"><span data-stu-id="d7074-121">**Return Value**</span></span>

 <span data-ttu-id="d7074-122">Um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="d7074-122">An `Int32`.</span></span>

 <span data-ttu-id="d7074-123">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="d7074-123">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a><span data-ttu-id="d7074-124">CONTAGEM (expressão)</span><span class="sxs-lookup"><span data-stu-id="d7074-124">COUNT(expression)</span></span>

<span data-ttu-id="d7074-125">Retorna o número de itens em uma coleção como `Int32`.</span><span class="sxs-lookup"><span data-stu-id="d7074-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="d7074-126">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="d7074-126">**Arguments**</span></span>

<span data-ttu-id="d7074-127">Uma coleção \<T> , em que T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="d7074-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="d7074-128">`Guid` (não retornado em SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="d7074-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="d7074-129">**Valor Retornado**</span><span class="sxs-lookup"><span data-stu-id="d7074-129">**Return Value**</span></span>

<span data-ttu-id="d7074-130">Um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="d7074-130">An `Int32`.</span></span>

<span data-ttu-id="d7074-131">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="d7074-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a><span data-ttu-id="d7074-132">COUNT_BIG (expressão)</span><span class="sxs-lookup"><span data-stu-id="d7074-132">COUNT_BIG(expression)</span></span>

<span data-ttu-id="d7074-133">Retorna o número de itens em uma coleção como `bigint`.</span><span class="sxs-lookup"><span data-stu-id="d7074-133">Returns the number of items in a collection as a `bigint`.</span></span>

 <span data-ttu-id="d7074-134">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="d7074-134">**Arguments**</span></span>

 <span data-ttu-id="d7074-135">Uma coleção (T), em que T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="d7074-135">A Collection(T), where T is one of the following types:</span></span>

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="d7074-136">`Guid` (não retornado em SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="d7074-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="d7074-137">**Valor Retornado**</span><span class="sxs-lookup"><span data-stu-id="d7074-137">**Return Value**</span></span>

<span data-ttu-id="d7074-138">Um `Int64`.</span><span class="sxs-lookup"><span data-stu-id="d7074-138">An `Int64`.</span></span>

<span data-ttu-id="d7074-139">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="d7074-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="d7074-140">MAX (expressão)</span><span class="sxs-lookup"><span data-stu-id="d7074-140">MAX(expression)</span></span>

<span data-ttu-id="d7074-141">Retorna o valor médio a coleção.</span><span class="sxs-lookup"><span data-stu-id="d7074-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="d7074-142">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="d7074-142">**Arguments**</span></span>

<span data-ttu-id="d7074-143">Uma coleção (T), em que T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="d7074-143">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="d7074-144">**Valor Retornado**</span><span class="sxs-lookup"><span data-stu-id="d7074-144">**Return Value**</span></span>

<span data-ttu-id="d7074-145">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="d7074-145">The type of `expression`.</span></span>

<span data-ttu-id="d7074-146">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="d7074-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="d7074-147">MIN (expressão)</span><span class="sxs-lookup"><span data-stu-id="d7074-147">MIN(expression)</span></span>

<span data-ttu-id="d7074-148">Retorna o valor médio em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="d7074-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="d7074-149">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="d7074-149">**Arguments**</span></span>

<span data-ttu-id="d7074-150">Uma coleção (T), em que T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="d7074-150">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="d7074-151">**Valor Retornado**</span><span class="sxs-lookup"><span data-stu-id="d7074-151">**Return Value**</span></span>

<span data-ttu-id="d7074-152">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="d7074-152">The type of `expression`.</span></span>

<span data-ttu-id="d7074-153">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="d7074-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="d7074-154">DESVPAD (expressão)</span><span class="sxs-lookup"><span data-stu-id="d7074-154">STDEV(expression)</span></span>

<span data-ttu-id="d7074-155">Retorna o desvio padrão estatístico de todos os valores da expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="d7074-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="d7074-156">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="d7074-156">**Arguments**</span></span>

<span data-ttu-id="d7074-157">Uma coleção ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="d7074-157">A Collection(`Double`).</span></span>

<span data-ttu-id="d7074-158">**Valor Retornado**</span><span class="sxs-lookup"><span data-stu-id="d7074-158">**Return Value**</span></span>

<span data-ttu-id="d7074-159">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="d7074-159">A `Double`.</span></span>

<span data-ttu-id="d7074-160">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="d7074-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="d7074-161">DESVPADP (expressão)</span><span class="sxs-lookup"><span data-stu-id="d7074-161">STDEVP(expression)</span></span>

<span data-ttu-id="d7074-162">Retorna o desvio padrão estatístico para a população de todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="d7074-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="d7074-163">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="d7074-163">**Arguments**</span></span>

<span data-ttu-id="d7074-164">Uma coleção ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="d7074-164">A Collection(`Double`).</span></span>

<span data-ttu-id="d7074-165">**Valor Retornado**</span><span class="sxs-lookup"><span data-stu-id="d7074-165">**Return Value**</span></span>

<span data-ttu-id="d7074-166">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="d7074-166">A `Double`.</span></span>

<span data-ttu-id="d7074-167">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="d7074-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="d7074-168">SUM (expressão)</span><span class="sxs-lookup"><span data-stu-id="d7074-168">SUM(expression)</span></span>

<span data-ttu-id="d7074-169">Retorna a soma de todos os valores na coleção.</span><span class="sxs-lookup"><span data-stu-id="d7074-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="d7074-170">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="d7074-170">**Arguments**</span></span>

<span data-ttu-id="d7074-171">Uma coleção (T), em que T é um dos seguintes tipos: `Int32` ,, `Int64` `Double` , `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="d7074-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="d7074-172">**Valor Retornado**</span><span class="sxs-lookup"><span data-stu-id="d7074-172">**Return Value**</span></span>

<span data-ttu-id="d7074-173">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="d7074-173">The type of `expression`.</span></span>

<span data-ttu-id="d7074-174">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="d7074-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="d7074-175">VAR (expressão)</span><span class="sxs-lookup"><span data-stu-id="d7074-175">VAR(expression)</span></span>

<span data-ttu-id="d7074-176">Retorna a variância estatística de todos os valores da expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="d7074-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="d7074-177">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="d7074-177">**Arguments**</span></span>

<span data-ttu-id="d7074-178">Uma coleção ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="d7074-178">A Collection(`Double`).</span></span>

<span data-ttu-id="d7074-179">**Valor Retornado**</span><span class="sxs-lookup"><span data-stu-id="d7074-179">**Return Value**</span></span>

<span data-ttu-id="d7074-180">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="d7074-180">A `Double`.</span></span>

<span data-ttu-id="d7074-181">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="d7074-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="d7074-182">VARP (expressão)</span><span class="sxs-lookup"><span data-stu-id="d7074-182">VARP(expression)</span></span>

<span data-ttu-id="d7074-183">Retorna a variância estatística para o preenchimento de todos os valores da expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="d7074-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="d7074-184">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="d7074-184">**Arguments**</span></span>

<span data-ttu-id="d7074-185">Uma coleção ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="d7074-185">A Collection(`Double`).</span></span>

<span data-ttu-id="d7074-186">**Valor Retornado**</span><span class="sxs-lookup"><span data-stu-id="d7074-186">**Return Value**</span></span>

<span data-ttu-id="d7074-187">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="d7074-187">A `Double`.</span></span>

<span data-ttu-id="d7074-188">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="d7074-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a><span data-ttu-id="d7074-189">Veja também</span><span class="sxs-lookup"><span data-stu-id="d7074-189">See also</span></span>

- [<span data-ttu-id="d7074-190">Funções de agregação (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d7074-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="d7074-191">Linguagem Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d7074-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="d7074-192">Funções agregadas canônicas</span><span class="sxs-lookup"><span data-stu-id="d7074-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
