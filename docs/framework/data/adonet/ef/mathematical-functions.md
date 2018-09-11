---
title: Funções matemáticas
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: e6c58d781d7138f8295f2d0a2f0db110ad4b1dd6
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365632"
---
# <a name="mathematical-functions"></a><span data-ttu-id="9aaa0-102">Funções matemáticas</span><span class="sxs-lookup"><span data-stu-id="9aaa0-102">Mathematical Functions</span></span>

<span data-ttu-id="9aaa0-103">O provedor de dados. NET Framework para SQL Server (SqlClient) fornece as funções matemáticas que executam cálculos nos valores de entrada que são fornecidos como argumentos, e retorna um resultado de valor numérico.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="9aaa0-104">Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="9aaa0-105">A propriedade de namespace de um provedor permite que Entity Framework descobrir que prefixo é usado por esse provedor para compilações específicas, como tipos e funções. A tabela a seguir descreve as funções matemáticas SqlClient.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="9aaa0-106">Abs(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-106">ABS(expression)</span></span>

<span data-ttu-id="9aaa0-107">Executa a função de valor absoluto.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-107">Performs the absolute value function.</span></span>

<span data-ttu-id="9aaa0-108">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-108">**Arguments**</span></span>

<span data-ttu-id="9aaa0-109">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-109">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="9aaa0-110">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-110">**Return Value**</span></span>

<span data-ttu-id="9aaa0-111">O valor absoluto de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-111">The absolute value of the specified expression.</span></span>

<span data-ttu-id="9aaa0-112">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-112">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="9aaa0-113">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-113">ACOS(expression)</span></span>

<span data-ttu-id="9aaa0-114">Retorna o valor de arccosine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-114">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="9aaa0-115">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-115">**Arguments**</span></span>

<span data-ttu-id="9aaa0-116">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-116">`expression`: A `Double`.</span></span>

<span data-ttu-id="9aaa0-117">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-117">**Return Value**</span></span>

<span data-ttu-id="9aaa0-118">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-118">A `Double`.</span></span>

<span data-ttu-id="9aaa0-119">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-119">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="9aaa0-120">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-120">ASIN(expression)</span></span>

<span data-ttu-id="9aaa0-121">Retorna o valor de arcsine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-121">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="9aaa0-122">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-122">**Arguments**</span></span>

<span data-ttu-id="9aaa0-123">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-123">`expression`: A `Double`.</span></span>

<span data-ttu-id="9aaa0-124">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-124">**Return Value**</span></span>

<span data-ttu-id="9aaa0-125">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-125">A `Double`.</span></span>

<span data-ttu-id="9aaa0-126">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-126">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="9aaa0-127">ATAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-127">ATAN(expression)</span></span>

<span data-ttu-id="9aaa0-128">Retorna o valor de arctangent de expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-128">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="9aaa0-129">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-129">**Arguments**</span></span>

<span data-ttu-id="9aaa0-130">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-130">`expression`: A `Double`.</span></span>

<span data-ttu-id="9aaa0-131">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-131">**Return Value**</span></span>

<span data-ttu-id="9aaa0-132">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-132">A `Double`.</span></span>

<span data-ttu-id="9aaa0-133">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-133">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="9aaa0-134">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-134">ATN2(expression, expression)</span></span>

<span data-ttu-id="9aaa0-135">Retorna o ângulo, em radianos, cuja tangente é entre as duas expressões numéricas especificadas.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-135">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="9aaa0-136">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-136">**Arguments**</span></span>

<span data-ttu-id="9aaa0-137">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-137">`expression`: A `Double`.</span></span>

<span data-ttu-id="9aaa0-138">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-138">**Return Value**</span></span>

<span data-ttu-id="9aaa0-139">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-139">A `Double`.</span></span>

<span data-ttu-id="9aaa0-140">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-140">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="9aaa0-141">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-141">CEILING(expression)</span></span>

<span data-ttu-id="9aaa0-142">Converte a expressão especificada para o inteiro menor que é maior ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-142">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="9aaa0-143">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-143">**Arguments**</span></span>

<span data-ttu-id="9aaa0-144">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-144">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="9aaa0-145">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-145">**Return Value**</span></span>

<span data-ttu-id="9aaa0-146">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-146">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="9aaa0-147">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-147">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="9aaa0-148">CoS(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-148">COS(expression)</span></span>

<span data-ttu-id="9aaa0-149">Calcula o cosseno trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-149">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="9aaa0-150">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-150">**Arguments**</span></span> 

<span data-ttu-id="9aaa0-151">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-151">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9aaa0-152">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-152">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-153">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-153">A `Double`.</span></span> 

<span data-ttu-id="9aaa0-154">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-154">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="9aaa0-155">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-155">COT(expression)</span></span>

<span data-ttu-id="9aaa0-156">Calcula o cotangente trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-156">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="9aaa0-157">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-157">**Arguments**</span></span> 

<span data-ttu-id="9aaa0-158">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-158">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9aaa0-159">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-159">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-160">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-160">A `Double`.</span></span> 

<span data-ttu-id="9aaa0-161">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-161">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="9aaa0-162">DEGREES(radians)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-162">DEGREES(radians)</span></span>

<span data-ttu-id="9aaa0-163">Retorna o ângulo correspondente em graus.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-163">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="9aaa0-164">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-164">**Arguments**</span></span> 

<span data-ttu-id="9aaa0-165">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-165">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="9aaa0-166">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-166">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-167">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-167">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="9aaa0-168">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-168">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="9aaa0-169">EXP(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-169">EXP(expression)</span></span>

<span data-ttu-id="9aaa0-170">Calcula o valor exponencialmente de uma expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-170">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="9aaa0-171">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-171">**Arguments**</span></span> 

<span data-ttu-id="9aaa0-172">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-172">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9aaa0-173">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-173">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-174">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-174">A `Double`.</span></span> 

<span data-ttu-id="9aaa0-175">**Exemplo** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="9aaa0-175">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="9aaa0-176">Floor(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-176">FLOOR(expression)</span></span>

<span data-ttu-id="9aaa0-177">Converte a expressão especificada para o inteiro maior menor ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-177">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="9aaa0-178">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-178">**Arguments**</span></span> 

<span data-ttu-id="9aaa0-179">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-179">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9aaa0-180">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-180">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-181">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-181">A `Double`.</span></span> 

<span data-ttu-id="9aaa0-182">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-182">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="9aaa0-183">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-183">LOG(expression)</span></span>

<span data-ttu-id="9aaa0-184">Calcula o logaritmo natural da expressão especificada de `float` .</span><span class="sxs-lookup"><span data-stu-id="9aaa0-184">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="9aaa0-185">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-185">**Arguments**</span></span> 

<span data-ttu-id="9aaa0-186">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-186">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9aaa0-187">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-187">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-188">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-188">A `Double`.</span></span> 

<span data-ttu-id="9aaa0-189">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-189">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="9aaa0-190">LOG10(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-190">LOG10(expression)</span></span>

<span data-ttu-id="9aaa0-191">Retorna o logaritmo base-10 de expressão especificada de `Double` .</span><span class="sxs-lookup"><span data-stu-id="9aaa0-191">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="9aaa0-192">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-192">**Arguments**</span></span> 

<span data-ttu-id="9aaa0-193">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-193">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9aaa0-194">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-194">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-195">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-195">A `Double`.</span></span> 

<span data-ttu-id="9aaa0-196">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-196">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="9aaa0-197">PI)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-197">PI()</span></span>

<span data-ttu-id="9aaa0-198">Retorna o valor constante de pi como `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-198">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="9aaa0-199">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-199">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-200">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-200">A `Double`.</span></span> 

<span data-ttu-id="9aaa0-201">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-201">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="9aaa0-202">POWER (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-202">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="9aaa0-203">Calcula o valor de uma expressão especificada em uma potência especificada.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-203">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="9aaa0-204">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-204">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="9aaa0-205">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-205">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="9aaa0-206">Um `Double` que representa a potência à qual elevar o `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-206">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="9aaa0-207">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-207">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-208">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-208">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="9aaa0-209">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-209">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="9aaa0-210">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-210">RADIANS(expression)</span></span>

<span data-ttu-id="9aaa0-211">Converte graus a radianos.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-211">Converts degrees to radians.</span></span> 

<span data-ttu-id="9aaa0-212">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-212">**Arguments**</span></span> 

<span data-ttu-id="9aaa0-213">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-213">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="9aaa0-214">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-214">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-215">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-215">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="9aaa0-216">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-216">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="9aaa0-217">RAND([Seed])</span><span class="sxs-lookup"><span data-stu-id="9aaa0-217">RAND([seed])</span></span>

<span data-ttu-id="9aaa0-218">Retorna um valor aleatório de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-218">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="9aaa0-219">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-219">**Arguments**</span></span> 

<span data-ttu-id="9aaa0-220">O valor de semente como um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-220">The seed value as an `Int32`.</span></span> <span data-ttu-id="9aaa0-221">Se a semente não for especificada, o mecanismo de base de dados SQL Server atribui um valor semente aleatoriamente.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-221">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="9aaa0-222">Para um valor semente especificado, o resultado retornado é sempre o mesmo.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-222">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="9aaa0-223">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-223">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-224">Um valor aleatório de 0 a 1. de `Double` .</span><span class="sxs-lookup"><span data-stu-id="9aaa0-224">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="9aaa0-225">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-225">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="9aaa0-226">Round(Numeric_Expression, Length[,Function])</span><span class="sxs-lookup"><span data-stu-id="9aaa0-226">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="9aaa0-227">Retorna uma expressão numérica, arredondada para o comprimento ou a precisão especificada.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-227">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="9aaa0-228">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-228">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="9aaa0-229">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-229">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="9aaa0-230">Uma `Int32` que representa a precisão para o qual `numeric_expression` deve ser arredondada.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-230">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="9aaa0-231">Quando `length` é um número positivo, `numeric_expression` ele é arredondado para o número de posições decimais especificadas por `length`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-231">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="9aaa0-232">Quando `length` é um número negativo, `numeric_expression` é arredondado no lado esquerdo do ponto decimal, como especificado por `length`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-232">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="9aaa0-233">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-233">Optional.</span></span> <span data-ttu-id="9aaa0-234">Um `Int32` que representa o tipo de operação a ser executada.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-234">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="9aaa0-235">Quando a função for omitida ou tem um valor de 0 (padrão), `numeric_expression` é arredondado.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-235">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="9aaa0-236">Quando um valor diferente de 0 for especificado, `numeric_expression` será truncado.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-236">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="9aaa0-237">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-237">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-238">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-238">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="9aaa0-239">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-239">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="9aaa0-240">Sign(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-240">SIGN(expression)</span></span> 

<span data-ttu-id="9aaa0-241">Retorna o positivo (+1), 0 (zero), ou (- o sinal de subtração de 1) da expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-241">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="9aaa0-242">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-242">**Arguments**</span></span> 

<span data-ttu-id="9aaa0-243">`expression`: `Int32`, `Int64`, `Double` ou `Decimal`</span><span class="sxs-lookup"><span data-stu-id="9aaa0-243">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="9aaa0-244">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-244">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-245">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-245">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="9aaa0-246">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-246">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="9aaa0-247">SIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-247">SIN(expression)</span></span>

<span data-ttu-id="9aaa0-248">Calcula o seno trigonométricas do ângulo especificado em radianos, e retorna uma expressão de `Double` .</span><span class="sxs-lookup"><span data-stu-id="9aaa0-248">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="9aaa0-249">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-249">**Arguments**</span></span> 

<span data-ttu-id="9aaa0-250">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-250">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9aaa0-251">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-251">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-252">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-252">A `Double`.</span></span> 

<span data-ttu-id="9aaa0-253">**Exemplo** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="9aaa0-253">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="9aaa0-254">Sqrt(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-254">SQRT(expression)</span></span>

<span data-ttu-id="9aaa0-255">Retorna a raiz quadrada de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-255">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="9aaa0-256">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-256">**Arguments**</span></span> 

<span data-ttu-id="9aaa0-257">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-257">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9aaa0-258">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-258">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-259">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-259">A `Double`.</span></span> 

<span data-ttu-id="9aaa0-260">**Exemplo** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="9aaa0-260">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="9aaa0-261">SQUARE(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-261">SQUARE(expression)</span></span>

<span data-ttu-id="9aaa0-262">Retorna o quadrado de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-262">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="9aaa0-263">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-263">**Arguments**</span></span> 

<span data-ttu-id="9aaa0-264">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-264">`expression`: A `Double`.</span></span> 

<span data-ttu-id="9aaa0-265">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-265">**Return Value**</span></span> 

<span data-ttu-id="9aaa0-266">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-266">A `Double`.</span></span> 

<span data-ttu-id="9aaa0-267">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-267">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="9aaa0-268">TAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-268">TAN(expression)</span></span>

<span data-ttu-id="9aaa0-269">Calcula a tangente de uma expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9aaa0-269">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="9aaa0-270">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-270">**Arguments**</span></span> 

<span data-ttu-id="9aaa0-271">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="9aaa0-271">`expression`: `Double`</span></span> 

<span data-ttu-id="9aaa0-272">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-272">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="9aaa0-273">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="9aaa0-273">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="9aaa0-274">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9aaa0-274">See also</span></span>

<span data-ttu-id="9aaa0-275">Para obter mais informações sobre as funções matemáticas que suporta SqlClient, consulte a documentação para a versão do SQL Server que você especificou no manifesto do provedor SqlClient:</span><span class="sxs-lookup"><span data-stu-id="9aaa0-275">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="9aaa0-276">**SQL Server 2005:** [funções matemáticas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="9aaa0-276">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>  
<span data-ttu-id="9aaa0-277">**SQL Server 2008:** [funções matemáticas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="9aaa0-277">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>  
<span data-ttu-id="9aaa0-278">**SQL Server 2012 e posterior:** [funções matemáticas (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="9aaa0-278">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>   

 [<span data-ttu-id="9aaa0-279">SqlClient para funções de Entity Framework</span><span class="sxs-lookup"><span data-stu-id="9aaa0-279">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
