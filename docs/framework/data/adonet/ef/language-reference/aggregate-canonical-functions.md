---
title: Funções agregadas canônicas
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: f5d3584c6e9d35c9eb69b4f54cad45187416ee59
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372796"
---
# <a name="aggregate-canonical-functions"></a><span data-ttu-id="af3f2-102">Funções agregadas canônicas</span><span class="sxs-lookup"><span data-stu-id="af3f2-102">Aggregate Canonical Functions</span></span>

<span data-ttu-id="af3f2-103">Agregados são as expressões em que reduz uma série de valores de entrada, por exemplo, um único valor.</span><span class="sxs-lookup"><span data-stu-id="af3f2-103">Aggregates are expressions that reduce a series of input values into, for example, a single value.</span></span> <span data-ttu-id="af3f2-104">Agregados são normalmente usadas em conjunto com o cláusula GROUP BY de expressão SELECT, e há restrições em onde eles podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="af3f2-104">Aggregates are normally used in conjunction with the GROUP BY clause of the SELECT expression, and there are constraints on where they can be used.</span></span>

## <a name="aggregate-entity-sql-canonical-functions"></a><span data-ttu-id="af3f2-105">Funções agregadas canônicas do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="af3f2-105">Aggregate Entity SQL canonical functions</span></span>

<span data-ttu-id="af3f2-106">A seguir estão as funções canônicas agregadas do Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="af3f2-106">The following are the aggregate Entity SQL canonical functions.</span></span>

### <a name="avgexpression"></a><span data-ttu-id="af3f2-107">Avg (expressão)</span><span class="sxs-lookup"><span data-stu-id="af3f2-107">Avg(expression)</span></span>

<span data-ttu-id="af3f2-108">Retorna a média dos valores não anuláveis.</span><span class="sxs-lookup"><span data-stu-id="af3f2-108">Returns the average of the non-null values.</span></span>

<span data-ttu-id="af3f2-109">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="af3f2-109">**Arguments**</span></span>

<span data-ttu-id="af3f2-110">Uma `Int32`, `Int64`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="af3f2-110">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="af3f2-111">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="af3f2-111">**Return Value**</span></span>

<span data-ttu-id="af3f2-112">O tipo de `expression`, ou `null` se todos os valores de entrada são `null` valores.</span><span class="sxs-lookup"><span data-stu-id="af3f2-112">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="af3f2-113">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="af3f2-113">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a><span data-ttu-id="af3f2-114">BigCount (expressão)</span><span class="sxs-lookup"><span data-stu-id="af3f2-114">BigCount(expression)</span></span>

<span data-ttu-id="af3f2-115">Retorna o tamanho do agregado que inclui valores nulos e duplicados.</span><span class="sxs-lookup"><span data-stu-id="af3f2-115">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="af3f2-116">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="af3f2-116">**Arguments**</span></span>

<span data-ttu-id="af3f2-117">Qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="af3f2-117">Any type.</span></span>

<span data-ttu-id="af3f2-118">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="af3f2-118">**Return Value**</span></span>

<span data-ttu-id="af3f2-119">Um `Int64`.</span><span class="sxs-lookup"><span data-stu-id="af3f2-119">An `Int64`.</span></span>

<span data-ttu-id="af3f2-120">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="af3f2-120">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a><span data-ttu-id="af3f2-121">Contagem (expressão)</span><span class="sxs-lookup"><span data-stu-id="af3f2-121">Count(expression)</span></span>

<span data-ttu-id="af3f2-122">Retorna o tamanho do agregado que inclui valores nulos e duplicados.</span><span class="sxs-lookup"><span data-stu-id="af3f2-122">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="af3f2-123">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="af3f2-123">**Arguments**</span></span>

<span data-ttu-id="af3f2-124">Qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="af3f2-124">Any type.</span></span>

<span data-ttu-id="af3f2-125">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="af3f2-125">**Return Value**</span></span>

<span data-ttu-id="af3f2-126">Um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="af3f2-126">An `Int32`.</span></span>

