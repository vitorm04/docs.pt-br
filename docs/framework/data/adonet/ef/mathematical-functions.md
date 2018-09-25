---
title: Funções matemáticas
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: e6c58d781d7138f8295f2d0a2f0db110ad4b1dd6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47113735"
---
# <a name="mathematical-functions"></a><span data-ttu-id="9b6d9-102">Funções matemáticas</span><span class="sxs-lookup"><span data-stu-id="9b6d9-102">Mathematical Functions</span></span>

<span data-ttu-id="9b6d9-103">O provedor de dados. NET Framework para SQL Server (SqlClient) fornece as funções matemáticas que executam cálculos nos valores de entrada que são fornecidos como argumentos, e retorna um resultado de valor numérico.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="9b6d9-104">Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="9b6d9-105">A propriedade de namespace de um provedor permite que Entity Framework descobrir que prefixo é usado por esse provedor para compilações específicas, como tipos e funções. A tabela a seguir descreve as funções matemáticas SqlClient.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="9b6d9-106">Abs(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-106">ABS(expression)</span></span>

<span data-ttu-id="9b6d9-107">Executa a função de valor absoluto.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-107">Performs the absolute value function.</span></span>

<span data-ttu-id="9b6d9-108">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-108">**Arguments**</span></span>

<span data-ttu-id="9b6d9-109">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-109">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="9b6d9-110">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-110">**Return Value**</span></span>

<span data-ttu-id="9b6d9-111">O valor absoluto de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-111">The absolute value of the specified expression.</span></span>

<span data-ttu-id="9b6d9-112">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-112">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="9b6d9-113">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-113">ACOS(expression)</span></span>

<span data-ttu-id="9b6d9-114">Retorna o valor de arccosine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-114">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="9b6d9-115">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-115">**Arguments**</span></span>

<span data-ttu-id="9b6d9-116">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-116">`expression`: A `Double`.</span></span>

<span data-ttu-id="9b6d9-117">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-117">**Return Value**</span></span>

<span data-ttu-id="9b6d9-118">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-118">A `Double`.</span></span>

<span data-ttu-id="9b6d9-119">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-119">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="9b6d9-120">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-120">ASIN(expression)</span></span>

<span data-ttu-id="9b6d9-121">Retorna o valor de arcsine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-121">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="9b6d9-122">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-122">**Arguments**</span></span>

<span data-ttu-id="9b6d9-123">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-123">`expression`: A `Double`.</span></span>

<span data-ttu-id="9b6d9-124">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-124">**Return Value**</span></span>

<span data-ttu-id="9b6d9-125">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-125">A `Double`.</span></span>

<span data-ttu-id="9b6d9-126">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-126">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="9b6d9-127">ATAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-127">ATAN(expression)</span></span>

<span data-ttu-id="9b6d9-128">Retorna o valor de arctangent de expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-128">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="9b6d9-129">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-129">**Arguments**</span></span>

<span data-ttu-id="9b6d9-130">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-130">`expression`: A `Double`.</span></span>

<span data-ttu-id="9b6d9-131">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-131">**Return Value**</span></span>

<span data-ttu-id="9b6d9-132">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-132">A `Double`.</span></span>

<span data-ttu-id="9b6d9-133">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-133">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="9b6d9-134">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-134">ATN2(expression, expression)</span></span>

<span data-ttu-id="9b6d9-135">Retorna o ângulo, em radianos, cuja tangente é entre as duas expressões numéricas especificadas.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-135">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="9b6d9-136">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-136">**Arguments**</span></span>

<span data-ttu-id="9b6d9-137">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-137">`expression`: A `Double`.</span></span>

<span data-ttu-id="9b6d9-138">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-138">**Return Value**</span></span>

<span data-ttu-id="9b6d9-139">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-139">A `Double`.</span></span>

<span data-ttu-id="9b6d9-140">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-140">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="9b6d9-141">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-141">CEILING(expression)</span></span>

<span data-ttu-id="9b6d9-142">Converte a expressão especificada para o inteiro menor que é maior ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-142">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="9b6d9-143">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-143">**Arguments**</span></span>

<span data-ttu-id="9b6d9-144">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-144">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="9b6d9-145">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-145">**Return Value**</span></span>

<span data-ttu-id="9b6d9-146">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-146">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="9b6d9-147">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-147">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="9b6d9-148">CoS(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-148">COS(expression)</span></span>

<span data-ttu-id="9b6d9-149">Calcula o cosseno trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-149">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="9b6d9-150">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-150">**Arguments**</span></span> 

<span data-ttu-id="9b6d9-151">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-151">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9b6d9-152">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-152">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-153">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-153">A `Double`.</span></span> 

<span data-ttu-id="9b6d9-154">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-154">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="9b6d9-155">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-155">COT(expression)</span></span>

<span data-ttu-id="9b6d9-156">Calcula o cotangente trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-156">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="9b6d9-157">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-157">**Arguments**</span></span> 

<span data-ttu-id="9b6d9-158">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-158">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9b6d9-159">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-159">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-160">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-160">A `Double`.</span></span> 

<span data-ttu-id="9b6d9-161">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-161">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="9b6d9-162">DEGREES(radians)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-162">DEGREES(radians)</span></span>

<span data-ttu-id="9b6d9-163">Retorna o ângulo correspondente em graus.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-163">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="9b6d9-164">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-164">**Arguments**</span></span> 

<span data-ttu-id="9b6d9-165">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-165">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="9b6d9-166">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-166">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-167">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-167">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="9b6d9-168">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-168">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="9b6d9-169">EXP(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-169">EXP(expression)</span></span>

<span data-ttu-id="9b6d9-170">Calcula o valor exponencialmente de uma expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-170">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="9b6d9-171">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-171">**Arguments**</span></span> 

<span data-ttu-id="9b6d9-172">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-172">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9b6d9-173">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-173">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-174">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-174">A `Double`.</span></span> 

<span data-ttu-id="9b6d9-175">**Exemplo** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="9b6d9-175">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="9b6d9-176">Floor(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-176">FLOOR(expression)</span></span>

<span data-ttu-id="9b6d9-177">Converte a expressão especificada para o inteiro maior menor ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-177">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="9b6d9-178">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-178">**Arguments**</span></span> 

<span data-ttu-id="9b6d9-179">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-179">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9b6d9-180">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-180">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-181">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-181">A `Double`.</span></span> 

<span data-ttu-id="9b6d9-182">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-182">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="9b6d9-183">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-183">LOG(expression)</span></span>

<span data-ttu-id="9b6d9-184">Calcula o logaritmo natural da expressão especificada de `float` .</span><span class="sxs-lookup"><span data-stu-id="9b6d9-184">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="9b6d9-185">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-185">**Arguments**</span></span> 

<span data-ttu-id="9b6d9-186">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-186">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9b6d9-187">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-187">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-188">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-188">A `Double`.</span></span> 

<span data-ttu-id="9b6d9-189">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-189">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="9b6d9-190">LOG10(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-190">LOG10(expression)</span></span>

<span data-ttu-id="9b6d9-191">Retorna o logaritmo base-10 de expressão especificada de `Double` .</span><span class="sxs-lookup"><span data-stu-id="9b6d9-191">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="9b6d9-192">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-192">**Arguments**</span></span> 

<span data-ttu-id="9b6d9-193">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-193">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9b6d9-194">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-194">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-195">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-195">A `Double`.</span></span> 

<span data-ttu-id="9b6d9-196">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-196">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="9b6d9-197">PI)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-197">PI()</span></span>

<span data-ttu-id="9b6d9-198">Retorna o valor constante de pi como `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-198">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="9b6d9-199">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-199">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-200">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-200">A `Double`.</span></span> 

<span data-ttu-id="9b6d9-201">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-201">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="9b6d9-202">POWER (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-202">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="9b6d9-203">Calcula o valor de uma expressão especificada em uma potência especificada.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-203">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="9b6d9-204">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-204">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="9b6d9-205">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-205">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="9b6d9-206">Um `Double` que representa a potência à qual elevar o `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-206">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="9b6d9-207">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-207">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-208">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-208">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="9b6d9-209">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-209">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="9b6d9-210">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-210">RADIANS(expression)</span></span>

<span data-ttu-id="9b6d9-211">Converte graus a radianos.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-211">Converts degrees to radians.</span></span> 

<span data-ttu-id="9b6d9-212">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-212">**Arguments**</span></span> 

<span data-ttu-id="9b6d9-213">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-213">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="9b6d9-214">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-214">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-215">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-215">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="9b6d9-216">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-216">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="9b6d9-217">RAND([Seed])</span><span class="sxs-lookup"><span data-stu-id="9b6d9-217">RAND([seed])</span></span>

<span data-ttu-id="9b6d9-218">Retorna um valor aleatório de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-218">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="9b6d9-219">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-219">**Arguments**</span></span> 

<span data-ttu-id="9b6d9-220">O valor de semente como um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-220">The seed value as an `Int32`.</span></span> <span data-ttu-id="9b6d9-221">Se a semente não for especificada, o mecanismo de base de dados SQL Server atribui um valor semente aleatoriamente.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-221">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="9b6d9-222">Para um valor semente especificado, o resultado retornado é sempre o mesmo.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-222">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="9b6d9-223">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-223">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-224">Um valor aleatório de 0 a 1. de `Double` .</span><span class="sxs-lookup"><span data-stu-id="9b6d9-224">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="9b6d9-225">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-225">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="9b6d9-226">Round(Numeric_Expression, Length[,Function])</span><span class="sxs-lookup"><span data-stu-id="9b6d9-226">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="9b6d9-227">Retorna uma expressão numérica, arredondada para o comprimento ou a precisão especificada.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-227">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="9b6d9-228">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-228">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="9b6d9-229">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-229">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="9b6d9-230">Uma `Int32` que representa a precisão para o qual `numeric_expression` deve ser arredondada.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-230">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="9b6d9-231">Quando `length` é um número positivo, `numeric_expression` ele é arredondado para o número de posições decimais especificadas por `length`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-231">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="9b6d9-232">Quando `length` é um número negativo, `numeric_expression` é arredondado no lado esquerdo do ponto decimal, como especificado por `length`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-232">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="9b6d9-233">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-233">Optional.</span></span> <span data-ttu-id="9b6d9-234">Um `Int32` que representa o tipo de operação a ser executada.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-234">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="9b6d9-235">Quando a função for omitida ou tem um valor de 0 (padrão), `numeric_expression` é arredondado.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-235">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="9b6d9-236">Quando um valor diferente de 0 for especificado, `numeric_expression` será truncado.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-236">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="9b6d9-237">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-237">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-238">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-238">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="9b6d9-239">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-239">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="9b6d9-240">Sign(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-240">SIGN(expression)</span></span> 

<span data-ttu-id="9b6d9-241">Retorna o positivo (+1), 0 (zero), ou (- o sinal de subtração de 1) da expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-241">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="9b6d9-242">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-242">**Arguments**</span></span> 

<span data-ttu-id="9b6d9-243">`expression`: `Int32`, `Int64`, `Double` ou `Decimal`</span><span class="sxs-lookup"><span data-stu-id="9b6d9-243">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="9b6d9-244">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-244">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-245">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-245">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="9b6d9-246">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-246">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="9b6d9-247">SIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-247">SIN(expression)</span></span>

<span data-ttu-id="9b6d9-248">Calcula o seno trigonométricas do ângulo especificado em radianos, e retorna uma expressão de `Double` .</span><span class="sxs-lookup"><span data-stu-id="9b6d9-248">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="9b6d9-249">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-249">**Arguments**</span></span> 

<span data-ttu-id="9b6d9-250">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-250">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9b6d9-251">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-251">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-252">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-252">A `Double`.</span></span> 

<span data-ttu-id="9b6d9-253">**Exemplo** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="9b6d9-253">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="9b6d9-254">Sqrt(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-254">SQRT(expression)</span></span>

<span data-ttu-id="9b6d9-255">Retorna a raiz quadrada de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-255">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="9b6d9-256">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-256">**Arguments**</span></span> 

<span data-ttu-id="9b6d9-257">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-257">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9b6d9-258">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-258">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-259">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-259">A `Double`.</span></span> 

<span data-ttu-id="9b6d9-260">**Exemplo** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="9b6d9-260">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="9b6d9-261">SQUARE(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-261">SQUARE(expression)</span></span>

<span data-ttu-id="9b6d9-262">Retorna o quadrado de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-262">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="9b6d9-263">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-263">**Arguments**</span></span> 

<span data-ttu-id="9b6d9-264">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-264">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9b6d9-265">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-265">**Return Value**</span></span> 

<span data-ttu-id="9b6d9-266">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-266">A `Double`.</span></span> 

<span data-ttu-id="9b6d9-267">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-267">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="9b6d9-268">TAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-268">TAN(expression)</span></span>

<span data-ttu-id="9b6d9-269">Calcula a tangente de uma expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9b6d9-269">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="9b6d9-270">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-270">**Arguments**</span></span> 

<span data-ttu-id="9b6d9-271">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="9b6d9-271">`expression`: `Double`</span></span> 

<span data-ttu-id="9b6d9-272">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-272">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="9b6d9-273">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9b6d9-273">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="9b6d9-274">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b6d9-274">See also</span></span>

<span data-ttu-id="9b6d9-275">Para obter mais informações sobre as funções matemáticas que suporta SqlClient, consulte a documentação para a versão do SQL Server que você especificou no manifesto do provedor SqlClient:</span><span class="sxs-lookup"><span data-stu-id="9b6d9-275">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="9b6d9-276">**SQL Server 2005:** [funções matemáticas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="9b6d9-276">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>  
<span data-ttu-id="9b6d9-277">**SQL Server 2008:** [funções matemáticas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="9b6d9-277">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>  
<span data-ttu-id="9b6d9-278">**SQL Server 2012 e posterior:** [funções matemáticas (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="9b6d9-278">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>   

 [<span data-ttu-id="9b6d9-279">SqlClient para funções de Entity Framework</span><span class="sxs-lookup"><span data-stu-id="9b6d9-279">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
