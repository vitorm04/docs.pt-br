---
title: Funções matemáticas
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 664d1a4f67ecced6713f83bf3dd11931c9b4dc18
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699995"
---
# <a name="mathematical-functions"></a><span data-ttu-id="2acd4-102">Funções matemáticas</span><span class="sxs-lookup"><span data-stu-id="2acd4-102">Mathematical Functions</span></span>

<span data-ttu-id="2acd4-103">O provedor de dados. NET Framework para SQL Server (SqlClient) fornece as funções matemáticas que executam cálculos nos valores de entrada que são fornecidos como argumentos, e retorna um resultado de valor numérico.</span><span class="sxs-lookup"><span data-stu-id="2acd4-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="2acd4-104">Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="2acd4-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="2acd4-105">A propriedade de namespace de um provedor permite que o Entity Framework descubra qual prefixo é usado por esse provedor para construções específicas, como tipos e funções.</span><span class="sxs-lookup"><span data-stu-id="2acd4-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="2acd4-106">A tabela a seguir descreve as funções matemáticas do SqlClient.</span><span class="sxs-lookup"><span data-stu-id="2acd4-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="2acd4-107">ABS (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-107">ABS(expression)</span></span>

<span data-ttu-id="2acd4-108">Executa a função de valor absoluto.</span><span class="sxs-lookup"><span data-stu-id="2acd4-108">Performs the absolute value function.</span></span>

<span data-ttu-id="2acd4-109">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-109">**Arguments**</span></span>

<span data-ttu-id="2acd4-110">`expression`: Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2acd4-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="2acd4-111">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-111">**Return Value**</span></span>

<span data-ttu-id="2acd4-112">O valor absoluto de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="2acd4-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="2acd4-113">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="2acd4-114">ACOS (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-114">ACOS(expression)</span></span>

<span data-ttu-id="2acd4-115">Retorna o valor de arccosine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="2acd4-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="2acd4-116">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-116">**Arguments**</span></span>

<span data-ttu-id="2acd4-117">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="2acd4-118">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-118">**Return Value**</span></span>

<span data-ttu-id="2acd4-119">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-119">A `Double`.</span></span>

<span data-ttu-id="2acd4-120">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="2acd4-121">ASIN(expression)</span><span class="sxs-lookup"><span data-stu-id="2acd4-121">ASIN(expression)</span></span>

<span data-ttu-id="2acd4-122">Retorna o valor de arcsine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="2acd4-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="2acd4-123">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-123">**Arguments**</span></span>

<span data-ttu-id="2acd4-124">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="2acd4-125">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-125">**Return Value**</span></span>

<span data-ttu-id="2acd4-126">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-126">A `Double`.</span></span>

<span data-ttu-id="2acd4-127">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="2acd4-128">ATAN (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-128">ATAN(expression)</span></span>

<span data-ttu-id="2acd4-129">Retorna o valor de arctangent de expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="2acd4-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="2acd4-130">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-130">**Arguments**</span></span>

<span data-ttu-id="2acd4-131">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="2acd4-132">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-132">**Return Value**</span></span>

<span data-ttu-id="2acd4-133">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-133">A `Double`.</span></span>

<span data-ttu-id="2acd4-134">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="2acd4-135">ATN2 (expressão, expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="2acd4-136">Retorna o ângulo, em radianos, cuja tangente é entre as duas expressões numéricas especificadas.</span><span class="sxs-lookup"><span data-stu-id="2acd4-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="2acd4-137">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-137">**Arguments**</span></span>

<span data-ttu-id="2acd4-138">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="2acd4-139">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-139">**Return Value**</span></span>

<span data-ttu-id="2acd4-140">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-140">A `Double`.</span></span>

<span data-ttu-id="2acd4-141">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="2acd4-142">TETO (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-142">CEILING(expression)</span></span>

<span data-ttu-id="2acd4-143">Converte a expressão especificada para o inteiro menor que é maior ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="2acd4-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="2acd4-144">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-144">**Arguments**</span></span>

<span data-ttu-id="2acd4-145">`expression`: Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2acd4-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="2acd4-146">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-146">**Return Value**</span></span>

<span data-ttu-id="2acd4-147">Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2acd4-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="2acd4-148">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-148">**Example**</span></span> 

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="2acd4-149">COS (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-149">COS(expression)</span></span>

<span data-ttu-id="2acd4-150">Calcula o cosseno trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="2acd4-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="2acd4-151">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-151">**Arguments**</span></span> 

<span data-ttu-id="2acd4-152">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="2acd4-153">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-153">**Return Value**</span></span> 

<span data-ttu-id="2acd4-154">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-154">A `Double`.</span></span> 

<span data-ttu-id="2acd4-155">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="2acd4-156">COT (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-156">COT(expression)</span></span>

<span data-ttu-id="2acd4-157">Calcula o cotangente trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="2acd4-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="2acd4-158">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-158">**Arguments**</span></span> 

<span data-ttu-id="2acd4-159">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="2acd4-160">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-160">**Return Value**</span></span> 

<span data-ttu-id="2acd4-161">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-161">A `Double`.</span></span> 

<span data-ttu-id="2acd4-162">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="2acd4-163">GRAUS (radianos)</span><span class="sxs-lookup"><span data-stu-id="2acd4-163">DEGREES(radians)</span></span>

<span data-ttu-id="2acd4-164">Retorna o ângulo correspondente em graus.</span><span class="sxs-lookup"><span data-stu-id="2acd4-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="2acd4-165">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-165">**Arguments**</span></span> 

<span data-ttu-id="2acd4-166">`expression`: Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2acd4-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="2acd4-167">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-167">**Return Value**</span></span> 

<span data-ttu-id="2acd4-168">Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2acd4-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="2acd4-169">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="2acd4-170">EXP (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-170">EXP(expression)</span></span>

<span data-ttu-id="2acd4-171">Calcula o valor exponencialmente de uma expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="2acd4-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="2acd4-172">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-172">**Arguments**</span></span> 

<span data-ttu-id="2acd4-173">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="2acd4-174">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-174">**Return Value**</span></span> 

<span data-ttu-id="2acd4-175">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-175">A `Double`.</span></span> 

<span data-ttu-id="2acd4-176">**Exemplo**`SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="2acd4-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="2acd4-177">FLOOR (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-177">FLOOR(expression)</span></span>

<span data-ttu-id="2acd4-178">Converte a expressão especificada para o inteiro maior menor ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="2acd4-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="2acd4-179">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-179">**Arguments**</span></span> 

<span data-ttu-id="2acd4-180">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="2acd4-181">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-181">**Return Value**</span></span> 

<span data-ttu-id="2acd4-182">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-182">A `Double`.</span></span> 

<span data-ttu-id="2acd4-183">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-183">**Example**</span></span> 

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="2acd4-184">LOG (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-184">LOG(expression)</span></span>

<span data-ttu-id="2acd4-185">Calcula o logaritmo natural da expressão especificada de `float` .</span><span class="sxs-lookup"><span data-stu-id="2acd4-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="2acd4-186">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-186">**Arguments**</span></span> 

<span data-ttu-id="2acd4-187">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="2acd4-188">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-188">**Return Value**</span></span> 

<span data-ttu-id="2acd4-189">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-189">A `Double`.</span></span> 

<span data-ttu-id="2acd4-190">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="2acd4-191">LOG10 (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-191">LOG10(expression)</span></span>

<span data-ttu-id="2acd4-192">Retorna o logaritmo base-10 de expressão especificada de `Double` .</span><span class="sxs-lookup"><span data-stu-id="2acd4-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="2acd4-193">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-193">**Arguments**</span></span> 

<span data-ttu-id="2acd4-194">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="2acd4-195">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-195">**Return Value**</span></span> 

<span data-ttu-id="2acd4-196">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-196">A `Double`.</span></span> 

<span data-ttu-id="2acd4-197">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="2acd4-198">PI ()</span><span class="sxs-lookup"><span data-stu-id="2acd4-198">PI()</span></span>

<span data-ttu-id="2acd4-199">Retorna o valor constante de pi como `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="2acd4-200">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-200">**Return Value**</span></span> 

<span data-ttu-id="2acd4-201">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-201">A `Double`.</span></span> 

<span data-ttu-id="2acd4-202">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="2acd4-203">POWER (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="2acd4-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="2acd4-204">Calcula o valor de uma expressão especificada em uma potência especificada.</span><span class="sxs-lookup"><span data-stu-id="2acd4-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="2acd4-205">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="2acd4-206">Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2acd4-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="2acd4-207">Um `Double` que representa o poder para o qual gerar o `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="2acd4-208">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-208">**Return Value**</span></span> 

<span data-ttu-id="2acd4-209">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="2acd4-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="2acd4-210">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="2acd4-211">RADIANOs (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-211">RADIANS(expression)</span></span>

<span data-ttu-id="2acd4-212">Converte graus a radianos.</span><span class="sxs-lookup"><span data-stu-id="2acd4-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="2acd4-213">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-213">**Arguments**</span></span> 

<span data-ttu-id="2acd4-214">`expression`: Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2acd4-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="2acd4-215">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-215">**Return Value**</span></span> 

<span data-ttu-id="2acd4-216">Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2acd4-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="2acd4-217">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="2acd4-218">RAND ([semente])</span><span class="sxs-lookup"><span data-stu-id="2acd4-218">RAND([seed])</span></span>

<span data-ttu-id="2acd4-219">Retorna um valor aleatório de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="2acd4-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="2acd4-220">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-220">**Arguments**</span></span> 

<span data-ttu-id="2acd4-221">O valor de semente como `Int32`um.</span><span class="sxs-lookup"><span data-stu-id="2acd4-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="2acd4-222">Se a semente não for especificada, o mecanismo de base de dados SQL Server atribui um valor semente aleatoriamente.</span><span class="sxs-lookup"><span data-stu-id="2acd4-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="2acd4-223">Para um valor semente especificado, o resultado retornado é sempre o mesmo.</span><span class="sxs-lookup"><span data-stu-id="2acd4-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="2acd4-224">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-224">**Return Value**</span></span> 

<span data-ttu-id="2acd4-225">Um valor aleatório de 0 a 1. de `Double` .</span><span class="sxs-lookup"><span data-stu-id="2acd4-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="2acd4-226">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="2acd4-227">ROUND (numeric_expression, comprimento [, função])</span><span class="sxs-lookup"><span data-stu-id="2acd4-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="2acd4-228">Retorna uma expressão numérica, arredondada para o comprimento ou a precisão especificada.</span><span class="sxs-lookup"><span data-stu-id="2acd4-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="2acd4-229">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="2acd4-230">Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2acd4-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="2acd4-231">Um `Int32` que representa a precisão `numeric_expression` a ser arredondado.</span><span class="sxs-lookup"><span data-stu-id="2acd4-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="2acd4-232">Quando `length` é um número positivo, `numeric_expression` ele é arredondado para o número de posições decimais especificadas por `length`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="2acd4-233">Quando `length` é um número negativo, `numeric_expression` é arredondado no lado esquerdo do ponto decimal, como especificado por `length`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="2acd4-234">Opcional.</span><span class="sxs-lookup"><span data-stu-id="2acd4-234">Optional.</span></span> <span data-ttu-id="2acd4-235">Um `Int32` que representa o tipo de operação a ser executada.</span><span class="sxs-lookup"><span data-stu-id="2acd4-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="2acd4-236">Quando a função é omitida ou tem um valor de 0 (padrão `numeric_expression` ), é arredondado.</span><span class="sxs-lookup"><span data-stu-id="2acd4-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="2acd4-237">Quando um valor diferente de 0 é especificado, `numeric_expression` é truncado.</span><span class="sxs-lookup"><span data-stu-id="2acd4-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="2acd4-238">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-238">**Return Value**</span></span> 

<span data-ttu-id="2acd4-239">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="2acd4-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="2acd4-240">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="2acd4-241">ASSINAR (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-241">SIGN(expression)</span></span> 

<span data-ttu-id="2acd4-242">Retorna o positivo (+1), 0 (zero), ou (- o sinal de subtração de 1) da expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="2acd4-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="2acd4-243">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-243">**Arguments**</span></span> 

<span data-ttu-id="2acd4-244">`expression`: `Int32`, `Int64`, `Double` ou `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2acd4-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="2acd4-245">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-245">**Return Value**</span></span> 

<span data-ttu-id="2acd4-246">Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2acd4-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="2acd4-247">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="2acd4-248">SIN(expression)</span><span class="sxs-lookup"><span data-stu-id="2acd4-248">SIN(expression)</span></span>

<span data-ttu-id="2acd4-249">Calcula o seno trigonométricas do ângulo especificado em radianos, e retorna uma expressão de `Double` .</span><span class="sxs-lookup"><span data-stu-id="2acd4-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="2acd4-250">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-250">**Arguments**</span></span> 

<span data-ttu-id="2acd4-251">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="2acd4-252">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-252">**Return Value**</span></span> 

<span data-ttu-id="2acd4-253">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-253">A `Double`.</span></span> 

<span data-ttu-id="2acd4-254">**Exemplo**`SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="2acd4-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="2acd4-255">SQRT (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-255">SQRT(expression)</span></span>

<span data-ttu-id="2acd4-256">Retorna a raiz quadrada de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="2acd4-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="2acd4-257">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-257">**Arguments**</span></span> 

<span data-ttu-id="2acd4-258">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="2acd4-259">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-259">**Return Value**</span></span> 

<span data-ttu-id="2acd4-260">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-260">A `Double`.</span></span> 

<span data-ttu-id="2acd4-261">**Exemplo**`SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="2acd4-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="2acd4-262">SQUARE (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-262">SQUARE(expression)</span></span>

<span data-ttu-id="2acd4-263">Retorna o quadrado de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="2acd4-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="2acd4-264">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-264">**Arguments**</span></span> 

<span data-ttu-id="2acd4-265">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="2acd4-266">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-266">**Return Value**</span></span> 

<span data-ttu-id="2acd4-267">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2acd4-267">A `Double`.</span></span> 

<span data-ttu-id="2acd4-268">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="2acd4-269">TAN (expressão)</span><span class="sxs-lookup"><span data-stu-id="2acd4-269">TAN(expression)</span></span>

<span data-ttu-id="2acd4-270">Calcula a tangente de uma expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="2acd4-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="2acd4-271">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="2acd4-271">**Arguments**</span></span> 

<span data-ttu-id="2acd4-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="2acd4-272">`expression`: `Double`</span></span> 

<span data-ttu-id="2acd4-273">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="2acd4-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="2acd4-274">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="2acd4-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="2acd4-275">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2acd4-275">See also</span></span>

- [<span data-ttu-id="2acd4-276">Funções matemáticas (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2acd4-276">Mathematical Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [<span data-ttu-id="2acd4-277">SqlClient para funções de Entity Framework</span><span class="sxs-lookup"><span data-stu-id="2acd4-277">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
