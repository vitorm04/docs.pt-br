---
title: Funções matemáticas
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 63f83532c399f77e268913da3198327345b9c2ee
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143669"
---
# <a name="mathematical-functions"></a><span data-ttu-id="ec55c-102">Funções matemáticas</span><span class="sxs-lookup"><span data-stu-id="ec55c-102">Mathematical Functions</span></span>

<span data-ttu-id="ec55c-103">O provedor de dados. NET Framework para SQL Server (SqlClient) fornece as funções matemáticas que executam cálculos nos valores de entrada que são fornecidos como argumentos, e retorna um resultado de valor numérico.</span><span class="sxs-lookup"><span data-stu-id="ec55c-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="ec55c-104">Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="ec55c-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="ec55c-105">A propriedade de namespace de um provedor permite que o Entity Framework descubra qual prefixo é usado por esse provedor para construções específicas, como tipos e funções.</span><span class="sxs-lookup"><span data-stu-id="ec55c-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="ec55c-106">A tabela a seguir descreve as funções matemáticas SqlClient.</span><span class="sxs-lookup"><span data-stu-id="ec55c-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="ec55c-107">Abs(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-107">ABS(expression)</span></span>

<span data-ttu-id="ec55c-108">Executa a função de valor absoluto.</span><span class="sxs-lookup"><span data-stu-id="ec55c-108">Performs the absolute value function.</span></span>

<span data-ttu-id="ec55c-109">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-109">**Arguments**</span></span>

<span data-ttu-id="ec55c-110">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="ec55c-111">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-111">**Return Value**</span></span>

<span data-ttu-id="ec55c-112">O valor absoluto de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="ec55c-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="ec55c-113">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="ec55c-114">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-114">ACOS(expression)</span></span>

<span data-ttu-id="ec55c-115">Retorna o valor de arccosine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="ec55c-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="ec55c-116">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-116">**Arguments**</span></span>

<span data-ttu-id="ec55c-117">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="ec55c-118">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-118">**Return Value**</span></span>

<span data-ttu-id="ec55c-119">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-119">A `Double`.</span></span>

<span data-ttu-id="ec55c-120">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="ec55c-121">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-121">ASIN(expression)</span></span>

<span data-ttu-id="ec55c-122">Retorna o valor de arcsine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="ec55c-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="ec55c-123">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-123">**Arguments**</span></span>

<span data-ttu-id="ec55c-124">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="ec55c-125">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-125">**Return Value**</span></span>

<span data-ttu-id="ec55c-126">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-126">A `Double`.</span></span>

<span data-ttu-id="ec55c-127">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="ec55c-128">ATAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-128">ATAN(expression)</span></span>

<span data-ttu-id="ec55c-129">Retorna o valor de arctangent de expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="ec55c-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="ec55c-130">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-130">**Arguments**</span></span>

<span data-ttu-id="ec55c-131">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="ec55c-132">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-132">**Return Value**</span></span>

<span data-ttu-id="ec55c-133">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-133">A `Double`.</span></span>

<span data-ttu-id="ec55c-134">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="ec55c-135">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="ec55c-136">Retorna o ângulo, em radianos, cuja tangente é entre as duas expressões numéricas especificadas.</span><span class="sxs-lookup"><span data-stu-id="ec55c-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="ec55c-137">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-137">**Arguments**</span></span>

<span data-ttu-id="ec55c-138">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="ec55c-139">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-139">**Return Value**</span></span>

<span data-ttu-id="ec55c-140">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-140">A `Double`.</span></span>

<span data-ttu-id="ec55c-141">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="ec55c-142">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-142">CEILING(expression)</span></span>

<span data-ttu-id="ec55c-143">Converte a expressão especificada para o inteiro menor que é maior ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="ec55c-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="ec55c-144">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-144">**Arguments**</span></span>

<span data-ttu-id="ec55c-145">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="ec55c-146">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-146">**Return Value**</span></span>

<span data-ttu-id="ec55c-147">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="ec55c-148">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-148">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="ec55c-149">CoS(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-149">COS(expression)</span></span>

<span data-ttu-id="ec55c-150">Calcula o cosseno trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="ec55c-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="ec55c-151">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-151">**Arguments**</span></span> 

<span data-ttu-id="ec55c-152">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ec55c-153">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-153">**Return Value**</span></span> 

<span data-ttu-id="ec55c-154">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-154">A `Double`.</span></span> 

<span data-ttu-id="ec55c-155">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="ec55c-156">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-156">COT(expression)</span></span>

<span data-ttu-id="ec55c-157">Calcula o cotangente trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="ec55c-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="ec55c-158">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-158">**Arguments**</span></span> 

<span data-ttu-id="ec55c-159">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ec55c-160">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-160">**Return Value**</span></span> 

<span data-ttu-id="ec55c-161">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-161">A `Double`.</span></span> 

<span data-ttu-id="ec55c-162">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="ec55c-163">DEGREES(radians)</span><span class="sxs-lookup"><span data-stu-id="ec55c-163">DEGREES(radians)</span></span>

<span data-ttu-id="ec55c-164">Retorna o ângulo correspondente em graus.</span><span class="sxs-lookup"><span data-stu-id="ec55c-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="ec55c-165">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-165">**Arguments**</span></span> 

<span data-ttu-id="ec55c-166">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="ec55c-167">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-167">**Return Value**</span></span> 

<span data-ttu-id="ec55c-168">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="ec55c-169">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="ec55c-170">EXP(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-170">EXP(expression)</span></span>

<span data-ttu-id="ec55c-171">Calcula o valor exponencialmente de uma expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="ec55c-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="ec55c-172">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-172">**Arguments**</span></span> 

<span data-ttu-id="ec55c-173">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ec55c-174">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-174">**Return Value**</span></span> 

<span data-ttu-id="ec55c-175">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-175">A `Double`.</span></span> 

<span data-ttu-id="ec55c-176">**Exemplo** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="ec55c-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="ec55c-177">Floor(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-177">FLOOR(expression)</span></span>

<span data-ttu-id="ec55c-178">Converte a expressão especificada para o inteiro maior menor ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="ec55c-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="ec55c-179">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-179">**Arguments**</span></span> 

<span data-ttu-id="ec55c-180">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ec55c-181">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-181">**Return Value**</span></span> 

<span data-ttu-id="ec55c-182">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-182">A `Double`.</span></span> 

<span data-ttu-id="ec55c-183">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-183">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="ec55c-184">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-184">LOG(expression)</span></span>

<span data-ttu-id="ec55c-185">Calcula o logaritmo natural da expressão especificada de `float` .</span><span class="sxs-lookup"><span data-stu-id="ec55c-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="ec55c-186">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-186">**Arguments**</span></span> 

<span data-ttu-id="ec55c-187">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ec55c-188">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-188">**Return Value**</span></span> 

<span data-ttu-id="ec55c-189">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-189">A `Double`.</span></span> 

<span data-ttu-id="ec55c-190">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="ec55c-191">LOG10(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-191">LOG10(expression)</span></span>

<span data-ttu-id="ec55c-192">Retorna o logaritmo base-10 de expressão especificada de `Double` .</span><span class="sxs-lookup"><span data-stu-id="ec55c-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="ec55c-193">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-193">**Arguments**</span></span> 

<span data-ttu-id="ec55c-194">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ec55c-195">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-195">**Return Value**</span></span> 

<span data-ttu-id="ec55c-196">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-196">A `Double`.</span></span> 

<span data-ttu-id="ec55c-197">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="ec55c-198">PI)</span><span class="sxs-lookup"><span data-stu-id="ec55c-198">PI()</span></span>

<span data-ttu-id="ec55c-199">Retorna o valor constante de pi como `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="ec55c-200">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-200">**Return Value**</span></span> 

<span data-ttu-id="ec55c-201">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-201">A `Double`.</span></span> 

<span data-ttu-id="ec55c-202">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="ec55c-203">POWER (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="ec55c-204">Calcula o valor de uma expressão especificada em uma potência especificada.</span><span class="sxs-lookup"><span data-stu-id="ec55c-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="ec55c-205">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="ec55c-206">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="ec55c-207">Um `Double` que representa a potência à qual elevar o `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="ec55c-208">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-208">**Return Value**</span></span> 

<span data-ttu-id="ec55c-209">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="ec55c-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="ec55c-210">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="ec55c-211">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-211">RADIANS(expression)</span></span>

<span data-ttu-id="ec55c-212">Converte graus a radianos.</span><span class="sxs-lookup"><span data-stu-id="ec55c-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="ec55c-213">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-213">**Arguments**</span></span> 

<span data-ttu-id="ec55c-214">`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="ec55c-215">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-215">**Return Value**</span></span> 

<span data-ttu-id="ec55c-216">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="ec55c-217">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="ec55c-218">RAND([Seed])</span><span class="sxs-lookup"><span data-stu-id="ec55c-218">RAND([seed])</span></span>

<span data-ttu-id="ec55c-219">Retorna um valor aleatório de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="ec55c-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="ec55c-220">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-220">**Arguments**</span></span> 

<span data-ttu-id="ec55c-221">O valor de semente como um `Int32`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="ec55c-222">Se a semente não for especificada, o mecanismo de base de dados SQL Server atribui um valor semente aleatoriamente.</span><span class="sxs-lookup"><span data-stu-id="ec55c-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="ec55c-223">Para um valor semente especificado, o resultado retornado é sempre o mesmo.</span><span class="sxs-lookup"><span data-stu-id="ec55c-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="ec55c-224">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-224">**Return Value**</span></span> 

<span data-ttu-id="ec55c-225">Um valor aleatório de 0 a 1. de `Double` .</span><span class="sxs-lookup"><span data-stu-id="ec55c-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="ec55c-226">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="ec55c-227">Round(Numeric_Expression, Length[,Function])</span><span class="sxs-lookup"><span data-stu-id="ec55c-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="ec55c-228">Retorna uma expressão numérica, arredondada para o comprimento ou a precisão especificada.</span><span class="sxs-lookup"><span data-stu-id="ec55c-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="ec55c-229">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="ec55c-230">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="ec55c-231">Uma `Int32` que representa a precisão para o qual `numeric_expression` deve ser arredondada.</span><span class="sxs-lookup"><span data-stu-id="ec55c-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="ec55c-232">Quando `length` é um número positivo, `numeric_expression` ele é arredondado para o número de posições decimais especificadas por `length`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="ec55c-233">Quando `length` é um número negativo, `numeric_expression` é arredondado no lado esquerdo do ponto decimal, como especificado por `length`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="ec55c-234">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ec55c-234">Optional.</span></span> <span data-ttu-id="ec55c-235">Um `Int32` que representa o tipo de operação a ser executada.</span><span class="sxs-lookup"><span data-stu-id="ec55c-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="ec55c-236">Quando a função for omitida ou tem um valor de 0 (padrão), `numeric_expression` é arredondado.</span><span class="sxs-lookup"><span data-stu-id="ec55c-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="ec55c-237">Quando um valor diferente de 0 for especificado, `numeric_expression` será truncado.</span><span class="sxs-lookup"><span data-stu-id="ec55c-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="ec55c-238">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-238">**Return Value**</span></span> 

<span data-ttu-id="ec55c-239">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="ec55c-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="ec55c-240">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="ec55c-241">Sign(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-241">SIGN(expression)</span></span> 

<span data-ttu-id="ec55c-242">Retorna o positivo (+1), 0 (zero), ou (- o sinal de subtração de 1) da expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="ec55c-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="ec55c-243">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-243">**Arguments**</span></span> 

<span data-ttu-id="ec55c-244">`expression`: `Int32`, `Int64`, `Double` ou `Decimal`</span><span class="sxs-lookup"><span data-stu-id="ec55c-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="ec55c-245">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-245">**Return Value**</span></span> 

<span data-ttu-id="ec55c-246">Uma `Int32`, `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="ec55c-247">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="ec55c-248">SIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-248">SIN(expression)</span></span>

<span data-ttu-id="ec55c-249">Calcula o seno trigonométricas do ângulo especificado em radianos, e retorna uma expressão de `Double` .</span><span class="sxs-lookup"><span data-stu-id="ec55c-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="ec55c-250">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-250">**Arguments**</span></span> 

<span data-ttu-id="ec55c-251">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ec55c-252">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-252">**Return Value**</span></span> 

<span data-ttu-id="ec55c-253">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-253">A `Double`.</span></span> 

<span data-ttu-id="ec55c-254">**Exemplo** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="ec55c-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="ec55c-255">Sqrt(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-255">SQRT(expression)</span></span>

<span data-ttu-id="ec55c-256">Retorna a raiz quadrada de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="ec55c-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="ec55c-257">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-257">**Arguments**</span></span> 

<span data-ttu-id="ec55c-258">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ec55c-259">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-259">**Return Value**</span></span> 

<span data-ttu-id="ec55c-260">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-260">A `Double`.</span></span> 

<span data-ttu-id="ec55c-261">**Exemplo** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="ec55c-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="ec55c-262">SQUARE(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-262">SQUARE(expression)</span></span>

<span data-ttu-id="ec55c-263">Retorna o quadrado de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="ec55c-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="ec55c-264">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-264">**Arguments**</span></span> 

<span data-ttu-id="ec55c-265">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ec55c-266">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-266">**Return Value**</span></span> 

<span data-ttu-id="ec55c-267">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="ec55c-267">A `Double`.</span></span> 

<span data-ttu-id="ec55c-268">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="ec55c-269">TAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="ec55c-269">TAN(expression)</span></span>

<span data-ttu-id="ec55c-270">Calcula a tangente de uma expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="ec55c-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="ec55c-271">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="ec55c-271">**Arguments**</span></span> 

<span data-ttu-id="ec55c-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="ec55c-272">`expression`: `Double`</span></span> 

<span data-ttu-id="ec55c-273">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="ec55c-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="ec55c-274">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="ec55c-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="ec55c-275">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec55c-275">See also</span></span>

<span data-ttu-id="ec55c-276">Para obter mais informações sobre as funções matemáticas que suporta SqlClient, consulte a documentação para a versão do SQL Server que você especificou no manifesto do provedor SqlClient:</span><span class="sxs-lookup"><span data-stu-id="ec55c-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="ec55c-277">**SQL Server 2005:** [Funções matemáticas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="ec55c-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>  
<span data-ttu-id="ec55c-278">**SQL Server 2008:** [Funções matemáticas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="ec55c-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>  
<span data-ttu-id="ec55c-279">**SQL Server 2012 e posterior:** [Funções matemáticas (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="ec55c-279">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>   

 [<span data-ttu-id="ec55c-280">SqlClient para funções de Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ec55c-280">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