<span data-ttu-id="af3f2-127">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="af3f2-127">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a><span data-ttu-id="af3f2-128">Máximo (expressão)</span><span class="sxs-lookup"><span data-stu-id="af3f2-128">Max(expression)</span></span>

<span data-ttu-id="af3f2-129">Retorna o máximo dos valores não anuláveis.</span><span class="sxs-lookup"><span data-stu-id="af3f2-129">Returns the maximum of the non-null values.</span></span>

<span data-ttu-id="af3f2-130">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="af3f2-130">**Arguments**</span></span>

<span data-ttu-id="af3f2-131">
  `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="af3f2-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="af3f2-132">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="af3f2-132">**Return Value**</span></span>

<span data-ttu-id="af3f2-133">O tipo de `expression`, ou `null` se todos os valores de entrada são `null` valores.</span><span class="sxs-lookup"><span data-stu-id="af3f2-133">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="af3f2-134">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="af3f2-134">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a><span data-ttu-id="af3f2-135">Minuto (expressão)</span><span class="sxs-lookup"><span data-stu-id="af3f2-135">Min(expression)</span></span>

<span data-ttu-id="af3f2-136">Retorna o mínimo dos valores não anuláveis.</span><span class="sxs-lookup"><span data-stu-id="af3f2-136">Returns the minimum of the non-null values.</span></span>

<span data-ttu-id="af3f2-137">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="af3f2-137">**Arguments**</span></span>

<span data-ttu-id="af3f2-138">
  `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="af3f2-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="af3f2-139">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="af3f2-139">**Return Value**</span></span>

<span data-ttu-id="af3f2-140">O tipo de `expression`, ou `null` se todos os valores de entrada são `null` valores.</span><span class="sxs-lookup"><span data-stu-id="af3f2-140">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="af3f2-141">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="af3f2-141">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a><span data-ttu-id="af3f2-142">StDev (expressão)</span><span class="sxs-lookup"><span data-stu-id="af3f2-142">StDev(expression)</span></span>

<span data-ttu-id="af3f2-143">Retorna o desvio padrão de valores não anuláveis.</span><span class="sxs-lookup"><span data-stu-id="af3f2-143">Returns the standard deviation of the non-null values.</span></span>

<span data-ttu-id="af3f2-144">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="af3f2-144">**Arguments**</span></span>

<span data-ttu-id="af3f2-145">
  `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="af3f2-145">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="af3f2-146">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="af3f2-146">**Return Value**</span></span>

<span data-ttu-id="af3f2-147">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="af3f2-147">A `Double`.</span></span> <span data-ttu-id="af3f2-148">`Null`, se todos os valores de entrada são valores de `null` .</span><span class="sxs-lookup"><span data-stu-id="af3f2-148">`Null`, if all input values are `null` values.</span></span>

<span data-ttu-id="af3f2-149">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="af3f2-149">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a><span data-ttu-id="af3f2-150">StDevP (expressão)</span><span class="sxs-lookup"><span data-stu-id="af3f2-150">StDevP(expression)</span></span>

<span data-ttu-id="af3f2-151">Retorna o desvio padrão para a população de todos os valores.</span><span class="sxs-lookup"><span data-stu-id="af3f2-151">Returns the standard deviation for the population of all values.</span></span>

<span data-ttu-id="af3f2-152">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="af3f2-152">**Arguments**</span></span>

<span data-ttu-id="af3f2-153">
  `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="af3f2-153">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="af3f2-154">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="af3f2-154">**Return Value**</span></span>

<span data-ttu-id="af3f2-155">Um `Double`, ou `null` se todos os valores de entrada são `null` valores.</span><span class="sxs-lookup"><span data-stu-id="af3f2-155">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="af3f2-156">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="af3f2-156">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a><span data-ttu-id="af3f2-157">Soma (expressão)</span><span class="sxs-lookup"><span data-stu-id="af3f2-157">Sum(expression)</span></span>

