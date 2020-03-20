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
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="6ea59-102">Funções agregadas (SqlClient para Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="6ea59-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="6ea59-103">O provedor de dados. NET Framework para SQL Server (SqlClient) fornece funções agregadas.</span><span class="sxs-lookup"><span data-stu-id="6ea59-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="6ea59-104">Funções agregadas executam cálculos em um conjunto de valores de entrada e retornam um valor.</span><span class="sxs-lookup"><span data-stu-id="6ea59-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="6ea59-105">Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="6ea59-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="6ea59-106">A propriedade de namespace de um provedor permite que o Entity Framework descubra qual prefixo é usado por esse provedor para construções específicas, como tipos e funções.</span><span class="sxs-lookup"><span data-stu-id="6ea59-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="6ea59-107">A seguir estão as funções agregadas sqlClient.</span><span class="sxs-lookup"><span data-stu-id="6ea59-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="6ea59-108">AVG(expressão)</span><span class="sxs-lookup"><span data-stu-id="6ea59-108">AVG(expression)</span></span>

<span data-ttu-id="6ea59-109">Retorna a média dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="6ea59-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="6ea59-110">Valores nulos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="6ea59-110">Null values are ignored.</span></span>

<span data-ttu-id="6ea59-111">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6ea59-111">**Arguments**</span></span>

<span data-ttu-id="6ea59-112">Um `Int32` `Int64`, `Double`, `Decimal`e .</span><span class="sxs-lookup"><span data-stu-id="6ea59-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="6ea59-113">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="6ea59-113">**Return Value**</span></span>

<span data-ttu-id="6ea59-114">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="6ea59-114">The type of `expression`.</span></span>

<span data-ttu-id="6ea59-115">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6ea59-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="6ea59-116">CHECKSUM_AGG(coleção)</span><span class="sxs-lookup"><span data-stu-id="6ea59-116">CHECKSUM_AGG(collection)</span></span>

 <span data-ttu-id="6ea59-117">Retorna a soma de verificação dos valores em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="6ea59-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="6ea59-118">Valores nulos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="6ea59-118">Null values are ignored.</span></span>

 <span data-ttu-id="6ea59-119">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6ea59-119">**Arguments**</span></span>

 <span data-ttu-id="6ea59-120">Uma Coleção.`Int32`</span><span class="sxs-lookup"><span data-stu-id="6ea59-120">A Collection(`Int32`).</span></span>

 <span data-ttu-id="6ea59-121">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="6ea59-121">**Return Value**</span></span>

 <span data-ttu-id="6ea59-122">Um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="6ea59-122">An `Int32`.</span></span>

 <span data-ttu-id="6ea59-123">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6ea59-123">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a><span data-ttu-id="6ea59-124">CONTAGEM (expressão)</span><span class="sxs-lookup"><span data-stu-id="6ea59-124">COUNT(expression)</span></span>

<span data-ttu-id="6ea59-125">Retorna o número de itens em uma coleção como `Int32`.</span><span class="sxs-lookup"><span data-stu-id="6ea59-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="6ea59-126">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6ea59-126">**Arguments**</span></span>

<span data-ttu-id="6ea59-127">Uma\<coleção T>, onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="6ea59-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="6ea59-128">`Guid`(não retornado no SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="6ea59-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="6ea59-129">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="6ea59-129">**Return Value**</span></span>

<span data-ttu-id="6ea59-130">Um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="6ea59-130">An `Int32`.</span></span>

<span data-ttu-id="6ea59-131">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6ea59-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a><span data-ttu-id="6ea59-132">COUNT_BIG(expressão)</span><span class="sxs-lookup"><span data-stu-id="6ea59-132">COUNT_BIG(expression)</span></span>

<span data-ttu-id="6ea59-133">Retorna o número de itens em uma coleção como `bigint`.</span><span class="sxs-lookup"><span data-stu-id="6ea59-133">Returns the number of items in a collection as a `bigint`.</span></span>

 <span data-ttu-id="6ea59-134">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6ea59-134">**Arguments**</span></span>

 <span data-ttu-id="6ea59-135">Uma Coleção(T), onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="6ea59-135">A Collection(T), where T is one of the following types:</span></span>

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="6ea59-136">`Guid`(não retornado no SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="6ea59-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="6ea59-137">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="6ea59-137">**Return Value**</span></span>

<span data-ttu-id="6ea59-138">Um `Int64`.</span><span class="sxs-lookup"><span data-stu-id="6ea59-138">An `Int64`.</span></span>

<span data-ttu-id="6ea59-139">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6ea59-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="6ea59-140">MAX (expressão)</span><span class="sxs-lookup"><span data-stu-id="6ea59-140">MAX(expression)</span></span>

<span data-ttu-id="6ea59-141">Retorna o valor médio a coleção.</span><span class="sxs-lookup"><span data-stu-id="6ea59-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="6ea59-142">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6ea59-142">**Arguments**</span></span>

<span data-ttu-id="6ea59-143">Uma Coleção(T), onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="6ea59-143">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="6ea59-144">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="6ea59-144">**Return Value**</span></span>

<span data-ttu-id="6ea59-145">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="6ea59-145">The type of `expression`.</span></span>

<span data-ttu-id="6ea59-146">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6ea59-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="6ea59-147">MIN (expressão)</span><span class="sxs-lookup"><span data-stu-id="6ea59-147">MIN(expression)</span></span>

<span data-ttu-id="6ea59-148">Retorna o valor médio em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="6ea59-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="6ea59-149">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6ea59-149">**Arguments**</span></span>

<span data-ttu-id="6ea59-150">Uma Coleção(T), onde T é um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="6ea59-150">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="6ea59-151">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="6ea59-151">**Return Value**</span></span>

<span data-ttu-id="6ea59-152">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="6ea59-152">The type of `expression`.</span></span>

<span data-ttu-id="6ea59-153">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6ea59-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="6ea59-154">STDEV(expressão)</span><span class="sxs-lookup"><span data-stu-id="6ea59-154">STDEV(expression)</span></span>

<span data-ttu-id="6ea59-155">Retorna o desvio padrão estatístico de todos os valores da expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="6ea59-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="6ea59-156">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6ea59-156">**Arguments**</span></span>

<span data-ttu-id="6ea59-157">Uma Coleção.`Double`</span><span class="sxs-lookup"><span data-stu-id="6ea59-157">A Collection(`Double`).</span></span>

<span data-ttu-id="6ea59-158">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="6ea59-158">**Return Value**</span></span>

<span data-ttu-id="6ea59-159">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="6ea59-159">A `Double`.</span></span>

<span data-ttu-id="6ea59-160">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6ea59-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="6ea59-161">STDEVP (expressão)</span><span class="sxs-lookup"><span data-stu-id="6ea59-161">STDEVP(expression)</span></span>

<span data-ttu-id="6ea59-162">Retorna o desvio padrão estatístico para a população de todos os valores na expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="6ea59-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="6ea59-163">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6ea59-163">**Arguments**</span></span>

<span data-ttu-id="6ea59-164">Uma Coleção.`Double`</span><span class="sxs-lookup"><span data-stu-id="6ea59-164">A Collection(`Double`).</span></span>

<span data-ttu-id="6ea59-165">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="6ea59-165">**Return Value**</span></span>

<span data-ttu-id="6ea59-166">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="6ea59-166">A `Double`.</span></span>

<span data-ttu-id="6ea59-167">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6ea59-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="6ea59-168">SOMA (expressão)</span><span class="sxs-lookup"><span data-stu-id="6ea59-168">SUM(expression)</span></span>

<span data-ttu-id="6ea59-169">Retorna a soma de todos os valores na coleção.</span><span class="sxs-lookup"><span data-stu-id="6ea59-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="6ea59-170">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6ea59-170">**Arguments**</span></span>

<span data-ttu-id="6ea59-171">Uma Coleção(T) onde T é um `Int32` `Int64`dos `Double` `Decimal`seguintes tipos: , , . .</span><span class="sxs-lookup"><span data-stu-id="6ea59-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="6ea59-172">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="6ea59-172">**Return Value**</span></span>

<span data-ttu-id="6ea59-173">O tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="6ea59-173">The type of `expression`.</span></span>

<span data-ttu-id="6ea59-174">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6ea59-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="6ea59-175">VAR (expressão)</span><span class="sxs-lookup"><span data-stu-id="6ea59-175">VAR(expression)</span></span>

<span data-ttu-id="6ea59-176">Retorna a variância estatística de todos os valores da expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="6ea59-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="6ea59-177">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6ea59-177">**Arguments**</span></span>

<span data-ttu-id="6ea59-178">Uma Coleção.`Double`</span><span class="sxs-lookup"><span data-stu-id="6ea59-178">A Collection(`Double`).</span></span>

<span data-ttu-id="6ea59-179">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="6ea59-179">**Return Value**</span></span>

<span data-ttu-id="6ea59-180">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="6ea59-180">A `Double`.</span></span>

<span data-ttu-id="6ea59-181">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6ea59-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="6ea59-182">VARP (expressão)</span><span class="sxs-lookup"><span data-stu-id="6ea59-182">VARP(expression)</span></span>

<span data-ttu-id="6ea59-183">Retorna a variância estatística para o preenchimento de todos os valores da expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="6ea59-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="6ea59-184">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6ea59-184">**Arguments**</span></span>

<span data-ttu-id="6ea59-185">Uma Coleção.`Double`</span><span class="sxs-lookup"><span data-stu-id="6ea59-185">A Collection(`Double`).</span></span>

<span data-ttu-id="6ea59-186">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="6ea59-186">**Return Value**</span></span>

<span data-ttu-id="6ea59-187">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="6ea59-187">A `Double`.</span></span>

<span data-ttu-id="6ea59-188">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6ea59-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a><span data-ttu-id="6ea59-189">Confira também</span><span class="sxs-lookup"><span data-stu-id="6ea59-189">See also</span></span>

- [<span data-ttu-id="6ea59-190">Funções de agregação (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6ea59-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- <span data-ttu-id="6ea59-191">[Entity SQL Language](./language-reference/entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="6ea59-191">[Entity SQL Language](./language-reference/entity-sql-language.md)</span></span>
- [<span data-ttu-id="6ea59-192">Funções agregadas canônicas</span><span class="sxs-lookup"><span data-stu-id="6ea59-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
