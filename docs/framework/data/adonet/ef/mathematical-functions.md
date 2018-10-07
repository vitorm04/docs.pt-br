---
title: Funções matemáticas
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: e6c58d781d7138f8295f2d0a2f0db110ad4b1dd6
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837304"
---
# <a name="mathematical-functions"></a><span data-ttu-id="dc1d1-102">Funções matemáticas</span><span class="sxs-lookup"><span data-stu-id="dc1d1-102">Mathematical Functions</span></span>

<span data-ttu-id="dc1d1-103">O provedor de dados. NET Framework para SQL Server (SqlClient) fornece as funções matemáticas que executam cálculos nos valores de entrada que são fornecidos como argumentos, e retorna um resultado de valor numérico.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="dc1d1-104">Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="dc1d1-105">A propriedade de namespace de um provedor permite que Entity Framework descobrir que prefixo é usado por esse provedor para compilações específicas, como tipos e funções. A tabela a seguir descreve as funções matemáticas SqlClient.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="dc1d1-106">Abs(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-106">ABS(expression)</span></span>

<span data-ttu-id="dc1d1-107">Executa a função de valor absoluto.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-107">Performs the absolute value function.</span></span>

<span data-ttu-id="dc1d1-108">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-108">**Arguments**</span></span>

<span data-ttu-id="dc1d1-109">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-109">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="dc1d1-110">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-110">**Return Value**</span></span>

<span data-ttu-id="dc1d1-111">O valor absoluto de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-111">The absolute value of the specified expression.</span></span>

<span data-ttu-id="dc1d1-112">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-112">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="dc1d1-113">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-113">ACOS(expression)</span></span>

<span data-ttu-id="dc1d1-114">Retorna o valor de arccosine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-114">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="dc1d1-115">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-115">**Arguments**</span></span>

<span data-ttu-id="dc1d1-116">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-116">`expression`: A `Double`.</span></span>

<span data-ttu-id="dc1d1-117">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-117">**Return Value**</span></span>

<span data-ttu-id="dc1d1-118">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-118">A `Double`.</span></span>

<span data-ttu-id="dc1d1-119">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-119">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="dc1d1-120">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-120">ASIN(expression)</span></span>

<span data-ttu-id="dc1d1-121">Retorna o valor de arcsine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-121">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="dc1d1-122">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-122">**Arguments**</span></span>

<span data-ttu-id="dc1d1-123">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-123">`expression`: A `Double`.</span></span>

<span data-ttu-id="dc1d1-124">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-124">**Return Value**</span></span>

<span data-ttu-id="dc1d1-125">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-125">A `Double`.</span></span>

<span data-ttu-id="dc1d1-126">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-126">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="dc1d1-127">ATAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-127">ATAN(expression)</span></span>

<span data-ttu-id="dc1d1-128">Retorna o valor de arctangent de expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-128">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="dc1d1-129">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-129">**Arguments**</span></span>

<span data-ttu-id="dc1d1-130">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-130">`expression`: A `Double`.</span></span>

<span data-ttu-id="dc1d1-131">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-131">**Return Value**</span></span>

<span data-ttu-id="dc1d1-132">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-132">A `Double`.</span></span>

<span data-ttu-id="dc1d1-133">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-133">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="dc1d1-134">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-134">ATN2(expression, expression)</span></span>

<span data-ttu-id="dc1d1-135">Retorna o ângulo, em radianos, cuja tangente é entre as duas expressões numéricas especificadas.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-135">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="dc1d1-136">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-136">**Arguments**</span></span>

<span data-ttu-id="dc1d1-137">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-137">`expression`: A `Double`.</span></span>

<span data-ttu-id="dc1d1-138">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-138">**Return Value**</span></span>

<span data-ttu-id="dc1d1-139">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-139">A `Double`.</span></span>

<span data-ttu-id="dc1d1-140">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-140">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="dc1d1-141">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-141">CEILING(expression)</span></span>

<span data-ttu-id="dc1d1-142">Converte a expressão especificada para o inteiro menor que é maior ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-142">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="dc1d1-143">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-143">**Arguments**</span></span>

<span data-ttu-id="dc1d1-144">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-144">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="dc1d1-145">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-145">**Return Value**</span></span>

<span data-ttu-id="dc1d1-146">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-146">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="dc1d1-147">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-147">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="dc1d1-148">CoS(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-148">COS(expression)</span></span>

<span data-ttu-id="dc1d1-149">Calcula o cosseno trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-149">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="dc1d1-150">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-150">**Arguments**</span></span> 

<span data-ttu-id="dc1d1-151">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-151">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc1d1-152">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-152">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-153">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-153">A `Double`.</span></span> 

<span data-ttu-id="dc1d1-154">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-154">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="dc1d1-155">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-155">COT(expression)</span></span>

<span data-ttu-id="dc1d1-156">Calcula o cotangente trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-156">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="dc1d1-157">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-157">**Arguments**</span></span> 

<span data-ttu-id="dc1d1-158">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-158">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc1d1-159">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-159">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-160">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-160">A `Double`.</span></span> 

<span data-ttu-id="dc1d1-161">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-161">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="dc1d1-162">DEGREES(radians)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-162">DEGREES(radians)</span></span>

<span data-ttu-id="dc1d1-163">Retorna o ângulo correspondente em graus.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-163">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="dc1d1-164">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-164">**Arguments**</span></span> 

<span data-ttu-id="dc1d1-165">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-165">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="dc1d1-166">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-166">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-167">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-167">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="dc1d1-168">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-168">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="dc1d1-169">EXP(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-169">EXP(expression)</span></span>

<span data-ttu-id="dc1d1-170">Calcula o valor exponencialmente de uma expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-170">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="dc1d1-171">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-171">**Arguments**</span></span> 

<span data-ttu-id="dc1d1-172">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-172">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc1d1-173">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-173">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-174">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-174">A `Double`.</span></span> 

<span data-ttu-id="dc1d1-175">**Exemplo** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="dc1d1-175">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="dc1d1-176">Floor(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-176">FLOOR(expression)</span></span>

<span data-ttu-id="dc1d1-177">Converte a expressão especificada para o inteiro maior menor ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-177">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="dc1d1-178">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-178">**Arguments**</span></span> 

<span data-ttu-id="dc1d1-179">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-179">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc1d1-180">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-180">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-181">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-181">A `Double`.</span></span> 

<span data-ttu-id="dc1d1-182">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-182">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="dc1d1-183">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-183">LOG(expression)</span></span>

<span data-ttu-id="dc1d1-184">Calcula o logaritmo natural da expressão especificada de `float` .</span><span class="sxs-lookup"><span data-stu-id="dc1d1-184">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="dc1d1-185">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-185">**Arguments**</span></span> 

<span data-ttu-id="dc1d1-186">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-186">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc1d1-187">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-187">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-188">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-188">A `Double`.</span></span> 

<span data-ttu-id="dc1d1-189">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-189">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="dc1d1-190">LOG10(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-190">LOG10(expression)</span></span>

<span data-ttu-id="dc1d1-191">Retorna o logaritmo base-10 de expressão especificada de `Double` .</span><span class="sxs-lookup"><span data-stu-id="dc1d1-191">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="dc1d1-192">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-192">**Arguments**</span></span> 

<span data-ttu-id="dc1d1-193">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-193">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc1d1-194">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-194">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-195">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-195">A `Double`.</span></span> 

<span data-ttu-id="dc1d1-196">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-196">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="dc1d1-197">PI)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-197">PI()</span></span>

<span data-ttu-id="dc1d1-198">Retorna o valor constante de pi como `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-198">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="dc1d1-199">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-199">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-200">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-200">A `Double`.</span></span> 

<span data-ttu-id="dc1d1-201">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-201">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="dc1d1-202">POWER (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-202">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="dc1d1-203">Calcula o valor de uma expressão especificada em uma potência especificada.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-203">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="dc1d1-204">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-204">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="dc1d1-205">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-205">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="dc1d1-206">Um `Double` que representa a potência à qual elevar o `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-206">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="dc1d1-207">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-207">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-208">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-208">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="dc1d1-209">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-209">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="dc1d1-210">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-210">RADIANS(expression)</span></span>

<span data-ttu-id="dc1d1-211">Converte graus a radianos.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-211">Converts degrees to radians.</span></span> 

<span data-ttu-id="dc1d1-212">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-212">**Arguments**</span></span> 

<span data-ttu-id="dc1d1-213">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-213">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="dc1d1-214">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-214">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-215">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-215">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="dc1d1-216">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-216">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="dc1d1-217">RAND([Seed])</span><span class="sxs-lookup"><span data-stu-id="dc1d1-217">RAND([seed])</span></span>

<span data-ttu-id="dc1d1-218">Retorna um valor aleatório de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-218">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="dc1d1-219">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-219">**Arguments**</span></span> 

<span data-ttu-id="dc1d1-220">O valor de semente como um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-220">The seed value as an `Int32`.</span></span> <span data-ttu-id="dc1d1-221">Se a semente não for especificada, o mecanismo de base de dados SQL Server atribui um valor semente aleatoriamente.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-221">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="dc1d1-222">Para um valor semente especificado, o resultado retornado é sempre o mesmo.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-222">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="dc1d1-223">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-223">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-224">Um valor aleatório de 0 a 1. de `Double` .</span><span class="sxs-lookup"><span data-stu-id="dc1d1-224">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="dc1d1-225">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-225">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="dc1d1-226">Round(Numeric_Expression, Length[,Function])</span><span class="sxs-lookup"><span data-stu-id="dc1d1-226">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="dc1d1-227">Retorna uma expressão numérica, arredondada para o comprimento ou a precisão especificada.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-227">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="dc1d1-228">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-228">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="dc1d1-229">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-229">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="dc1d1-230">Uma `Int32` que representa a precisão para o qual `numeric_expression` deve ser arredondada.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-230">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="dc1d1-231">Quando `length` é um número positivo, `numeric_expression` ele é arredondado para o número de posições decimais especificadas por `length`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-231">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="dc1d1-232">Quando `length` é um número negativo, `numeric_expression` é arredondado no lado esquerdo do ponto decimal, como especificado por `length`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-232">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="dc1d1-233">Opcional.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-233">Optional.</span></span> <span data-ttu-id="dc1d1-234">Um `Int32` que representa o tipo de operação a ser executada.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-234">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="dc1d1-235">Quando a função for omitida ou tem um valor de 0 (padrão), `numeric_expression` é arredondado.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-235">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="dc1d1-236">Quando um valor diferente de 0 for especificado, `numeric_expression` será truncado.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-236">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="dc1d1-237">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-237">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-238">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-238">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="dc1d1-239">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-239">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="dc1d1-240">Sign(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-240">SIGN(expression)</span></span> 

<span data-ttu-id="dc1d1-241">Retorna o positivo (+1), 0 (zero), ou (- o sinal de subtração de 1) da expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-241">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="dc1d1-242">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-242">**Arguments**</span></span> 

<span data-ttu-id="dc1d1-243">`expression`: `Int32`, `Int64`, `Double` ou `Decimal`</span><span class="sxs-lookup"><span data-stu-id="dc1d1-243">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="dc1d1-244">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-244">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-245">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-245">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="dc1d1-246">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-246">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="dc1d1-247">SIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-247">SIN(expression)</span></span>

<span data-ttu-id="dc1d1-248">Calcula o seno trigonométricas do ângulo especificado em radianos, e retorna uma expressão de `Double` .</span><span class="sxs-lookup"><span data-stu-id="dc1d1-248">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="dc1d1-249">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-249">**Arguments**</span></span> 

<span data-ttu-id="dc1d1-250">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-250">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc1d1-251">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-251">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-252">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-252">A `Double`.</span></span> 

<span data-ttu-id="dc1d1-253">**Exemplo** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="dc1d1-253">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="dc1d1-254">Sqrt(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-254">SQRT(expression)</span></span>

<span data-ttu-id="dc1d1-255">Retorna a raiz quadrada de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-255">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="dc1d1-256">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-256">**Arguments**</span></span> 

<span data-ttu-id="dc1d1-257">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-257">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc1d1-258">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-258">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-259">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-259">A `Double`.</span></span> 

<span data-ttu-id="dc1d1-260">**Exemplo** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="dc1d1-260">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="dc1d1-261">SQUARE(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-261">SQUARE(expression)</span></span>

<span data-ttu-id="dc1d1-262">Retorna o quadrado de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-262">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="dc1d1-263">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-263">**Arguments**</span></span> 

<span data-ttu-id="dc1d1-264">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-264">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc1d1-265">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-265">**Return Value**</span></span> 

<span data-ttu-id="dc1d1-266">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-266">A `Double`.</span></span> 

<span data-ttu-id="dc1d1-267">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-267">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="dc1d1-268">TAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-268">TAN(expression)</span></span>

<span data-ttu-id="dc1d1-269">Calcula a tangente de uma expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="dc1d1-269">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="dc1d1-270">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-270">**Arguments**</span></span> 

<span data-ttu-id="dc1d1-271">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="dc1d1-271">`expression`: `Double`</span></span> 

<span data-ttu-id="dc1d1-272">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-272">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="dc1d1-273">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="dc1d1-273">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="dc1d1-274">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc1d1-274">See also</span></span>

<span data-ttu-id="dc1d1-275">Para obter mais informações sobre as funções matemáticas que suporta SqlClient, consulte a documentação para a versão do SQL Server que você especificou no manifesto do provedor SqlClient:</span><span class="sxs-lookup"><span data-stu-id="dc1d1-275">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="dc1d1-276">**SQL Server 2005:** [funções matemáticas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="dc1d1-276">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>  
<span data-ttu-id="dc1d1-277">**SQL Server 2008:** [funções matemáticas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="dc1d1-277">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>  
<span data-ttu-id="dc1d1-278">**SQL Server 2012 e posterior:** [funções matemáticas (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="dc1d1-278">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>   

 [<span data-ttu-id="dc1d1-279">SqlClient para funções de Entity Framework</span><span class="sxs-lookup"><span data-stu-id="dc1d1-279">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
