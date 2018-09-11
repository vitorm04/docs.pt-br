---
title: Funções matemáticas
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: e6c58d781d7138f8295f2d0a2f0db110ad4b1dd6
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268945"
---
# <a name="mathematical-functions"></a><span data-ttu-id="c06ce-102">Funções matemáticas</span><span class="sxs-lookup"><span data-stu-id="c06ce-102">Mathematical Functions</span></span>

<span data-ttu-id="c06ce-103">O provedor de dados. NET Framework para SQL Server (SqlClient) fornece as funções matemáticas que executam cálculos nos valores de entrada que são fornecidos como argumentos, e retorna um resultado de valor numérico.</span><span class="sxs-lookup"><span data-stu-id="c06ce-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="c06ce-104">Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="c06ce-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="c06ce-105">A propriedade de namespace de um provedor permite que Entity Framework descobrir que prefixo é usado por esse provedor para compilações específicas, como tipos e funções. A tabela a seguir descreve as funções matemáticas SqlClient.</span><span class="sxs-lookup"><span data-stu-id="c06ce-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="c06ce-106">Abs(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-106">ABS(expression)</span></span>

<span data-ttu-id="c06ce-107">Executa a função de valor absoluto.</span><span class="sxs-lookup"><span data-stu-id="c06ce-107">Performs the absolute value function.</span></span>

<span data-ttu-id="c06ce-108">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-108">**Arguments**</span></span>

<span data-ttu-id="c06ce-109">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-109">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="c06ce-110">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-110">**Return Value**</span></span>

<span data-ttu-id="c06ce-111">O valor absoluto de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="c06ce-111">The absolute value of the specified expression.</span></span>

<span data-ttu-id="c06ce-112">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-112">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="c06ce-113">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-113">ACOS(expression)</span></span>

<span data-ttu-id="c06ce-114">Retorna o valor de arccosine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="c06ce-114">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="c06ce-115">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-115">**Arguments**</span></span>

<span data-ttu-id="c06ce-116">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-116">`expression`: A `Double`.</span></span>

<span data-ttu-id="c06ce-117">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-117">**Return Value**</span></span>

<span data-ttu-id="c06ce-118">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-118">A `Double`.</span></span>

<span data-ttu-id="c06ce-119">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-119">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="c06ce-120">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-120">ASIN(expression)</span></span>

<span data-ttu-id="c06ce-121">Retorna o valor de arcsine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="c06ce-121">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="c06ce-122">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-122">**Arguments**</span></span>

<span data-ttu-id="c06ce-123">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-123">`expression`: A `Double`.</span></span>

<span data-ttu-id="c06ce-124">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-124">**Return Value**</span></span>

<span data-ttu-id="c06ce-125">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-125">A `Double`.</span></span>

<span data-ttu-id="c06ce-126">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-126">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="c06ce-127">ATAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-127">ATAN(expression)</span></span>

<span data-ttu-id="c06ce-128">Retorna o valor de arctangent de expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="c06ce-128">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="c06ce-129">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-129">**Arguments**</span></span>

<span data-ttu-id="c06ce-130">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-130">`expression`: A `Double`.</span></span>

<span data-ttu-id="c06ce-131">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-131">**Return Value**</span></span>

<span data-ttu-id="c06ce-132">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-132">A `Double`.</span></span>

<span data-ttu-id="c06ce-133">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-133">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="c06ce-134">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-134">ATN2(expression, expression)</span></span>

<span data-ttu-id="c06ce-135">Retorna o ângulo, em radianos, cuja tangente é entre as duas expressões numéricas especificadas.</span><span class="sxs-lookup"><span data-stu-id="c06ce-135">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="c06ce-136">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-136">**Arguments**</span></span>

<span data-ttu-id="c06ce-137">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-137">`expression`: A `Double`.</span></span>

<span data-ttu-id="c06ce-138">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-138">**Return Value**</span></span>

<span data-ttu-id="c06ce-139">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-139">A `Double`.</span></span>

<span data-ttu-id="c06ce-140">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-140">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="c06ce-141">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-141">CEILING(expression)</span></span>