<span data-ttu-id="af3f2-158">Retorna a soma dos valores não anuláveis.</span><span class="sxs-lookup"><span data-stu-id="af3f2-158">Returns the sum of the non-null values.</span></span>

<span data-ttu-id="af3f2-159">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="af3f2-159">**Arguments**</span></span>

<span data-ttu-id="af3f2-160">
  `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="af3f2-160">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="af3f2-161">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="af3f2-161">**Return Value**</span></span>

<span data-ttu-id="af3f2-162">Um `Double`, ou `null` se todos os valores de entrada são `null` valores.</span><span class="sxs-lookup"><span data-stu-id="af3f2-162">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="af3f2-163">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="af3f2-163">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a><span data-ttu-id="af3f2-164">Var (expressão)</span><span class="sxs-lookup"><span data-stu-id="af3f2-164">Var(expression)</span></span>

<span data-ttu-id="af3f2-165">Retorna a variação de todos os valores não anuláveis.</span><span class="sxs-lookup"><span data-stu-id="af3f2-165">Returns the variance of all non-null values.</span></span>

<span data-ttu-id="af3f2-166">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="af3f2-166">**Arguments**</span></span>

<span data-ttu-id="af3f2-167">
  `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="af3f2-167">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="af3f2-168">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="af3f2-168">**Return Value**</span></span>

<span data-ttu-id="af3f2-169">Um `Double`, ou `null` se todos os valores de entrada são `null` valores.</span><span class="sxs-lookup"><span data-stu-id="af3f2-169">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="af3f2-170">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="af3f2-170">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a><span data-ttu-id="af3f2-171">VarP (expressão)</span><span class="sxs-lookup"><span data-stu-id="af3f2-171">VarP(expression)</span></span>

<span data-ttu-id="af3f2-172">Retorna a variação para a população de todos os valores não anuláveis.</span><span class="sxs-lookup"><span data-stu-id="af3f2-172">Returns the variance for the population of all non-null values.</span></span>

<span data-ttu-id="af3f2-173">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="af3f2-173">**Arguments**</span></span>

