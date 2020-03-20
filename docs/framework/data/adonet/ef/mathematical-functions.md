---
title: Funções Matemáticas
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 4512aaa2eeb3e715a1d6f7a8655912eb15162124
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149759"
---
# <a name="mathematical-functions"></a><span data-ttu-id="f49ab-102">Funções Matemáticas</span><span class="sxs-lookup"><span data-stu-id="f49ab-102">Mathematical Functions</span></span>

<span data-ttu-id="f49ab-103">O provedor de dados. NET Framework para SQL Server (SqlClient) fornece as funções matemáticas que executam cálculos nos valores de entrada que são fornecidos como argumentos, e retorna um resultado de valor numérico.</span><span class="sxs-lookup"><span data-stu-id="f49ab-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="f49ab-104">Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="f49ab-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="f49ab-105">A propriedade de namespace de um provedor permite que o Entity Framework descubra qual prefixo é usado por esse provedor para construções específicas, como tipos e funções.</span><span class="sxs-lookup"><span data-stu-id="f49ab-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="f49ab-106">A tabela a seguir descreve as funções matemáticas SqlClient.</span><span class="sxs-lookup"><span data-stu-id="f49ab-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="f49ab-107">ABS (expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-107">ABS(expression)</span></span>

<span data-ttu-id="f49ab-108">Executa a função de valor absoluto.</span><span class="sxs-lookup"><span data-stu-id="f49ab-108">Performs the absolute value function.</span></span>

<span data-ttu-id="f49ab-109">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-109">**Arguments**</span></span>

<span data-ttu-id="f49ab-110">`expression`: `Int32` `Int64`Um, `Double`ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="f49ab-111">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-111">**Return Value**</span></span>

<span data-ttu-id="f49ab-112">O valor absoluto de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="f49ab-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="f49ab-113">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="f49ab-114">ACOS(expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-114">ACOS(expression)</span></span>

<span data-ttu-id="f49ab-115">Retorna o valor de arccosine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="f49ab-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="f49ab-116">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-116">**Arguments**</span></span>

<span data-ttu-id="f49ab-117">`expression`: um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="f49ab-118">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-118">**Return Value**</span></span>

<span data-ttu-id="f49ab-119">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-119">A `Double`.</span></span>

<span data-ttu-id="f49ab-120">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="f49ab-121">ASIN (expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-121">ASIN(expression)</span></span>

<span data-ttu-id="f49ab-122">Retorna o valor de arcsine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="f49ab-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="f49ab-123">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-123">**Arguments**</span></span>

<span data-ttu-id="f49ab-124">`expression`: um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="f49ab-125">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-125">**Return Value**</span></span>

<span data-ttu-id="f49ab-126">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-126">A `Double`.</span></span>

<span data-ttu-id="f49ab-127">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="f49ab-128">ATAN (expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-128">ATAN(expression)</span></span>

<span data-ttu-id="f49ab-129">Retorna o valor de arctangent de expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="f49ab-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="f49ab-130">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-130">**Arguments**</span></span>

<span data-ttu-id="f49ab-131">`expression`: um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="f49ab-132">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-132">**Return Value**</span></span>

<span data-ttu-id="f49ab-133">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-133">A `Double`.</span></span>

<span data-ttu-id="f49ab-134">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="f49ab-135">ATN2 (expressão, expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="f49ab-136">Retorna o ângulo, em radianos, cuja tangente é entre as duas expressões numéricas especificadas.</span><span class="sxs-lookup"><span data-stu-id="f49ab-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="f49ab-137">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-137">**Arguments**</span></span>

<span data-ttu-id="f49ab-138">`expression`: um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="f49ab-139">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-139">**Return Value**</span></span>

<span data-ttu-id="f49ab-140">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-140">A `Double`.</span></span>

<span data-ttu-id="f49ab-141">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`

## <a name="ceilingexpression"></a><span data-ttu-id="f49ab-142">TETO (expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-142">CEILING(expression)</span></span>

<span data-ttu-id="f49ab-143">Converte a expressão especificada para o inteiro menor que é maior ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="f49ab-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="f49ab-144">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-144">**Arguments**</span></span>

<span data-ttu-id="f49ab-145">`expression`: `Int32` `Int64`Um, `Double`ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="f49ab-146">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-146">**Return Value**</span></span>

<span data-ttu-id="f49ab-147">`Int32`Um, `Int64` `Double`ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="f49ab-148">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-148">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="f49ab-149">COS (expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-149">COS(expression)</span></span>

<span data-ttu-id="f49ab-150">Calcula o cosseno trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="f49ab-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span>

<span data-ttu-id="f49ab-151">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-151">**Arguments**</span></span>

<span data-ttu-id="f49ab-152">`expression`: um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-152">`expression`: A `Double`.</span></span>

<span data-ttu-id="f49ab-153">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-153">**Return Value**</span></span>

<span data-ttu-id="f49ab-154">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-154">A `Double`.</span></span>

<span data-ttu-id="f49ab-155">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-155">**Example**</span></span>

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="f49ab-156">COT (expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-156">COT(expression)</span></span>

<span data-ttu-id="f49ab-157">Calcula o cotangente trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="f49ab-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span>

<span data-ttu-id="f49ab-158">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-158">**Arguments**</span></span>

<span data-ttu-id="f49ab-159">`expression`: um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-159">`expression`: A `Double`.</span></span>

<span data-ttu-id="f49ab-160">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-160">**Return Value**</span></span>

<span data-ttu-id="f49ab-161">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-161">A `Double`.</span></span>

<span data-ttu-id="f49ab-162">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-162">**Example**</span></span>

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="f49ab-163">GRAUS (radianos)</span><span class="sxs-lookup"><span data-stu-id="f49ab-163">DEGREES(radians)</span></span>

<span data-ttu-id="f49ab-164">Retorna o ângulo correspondente em graus.</span><span class="sxs-lookup"><span data-stu-id="f49ab-164">Returns the corresponding angle in degrees.</span></span>

<span data-ttu-id="f49ab-165">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-165">**Arguments**</span></span>

<span data-ttu-id="f49ab-166">`expression`: `Int32` `Int64`Um, `Double`ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="f49ab-167">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-167">**Return Value**</span></span>

<span data-ttu-id="f49ab-168">`Int32`Um, `Int64` `Double`ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="f49ab-169">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-169">**Example**</span></span>

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="f49ab-170">EXP(expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-170">EXP(expression)</span></span>

<span data-ttu-id="f49ab-171">Calcula o valor exponencialmente de uma expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="f49ab-171">Calculates the exponential value of a specified numeric expression.</span></span>

<span data-ttu-id="f49ab-172">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-172">**Arguments**</span></span>

<span data-ttu-id="f49ab-173">`expression`: um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-173">`expression`: A `Double`.</span></span>

<span data-ttu-id="f49ab-174">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-174">**Return Value**</span></span>

<span data-ttu-id="f49ab-175">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-175">A `Double`.</span></span>

<span data-ttu-id="f49ab-176">**Exemplo**`SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="f49ab-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="f49ab-177">PISO (expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-177">FLOOR(expression)</span></span>

<span data-ttu-id="f49ab-178">Converte a expressão especificada para o inteiro maior menor ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="f49ab-178">Converts the specified expression to the largest integer less than or equal to it.</span></span>

<span data-ttu-id="f49ab-179">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-179">**Arguments**</span></span>

<span data-ttu-id="f49ab-180">`expression`: um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-180">`expression`: A `Double`.</span></span>

<span data-ttu-id="f49ab-181">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-181">**Return Value**</span></span>

<span data-ttu-id="f49ab-182">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-182">A `Double`.</span></span>

<span data-ttu-id="f49ab-183">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-183">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="f49ab-184">LOG (expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-184">LOG(expression)</span></span>

<span data-ttu-id="f49ab-185">Calcula o logaritmo natural da expressão especificada de `float` .</span><span class="sxs-lookup"><span data-stu-id="f49ab-185">Calculates the natural logarithm of the specified `float` expression.</span></span>

<span data-ttu-id="f49ab-186">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-186">**Arguments**</span></span>

<span data-ttu-id="f49ab-187">`expression`: um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-187">`expression`: A `Double`.</span></span>

<span data-ttu-id="f49ab-188">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-188">**Return Value**</span></span>

<span data-ttu-id="f49ab-189">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-189">A `Double`.</span></span>

<span data-ttu-id="f49ab-190">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-190">**Example**</span></span>

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="f49ab-191">LOG10(expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-191">LOG10(expression)</span></span>

<span data-ttu-id="f49ab-192">Retorna o logaritmo base-10 de expressão especificada de `Double` .</span><span class="sxs-lookup"><span data-stu-id="f49ab-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span>

<span data-ttu-id="f49ab-193">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-193">**Arguments**</span></span>

<span data-ttu-id="f49ab-194">`expression`: um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-194">`expression`: A `Double`.</span></span>

<span data-ttu-id="f49ab-195">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-195">**Return Value**</span></span>

<span data-ttu-id="f49ab-196">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-196">A `Double`.</span></span>

<span data-ttu-id="f49ab-197">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-197">**Example**</span></span>

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="f49ab-198">PI()</span><span class="sxs-lookup"><span data-stu-id="f49ab-198">PI()</span></span>

<span data-ttu-id="f49ab-199">Retorna o valor constante de pi como `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-199">Returns the constant value of pi as a `Double`.</span></span>

<span data-ttu-id="f49ab-200">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-200">**Return Value**</span></span>

<span data-ttu-id="f49ab-201">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-201">A `Double`.</span></span>

<span data-ttu-id="f49ab-202">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-202">**Example**</span></span>

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="f49ab-203">(numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="f49ab-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="f49ab-204">Calcula o valor de uma expressão especificada em uma potência especificada.</span><span class="sxs-lookup"><span data-stu-id="f49ab-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="f49ab-205">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-205">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="f49ab-206">`Int32`Um, `Int64` `Double`ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="f49ab-207">Um `Double` que representa o poder para `numeric_expression`elevar o .</span><span class="sxs-lookup"><span data-stu-id="f49ab-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>|

<span data-ttu-id="f49ab-208">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-208">**Return Value**</span></span>

<span data-ttu-id="f49ab-209">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="f49ab-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="f49ab-210">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-210">**Example**</span></span>

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="f49ab-211">RADIANS (expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-211">RADIANS(expression)</span></span>

<span data-ttu-id="f49ab-212">Converte graus em radianos.</span><span class="sxs-lookup"><span data-stu-id="f49ab-212">Converts degrees to radians.</span></span>

<span data-ttu-id="f49ab-213">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-213">**Arguments**</span></span>

<span data-ttu-id="f49ab-214">`expression`: `Int32` `Int64`Um, `Double`ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="f49ab-215">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-215">**Return Value**</span></span>

<span data-ttu-id="f49ab-216">`Int32`Um, `Int64` `Double`ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="f49ab-217">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-217">**Example**</span></span>

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="f49ab-218">RAND([semente])</span><span class="sxs-lookup"><span data-stu-id="f49ab-218">RAND([seed])</span></span>

<span data-ttu-id="f49ab-219">Retorna um valor aleatório de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="f49ab-219">Returns a random value from 0 through 1.</span></span>

<span data-ttu-id="f49ab-220">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-220">**Arguments**</span></span>

<span data-ttu-id="f49ab-221">O valor da `Int32`semente como um .</span><span class="sxs-lookup"><span data-stu-id="f49ab-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="f49ab-222">Se a semente não for especificada, o mecanismo de base de dados SQL Server atribui um valor semente aleatoriamente.</span><span class="sxs-lookup"><span data-stu-id="f49ab-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="f49ab-223">Para um valor de semente especificado, o resultado retornado é sempre o mesmo.</span><span class="sxs-lookup"><span data-stu-id="f49ab-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="f49ab-224">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-224">**Return Value**</span></span>

<span data-ttu-id="f49ab-225">Um valor aleatório de 0 a 1. de `Double` .</span><span class="sxs-lookup"><span data-stu-id="f49ab-225">A random `Double` value from 0 through 1.</span></span>

<span data-ttu-id="f49ab-226">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-226">**Example**</span></span>

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="f49ab-227">ROUND(numeric_expression, comprimento[,função])</span><span class="sxs-lookup"><span data-stu-id="f49ab-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="f49ab-228">Retorna uma expressão numérica, arredondada para o comprimento ou a precisão especificada.</span><span class="sxs-lookup"><span data-stu-id="f49ab-228">Returns a numeric expression, rounded to the specified length or precision.</span></span>

<span data-ttu-id="f49ab-229">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-229">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="f49ab-230">`Int32`Um, `Int64` `Double`ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>
|`length`| <span data-ttu-id="f49ab-231">Um `Int32` que representa a `numeric_expression` precisão a que deve ser arredondado.</span><span class="sxs-lookup"><span data-stu-id="f49ab-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="f49ab-232">Quando `length` é um número positivo, `numeric_expression` ele é arredondado para o número de posições decimais especificadas por `length`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="f49ab-233">Quando `length` é um número negativo, `numeric_expression` é arredondado no lado esquerdo do ponto decimal, como especificado por `length`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="f49ab-234">Opcional.</span><span class="sxs-lookup"><span data-stu-id="f49ab-234">Optional.</span></span> <span data-ttu-id="f49ab-235">Um `Int32` que representa o tipo de operação a ser realizado.</span><span class="sxs-lookup"><span data-stu-id="f49ab-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="f49ab-236">Quando a função é omitida `numeric_expression` ou tem um valor de 0 (padrão), é arredondada.</span><span class="sxs-lookup"><span data-stu-id="f49ab-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="f49ab-237">Quando um valor diferente de `numeric_expression` 0 é especificado, é truncado.</span><span class="sxs-lookup"><span data-stu-id="f49ab-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="f49ab-238">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-238">**Return Value**</span></span>

<span data-ttu-id="f49ab-239">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="f49ab-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="f49ab-240">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-240">**Example**</span></span>

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="f49ab-241">SIGN(expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-241">SIGN(expression)</span></span>

<span data-ttu-id="f49ab-242">Retorna o sinal positivo (+1), zero (0) ou sinal negativo (-1) da expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="f49ab-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span>

<span data-ttu-id="f49ab-243">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-243">**Arguments**</span></span>

<span data-ttu-id="f49ab-244">`expression`: `Int32`, `Int64`, `Double` ou `Decimal`</span><span class="sxs-lookup"><span data-stu-id="f49ab-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span>

<span data-ttu-id="f49ab-245">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-245">**Return Value**</span></span>

<span data-ttu-id="f49ab-246">`Int32`Um, `Int64` `Double`ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="f49ab-247">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-247">**Example**</span></span>

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="f49ab-248">SIN (expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-248">SIN(expression)</span></span>

<span data-ttu-id="f49ab-249">Calcula o seno trigonométricas do ângulo especificado em radianos, e retorna uma expressão de `Double` .</span><span class="sxs-lookup"><span data-stu-id="f49ab-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span>

<span data-ttu-id="f49ab-250">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-250">**Arguments**</span></span>

<span data-ttu-id="f49ab-251">`expression`: um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-251">`expression`: A `Double`.</span></span>

<span data-ttu-id="f49ab-252">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-252">**Return Value**</span></span>

<span data-ttu-id="f49ab-253">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-253">A `Double`.</span></span>

<span data-ttu-id="f49ab-254">**Exemplo**`SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="f49ab-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="f49ab-255">SQRT(expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-255">SQRT(expression)</span></span>

<span data-ttu-id="f49ab-256">Retorna a raiz quadrada de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="f49ab-256">Returns the square root of the specified expression.</span></span>

<span data-ttu-id="f49ab-257">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-257">**Arguments**</span></span>

<span data-ttu-id="f49ab-258">`expression`: um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-258">`expression`: A `Double`.</span></span>

<span data-ttu-id="f49ab-259">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-259">**Return Value**</span></span>

<span data-ttu-id="f49ab-260">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-260">A `Double`.</span></span>

<span data-ttu-id="f49ab-261">**Exemplo**`SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="f49ab-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="f49ab-262">QUADRADO (expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-262">SQUARE(expression)</span></span>

<span data-ttu-id="f49ab-263">Retorna o quadrado de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="f49ab-263">Returns the square of the specified expression.</span></span>

<span data-ttu-id="f49ab-264">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-264">**Arguments**</span></span>

<span data-ttu-id="f49ab-265">`expression`: um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-265">`expression`: A `Double`.</span></span>

<span data-ttu-id="f49ab-266">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-266">**Return Value**</span></span>

<span data-ttu-id="f49ab-267">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="f49ab-267">A `Double`.</span></span>

<span data-ttu-id="f49ab-268">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-268">**Example**</span></span>

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="f49ab-269">TAN (expressão)</span><span class="sxs-lookup"><span data-stu-id="f49ab-269">TAN(expression)</span></span>

<span data-ttu-id="f49ab-270">Calcula a tangente de uma expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="f49ab-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="f49ab-271">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="f49ab-271">**Arguments**</span></span>

<span data-ttu-id="f49ab-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="f49ab-272">`expression`: `Double`</span></span>

<span data-ttu-id="f49ab-273">**Valor de Retorno**</span><span class="sxs-lookup"><span data-stu-id="f49ab-273">**Return Value**</span></span>

`Double`

<span data-ttu-id="f49ab-274">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f49ab-274">**Example**</span></span>

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="f49ab-275">Confira também</span><span class="sxs-lookup"><span data-stu-id="f49ab-275">See also</span></span>

- [<span data-ttu-id="f49ab-276">Funções matemáticas (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f49ab-276">Mathematical Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [<span data-ttu-id="f49ab-277">SqlClient para funções de Entity Framework</span><span class="sxs-lookup"><span data-stu-id="f49ab-277">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