<span data-ttu-id="c06ce-142">Converte a expressão especificada para o inteiro menor que é maior ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="c06ce-142">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="c06ce-143">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-143">**Arguments**</span></span>

<span data-ttu-id="c06ce-144">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-144">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="c06ce-145">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-145">**Return Value**</span></span>

<span data-ttu-id="c06ce-146">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-146">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="c06ce-147">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-147">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="c06ce-148">CoS(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-148">COS(expression)</span></span>

<span data-ttu-id="c06ce-149">Calcula o cosseno trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="c06ce-149">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="c06ce-150">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-150">**Arguments**</span></span> 

<span data-ttu-id="c06ce-151">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-151">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c06ce-152">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-152">**Return Value**</span></span> 

<span data-ttu-id="c06ce-153">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-153">A `Double`.</span></span> 

<span data-ttu-id="c06ce-154">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-154">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="c06ce-155">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-155">COT(expression)</span></span>

<span data-ttu-id="c06ce-156">Calcula o cotangente trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="c06ce-156">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="c06ce-157">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-157">**Arguments**</span></span> 

<span data-ttu-id="c06ce-158">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-158">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c06ce-159">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-159">**Return Value**</span></span> 

<span data-ttu-id="c06ce-160">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-160">A `Double`.</span></span> 

<span data-ttu-id="c06ce-161">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-161">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="c06ce-162">DEGREES(radians)</span><span class="sxs-lookup"><span data-stu-id="c06ce-162">DEGREES(radians)</span></span>

<span data-ttu-id="c06ce-163">Retorna o ângulo correspondente em graus.</span><span class="sxs-lookup"><span data-stu-id="c06ce-163">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="c06ce-164">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-164">**Arguments**</span></span> 

<span data-ttu-id="c06ce-165">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-165">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="c06ce-166">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-166">**Return Value**</span></span> 

<span data-ttu-id="c06ce-167">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-167">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="c06ce-168">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-168">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="c06ce-169">EXP(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-169">EXP(expression)</span></span>

<span data-ttu-id="c06ce-170">Calcula o valor exponencialmente de uma expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="c06ce-170">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="c06ce-171">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-171">**Arguments**</span></span> 

<span data-ttu-id="c06ce-172">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-172">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c06ce-173">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-173">**Return Value**</span></span> 

<span data-ttu-id="c06ce-174">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-174">A `Double`.</span></span> 

<span data-ttu-id="c06ce-175">**Exemplo** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="c06ce-175">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="c06ce-176">Floor(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-176">FLOOR(expression)</span></span>

<span data-ttu-id="c06ce-177">Converte a expressão especificada para o inteiro maior menor ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="c06ce-177">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="c06ce-178">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-178">**Arguments**</span></span> 

<span data-ttu-id="c06ce-179">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-179">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c06ce-180">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-180">**Return Value**</span></span> 

<span data-ttu-id="c06ce-181">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-181">A `Double`.</span></span> 

<span data-ttu-id="c06ce-182">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-182">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="c06ce-183">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-183">LOG(expression)</span></span>

<span data-ttu-id="c06ce-184">Calcula o logaritmo natural da expressão especificada de `float` .</span><span class="sxs-lookup"><span data-stu-id="c06ce-184">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="c06ce-185">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-185">**Arguments**</span></span> 

<span data-ttu-id="c06ce-186">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-186">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c06ce-187">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-187">**Return Value**</span></span> 

<span data-ttu-id="c06ce-188">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-188">A `Double`.</span></span> 

<span data-ttu-id="c06ce-189">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-189">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="c06ce-190">LOG10(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-190">LOG10(expression)</span></span>

<span data-ttu-id="c06ce-191">Retorna o logaritmo base-10 de expressão especificada de `Double` .</span><span class="sxs-lookup"><span data-stu-id="c06ce-191">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="c06ce-192">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-192">**Arguments**</span></span> 

<span data-ttu-id="c06ce-193">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-193">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c06ce-194">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-194">**Return Value**</span></span> 

<span data-ttu-id="c06ce-195">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-195">A `Double`.</span></span> 

<span data-ttu-id="c06ce-196">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-196">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="c06ce-197">PI)</span><span class="sxs-lookup"><span data-stu-id="c06ce-197">PI()</span></span>

<span data-ttu-id="c06ce-198">Retorna o valor constante de pi como `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-198">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="c06ce-199">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-199">**Return Value**</span></span> 

<span data-ttu-id="c06ce-200">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-200">A `Double`.</span></span> 

<span data-ttu-id="c06ce-201">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-201">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="c06ce-202">POWER (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-202">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="c06ce-203">Calcula o valor de uma expressão especificada em uma potência especificada.</span><span class="sxs-lookup"><span data-stu-id="c06ce-203">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="c06ce-204">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-204">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="c06ce-205">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-205">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="c06ce-206">Um `Double` que representa a potência à qual elevar o `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-206">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="c06ce-207">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-207">**Return Value**</span></span> 

<span data-ttu-id="c06ce-208">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="c06ce-208">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="c06ce-209">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-209">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="c06ce-210">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-210">RADIANS(expression)</span></span>

<span data-ttu-id="c06ce-211">Converte graus a radianos.</span><span class="sxs-lookup"><span data-stu-id="c06ce-211">Converts degrees to radians.</span></span> 

<span data-ttu-id="c06ce-212">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-212">**Arguments**</span></span> 

<span data-ttu-id="c06ce-213">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-213">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="c06ce-214">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-214">**Return Value**</span></span> 

<span data-ttu-id="c06ce-215">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-215">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="c06ce-216">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-216">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="c06ce-217">RAND([Seed])</span><span class="sxs-lookup"><span data-stu-id="c06ce-217">RAND([seed])</span></span>

<span data-ttu-id="c06ce-218">Retorna um valor aleatório de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="c06ce-218">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="c06ce-219">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-219">**Arguments**</span></span> 

<span data-ttu-id="c06ce-220">O valor de semente como um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-220">The seed value as an `Int32`.</span></span> <span data-ttu-id="c06ce-221">Se a semente não for especificada, o mecanismo de base de dados SQL Server atribui um valor semente aleatoriamente.</span><span class="sxs-lookup"><span data-stu-id="c06ce-221">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="c06ce-222">Para um valor semente especificado, o resultado retornado é sempre o mesmo.</span><span class="sxs-lookup"><span data-stu-id="c06ce-222">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="c06ce-223">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-223">**Return Value**</span></span> 

<span data-ttu-id="c06ce-224">Um valor aleatório de 0 a 1. de `Double` .</span><span class="sxs-lookup"><span data-stu-id="c06ce-224">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="c06ce-225">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-225">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="c06ce-226">Round(Numeric_Expression, Length[,Function])</span><span class="sxs-lookup"><span data-stu-id="c06ce-226">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="c06ce-227">Retorna uma expressão numérica, arredondada para o comprimento ou a precisão especificada.</span><span class="sxs-lookup"><span data-stu-id="c06ce-227">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="c06ce-228">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-228">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="c06ce-229">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-229">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="c06ce-230">Uma `Int32` que representa a precisão para o qual `numeric_expression` deve ser arredondada.</span><span class="sxs-lookup"><span data-stu-id="c06ce-230">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="c06ce-231">Quando `length` é um número positivo, `numeric_expression` ele é arredondado para o número de posições decimais especificadas por `length`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-231">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="c06ce-232">Quando `length` é um número negativo, `numeric_expression` é arredondado no lado esquerdo do ponto decimal, como especificado por `length`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-232">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="c06ce-233">Opcional.</span><span class="sxs-lookup"><span data-stu-id="c06ce-233">Optional.</span></span> <span data-ttu-id="c06ce-234">Um `Int32` que representa o tipo de operação a ser executada.</span><span class="sxs-lookup"><span data-stu-id="c06ce-234">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="c06ce-235">Quando a função for omitida ou tem um valor de 0 (padrão), `numeric_expression` é arredondado.</span><span class="sxs-lookup"><span data-stu-id="c06ce-235">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="c06ce-236">Quando um valor diferente de 0 for especificado, `numeric_expression` será truncado.</span><span class="sxs-lookup"><span data-stu-id="c06ce-236">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="c06ce-237">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-237">**Return Value**</span></span> 

<span data-ttu-id="c06ce-238">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="c06ce-238">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="c06ce-239">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-239">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="c06ce-240">Sign(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-240">SIGN(expression)</span></span> 

<span data-ttu-id="c06ce-241">Retorna o positivo (+1), 0 (zero), ou (- o sinal de subtração de 1) da expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="c06ce-241">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="c06ce-242">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-242">**Arguments**</span></span> 

<span data-ttu-id="c06ce-243">`expression`: `Int32`, `Int64`, `Double` ou `Decimal`</span><span class="sxs-lookup"><span data-stu-id="c06ce-243">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="c06ce-244">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-244">**Return Value**</span></span> 

<span data-ttu-id="c06ce-245">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-245">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="c06ce-246">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-246">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="c06ce-247">SIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-247">SIN(expression)</span></span>

<span data-ttu-id="c06ce-248">Calcula o seno trigonométricas do ângulo especificado em radianos, e retorna uma expressão de `Double` .</span><span class="sxs-lookup"><span data-stu-id="c06ce-248">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="c06ce-249">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-249">**Arguments**</span></span> 

<span data-ttu-id="c06ce-250">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-250">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c06ce-251">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-251">**Return Value**</span></span> 

<span data-ttu-id="c06ce-252">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-252">A `Double`.</span></span> 

<span data-ttu-id="c06ce-253">**Exemplo** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="c06ce-253">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="c06ce-254">Sqrt(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-254">SQRT(expression)</span></span>

<span data-ttu-id="c06ce-255">Retorna a raiz quadrada de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="c06ce-255">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="c06ce-256">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-256">**Arguments**</span></span> 

<span data-ttu-id="c06ce-257">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-257">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c06ce-258">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-258">**Return Value**</span></span> 

<span data-ttu-id="c06ce-259">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-259">A `Double`.</span></span> 

<span data-ttu-id="c06ce-260">**Exemplo** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="c06ce-260">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="c06ce-261">SQUARE(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-261">SQUARE(expression)</span></span>

<span data-ttu-id="c06ce-262">Retorna o quadrado de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="c06ce-262">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="c06ce-263">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-263">**Arguments**</span></span> 

<span data-ttu-id="c06ce-264">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-264">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c06ce-265">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-265">**Return Value**</span></span> 

<span data-ttu-id="c06ce-266">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="c06ce-266">A `Double`.</span></span> 

<span data-ttu-id="c06ce-267">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-267">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="c06ce-268">TAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="c06ce-268">TAN(expression)</span></span>

<span data-ttu-id="c06ce-269">Calcula a tangente de uma expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="c06ce-269">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="c06ce-270">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="c06ce-270">**Arguments**</span></span> 

<span data-ttu-id="c06ce-271">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="c06ce-271">`expression`: `Double`</span></span> 

<span data-ttu-id="c06ce-272">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="c06ce-272">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="c06ce-273">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="c06ce-273">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="c06ce-274">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c06ce-274">See also</span></span>

<span data-ttu-id="c06ce-275">Para obter mais informações sobre as funções matemáticas que suporta SqlClient, consulte a documentação para a versão do SQL Server que você especificou no manifesto do provedor SqlClient:</span><span class="sxs-lookup"><span data-stu-id="c06ce-275">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="c06ce-276">**SQL Server 2005:** [funções matemáticas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="c06ce-276">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>  
<span data-ttu-id="c06ce-277">**SQL Server 2008:** [funções matemáticas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="c06ce-277">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>  
<span data-ttu-id="c06ce-278">**SQL Server 2012 e posterior:** [funções matemáticas (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="c06ce-278">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>   

 [<span data-ttu-id="c06ce-279">SqlClient para funções de Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c06ce-279">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