<span data-ttu-id="af3f2-174">
  `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="af3f2-174">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="af3f2-175">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="af3f2-175">**Return Value**</span></span>

<span data-ttu-id="af3f2-176">Um `Double`, ou `null` se todos os valores de entrada são `null` valores.</span><span class="sxs-lookup"><span data-stu-id="af3f2-176">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="af3f2-177">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="af3f2-177">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

<span data-ttu-id="af3f2-178">Funcionalidade equivalente está disponível no provedor gerenciado cliente do Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="af3f2-178">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="af3f2-179">Para obter mais informações, consulte [SqlClient para funções de Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="af3f2-179">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>

## <a name="collection-based-aggregates"></a><span data-ttu-id="af3f2-180">Agregações baseadas em coleção</span><span class="sxs-lookup"><span data-stu-id="af3f2-180">Collection-based aggregates</span></span>

<span data-ttu-id="af3f2-181">Agregados coleção com base (funções de coleção) operam em coleções e retornam um valor.</span><span class="sxs-lookup"><span data-stu-id="af3f2-181">Collection-based aggregates (collection functions) operate on collections and return a value.</span></span> <span data-ttu-id="af3f2-182">Por exemplo se os ORDENS são uma coleção de todos os pedidos, você pode calcular a data de remessa mais antiga com a seguinte expressão:</span><span class="sxs-lookup"><span data-stu-id="af3f2-182">For example if ORDERS is a collection of all orders, you can calculate the earliest ship date with the following expression:</span></span>

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

<span data-ttu-id="af3f2-183">Agregados coleções baseadas dentro de expressões são avaliadas dentro do escopo ambiente atual de resolução.</span><span class="sxs-lookup"><span data-stu-id="af3f2-183">Expressions inside collection-based aggregates are evaluated within the current ambient name-resolution scope.</span></span>

## <a name="group-based-aggregates"></a><span data-ttu-id="af3f2-184">Agregações com base em grupo</span><span class="sxs-lookup"><span data-stu-id="af3f2-184">Group-based aggregates</span></span>

<span data-ttu-id="af3f2-185">Agregados Grupo- com base são calculadas sobre um grupo como definidas por cláusula GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="af3f2-185">Group-based aggregates are calculated over a group as defined by the GROUP BY clause.</span></span> <span data-ttu-id="af3f2-186">Para cada grupo em resultado, uma agregação separada é calculada usando elementos em cada grupo como entrada ao cálculo agregado.</span><span class="sxs-lookup"><span data-stu-id="af3f2-186">For each group in the result, a separate aggregate is calculated by using the elements in each group as input to the aggregate calculation.</span></span> <span data-ttu-id="af3f2-187">Quando a grupo- pela cláusula é usado em uma expressão selecionar, simplesmente agrupamento nomes de expressão, agregados, ou expressões constantes podem acessar estar presente na projeção ou ordem- pela cláusula.</span><span class="sxs-lookup"><span data-stu-id="af3f2-187">When a group-by clause is used in a select expression, only grouping expression names, aggregates, or constant expressions can be present in the projection or order-by clause.</span></span>

<span data-ttu-id="af3f2-188">O exemplo a seguir calcula a média quantidade ordenada para cada produto:</span><span class="sxs-lookup"><span data-stu-id="af3f2-188">The following example calculates the average quantity ordered for each product:</span></span>

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

<span data-ttu-id="af3f2-189">É possível ter uma agregação grupo-base sem um explícito grupo-pela cláusula SELECT na expressão.</span><span class="sxs-lookup"><span data-stu-id="af3f2-189">It's possible to have a group-based aggregate without an explicit group-by clause in the SELECT expression.</span></span> <span data-ttu-id="af3f2-190">Nesse caso, todos os elementos são tratados como um único grupo.</span><span class="sxs-lookup"><span data-stu-id="af3f2-190">In this case, all elements are treated as a single group.</span></span> <span data-ttu-id="af3f2-191">Isso é equivalente a especificar um agrupamento com base em uma constante.</span><span class="sxs-lookup"><span data-stu-id="af3f2-191">This is equivalent of specifying a grouping based on a constant.</span></span> <span data-ttu-id="af3f2-192">Tomada, por exemplo, a expressão a seguir:</span><span class="sxs-lookup"><span data-stu-id="af3f2-192">Take, for example, the following expression:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

<span data-ttu-id="af3f2-193">Isso é equivalente ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="af3f2-193">This is equivalent to the following:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

<span data-ttu-id="af3f2-194">As expressões na agregação grupo- base são avaliadas dentro do escopo de resolução que seria visível para a cláusula WHERE expressão.</span><span class="sxs-lookup"><span data-stu-id="af3f2-194">Expressions inside the group-based aggregate are evaluated within the name-resolution scope that would be visible to the WHERE clause expression.</span></span>

<span data-ttu-id="af3f2-195">Como em [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], agregações baseadas em grupo também podem especificar um todos ou modificador DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="af3f2-195">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], group-based aggregates can also specify an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="af3f2-196">Se o modificador DISTINCT é especificado, as duplicatas são eliminadas de coleção de entrada aggregate, antes que a agregação é calculada apenas.</span><span class="sxs-lookup"><span data-stu-id="af3f2-196">If the DISTINCT modifier is specified, duplicates are eliminated from the aggregate input collection, before the aggregate is computed.</span></span> <span data-ttu-id="af3f2-197">Se TODOS OS modificador é especificado (ou se nenhum modificador é especificado), nenhuma descarte duplicado é executada.</span><span class="sxs-lookup"><span data-stu-id="af3f2-197">If the ALL modifier is specified (or if no modifier is specified), no duplicate elimination is performed.</span></span>

## <a name="see-also"></a><span data-ttu-id="af3f2-198">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af3f2-198">See also</span></span>

- <span data-ttu-id="af3f2-199">[Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) (Funções canônicas)</span><span class="sxs-lookup"><span data-stu-id="af3f2-199">[Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)</span></span>
