---
title: Funções matemáticas
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 5e5658e28c7d806f7fd38f941bfa7254e7806e11
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182487"
---
# <a name="mathematical-functions"></a><span data-ttu-id="3929b-102">Funções matemáticas</span><span class="sxs-lookup"><span data-stu-id="3929b-102">Mathematical Functions</span></span>

<span data-ttu-id="3929b-103">O provedor de dados. NET Framework para SQL Server (SqlClient) fornece as funções matemáticas que executam cálculos nos valores de entrada que são fornecidos como argumentos, e retorna um resultado de valor numérico.</span><span class="sxs-lookup"><span data-stu-id="3929b-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="3929b-104">Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="3929b-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="3929b-105">A propriedade de namespace de um provedor permite que o Entity Framework descubra qual prefixo é usado por esse provedor para construções específicas, como tipos e funções.</span><span class="sxs-lookup"><span data-stu-id="3929b-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="3929b-106">A tabela a seguir descreve as funções matemáticas do SqlClient.</span><span class="sxs-lookup"><span data-stu-id="3929b-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="3929b-107">ABS (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-107">ABS(expression)</span></span>

<span data-ttu-id="3929b-108">Executa a função de valor absoluto.</span><span class="sxs-lookup"><span data-stu-id="3929b-108">Performs the absolute value function.</span></span>

<span data-ttu-id="3929b-109">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-109">**Arguments**</span></span>

<span data-ttu-id="3929b-110">`expression`: Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="3929b-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="3929b-111">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-111">**Return Value**</span></span>

<span data-ttu-id="3929b-112">O valor absoluto de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="3929b-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="3929b-113">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="3929b-114">ACOS (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-114">ACOS(expression)</span></span>

<span data-ttu-id="3929b-115">Retorna o valor de arccosine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="3929b-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="3929b-116">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-116">**Arguments**</span></span>

<span data-ttu-id="3929b-117">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="3929b-118">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-118">**Return Value**</span></span>

<span data-ttu-id="3929b-119">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-119">A `Double`.</span></span>

<span data-ttu-id="3929b-120">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="3929b-121">ASIN(expression)</span><span class="sxs-lookup"><span data-stu-id="3929b-121">ASIN(expression)</span></span>

<span data-ttu-id="3929b-122">Retorna o valor de arcsine de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="3929b-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="3929b-123">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-123">**Arguments**</span></span>

<span data-ttu-id="3929b-124">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="3929b-125">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-125">**Return Value**</span></span>

<span data-ttu-id="3929b-126">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-126">A `Double`.</span></span>

<span data-ttu-id="3929b-127">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="3929b-128">ATAN (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-128">ATAN(expression)</span></span>

<span data-ttu-id="3929b-129">Retorna o valor de arctangent de expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="3929b-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="3929b-130">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-130">**Arguments**</span></span>

<span data-ttu-id="3929b-131">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="3929b-132">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-132">**Return Value**</span></span>

<span data-ttu-id="3929b-133">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-133">A `Double`.</span></span>

<span data-ttu-id="3929b-134">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="3929b-135">ATN2 (expressão, expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="3929b-136">Retorna o ângulo, em radianos, cuja tangente é entre as duas expressões numéricas especificadas.</span><span class="sxs-lookup"><span data-stu-id="3929b-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="3929b-137">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-137">**Arguments**</span></span>

<span data-ttu-id="3929b-138">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="3929b-139">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-139">**Return Value**</span></span>

<span data-ttu-id="3929b-140">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-140">A `Double`.</span></span>

<span data-ttu-id="3929b-141">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="3929b-142">TETO (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-142">CEILING(expression)</span></span>

<span data-ttu-id="3929b-143">Converte a expressão especificada para o inteiro menor que é maior ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="3929b-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="3929b-144">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-144">**Arguments**</span></span>

<span data-ttu-id="3929b-145">`expression`: Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="3929b-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="3929b-146">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-146">**Return Value**</span></span>

<span data-ttu-id="3929b-147">Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="3929b-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="3929b-148">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-148">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="3929b-149">COS (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-149">COS(expression)</span></span>

<span data-ttu-id="3929b-150">Calcula o cosseno trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="3929b-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="3929b-151">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-151">**Arguments**</span></span> 

<span data-ttu-id="3929b-152">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="3929b-153">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-153">**Return Value**</span></span> 

<span data-ttu-id="3929b-154">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-154">A `Double`.</span></span> 

<span data-ttu-id="3929b-155">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="3929b-156">COT (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-156">COT(expression)</span></span>

<span data-ttu-id="3929b-157">Calcula o cotangente trigonométricas do ângulo especificado em radianos.</span><span class="sxs-lookup"><span data-stu-id="3929b-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="3929b-158">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-158">**Arguments**</span></span> 

<span data-ttu-id="3929b-159">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="3929b-160">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-160">**Return Value**</span></span> 

<span data-ttu-id="3929b-161">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-161">A `Double`.</span></span> 

<span data-ttu-id="3929b-162">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="3929b-163">GRAUS (radianos)</span><span class="sxs-lookup"><span data-stu-id="3929b-163">DEGREES(radians)</span></span>

<span data-ttu-id="3929b-164">Retorna o ângulo correspondente em graus.</span><span class="sxs-lookup"><span data-stu-id="3929b-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="3929b-165">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-165">**Arguments**</span></span> 

<span data-ttu-id="3929b-166">`expression`: Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="3929b-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="3929b-167">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-167">**Return Value**</span></span> 

<span data-ttu-id="3929b-168">Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="3929b-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="3929b-169">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="3929b-170">EXP (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-170">EXP(expression)</span></span>

<span data-ttu-id="3929b-171">Calcula o valor exponencialmente de uma expressão numérica especificada.</span><span class="sxs-lookup"><span data-stu-id="3929b-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="3929b-172">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-172">**Arguments**</span></span> 

<span data-ttu-id="3929b-173">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="3929b-174">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-174">**Return Value**</span></span> 

<span data-ttu-id="3929b-175">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-175">A `Double`.</span></span> 

<span data-ttu-id="3929b-176">**Exemplo**`SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="3929b-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="3929b-177">FLOOR (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-177">FLOOR(expression)</span></span>

<span data-ttu-id="3929b-178">Converte a expressão especificada para o inteiro maior menor ou igual a ele.</span><span class="sxs-lookup"><span data-stu-id="3929b-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="3929b-179">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-179">**Arguments**</span></span> 

<span data-ttu-id="3929b-180">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="3929b-181">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-181">**Return Value**</span></span> 

<span data-ttu-id="3929b-182">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-182">A `Double`.</span></span> 

<span data-ttu-id="3929b-183">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-183">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="3929b-184">LOG (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-184">LOG(expression)</span></span>

<span data-ttu-id="3929b-185">Calcula o logaritmo natural da expressão especificada de `float` .</span><span class="sxs-lookup"><span data-stu-id="3929b-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="3929b-186">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-186">**Arguments**</span></span> 

<span data-ttu-id="3929b-187">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="3929b-188">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-188">**Return Value**</span></span> 

<span data-ttu-id="3929b-189">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-189">A `Double`.</span></span> 

<span data-ttu-id="3929b-190">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="3929b-191">LOG10 (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-191">LOG10(expression)</span></span>

<span data-ttu-id="3929b-192">Retorna o logaritmo base-10 de expressão especificada de `Double` .</span><span class="sxs-lookup"><span data-stu-id="3929b-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="3929b-193">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-193">**Arguments**</span></span> 

<span data-ttu-id="3929b-194">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="3929b-195">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-195">**Return Value**</span></span> 

<span data-ttu-id="3929b-196">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-196">A `Double`.</span></span> 

<span data-ttu-id="3929b-197">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="3929b-198">PI ()</span><span class="sxs-lookup"><span data-stu-id="3929b-198">PI()</span></span>

<span data-ttu-id="3929b-199">Retorna o valor constante de pi como `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="3929b-200">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-200">**Return Value**</span></span> 

<span data-ttu-id="3929b-201">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-201">A `Double`.</span></span> 

<span data-ttu-id="3929b-202">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="3929b-203">POWER (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="3929b-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="3929b-204">Calcula o valor de uma expressão especificada em uma potência especificada.</span><span class="sxs-lookup"><span data-stu-id="3929b-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="3929b-205">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="3929b-206">Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="3929b-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="3929b-207">Um `Double` que representa o poder para o qual gerar o `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="3929b-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="3929b-208">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-208">**Return Value**</span></span> 

<span data-ttu-id="3929b-209">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="3929b-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="3929b-210">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="3929b-211">RADIANOs (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-211">RADIANS(expression)</span></span>

<span data-ttu-id="3929b-212">Converte graus a radianos.</span><span class="sxs-lookup"><span data-stu-id="3929b-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="3929b-213">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-213">**Arguments**</span></span> 

<span data-ttu-id="3929b-214">`expression`: Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="3929b-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="3929b-215">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-215">**Return Value**</span></span> 

<span data-ttu-id="3929b-216">Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="3929b-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="3929b-217">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="3929b-218">RAND ([semente])</span><span class="sxs-lookup"><span data-stu-id="3929b-218">RAND([seed])</span></span>

<span data-ttu-id="3929b-219">Retorna um valor aleatório de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="3929b-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="3929b-220">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-220">**Arguments**</span></span> 

<span data-ttu-id="3929b-221">O valor de semente como `Int32`um.</span><span class="sxs-lookup"><span data-stu-id="3929b-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="3929b-222">Se a semente não for especificada, o mecanismo de base de dados SQL Server atribui um valor semente aleatoriamente.</span><span class="sxs-lookup"><span data-stu-id="3929b-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="3929b-223">Para um valor semente especificado, o resultado retornado é sempre o mesmo.</span><span class="sxs-lookup"><span data-stu-id="3929b-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="3929b-224">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-224">**Return Value**</span></span> 

<span data-ttu-id="3929b-225">Um valor aleatório de 0 a 1. de `Double` .</span><span class="sxs-lookup"><span data-stu-id="3929b-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="3929b-226">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="3929b-227">ROUND (numeric_expression, comprimento [, função])</span><span class="sxs-lookup"><span data-stu-id="3929b-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="3929b-228">Retorna uma expressão numérica, arredondada para o comprimento ou a precisão especificada.</span><span class="sxs-lookup"><span data-stu-id="3929b-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="3929b-229">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="3929b-230">Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="3929b-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="3929b-231">Um `Int32` que representa a precisão `numeric_expression` a ser arredondado.</span><span class="sxs-lookup"><span data-stu-id="3929b-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="3929b-232">Quando `length` é um número positivo, `numeric_expression` ele é arredondado para o número de posições decimais especificadas por `length`.</span><span class="sxs-lookup"><span data-stu-id="3929b-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="3929b-233">Quando `length` é um número negativo, `numeric_expression` é arredondado no lado esquerdo do ponto decimal, como especificado por `length`.</span><span class="sxs-lookup"><span data-stu-id="3929b-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="3929b-234">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3929b-234">Optional.</span></span> <span data-ttu-id="3929b-235">Um `Int32` que representa o tipo de operação a ser executada.</span><span class="sxs-lookup"><span data-stu-id="3929b-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="3929b-236">Quando a função é omitida ou tem um valor de 0 (padrão `numeric_expression` ), é arredondado.</span><span class="sxs-lookup"><span data-stu-id="3929b-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="3929b-237">Quando um valor diferente de 0 é especificado, `numeric_expression` é truncado.</span><span class="sxs-lookup"><span data-stu-id="3929b-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="3929b-238">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-238">**Return Value**</span></span> 

<span data-ttu-id="3929b-239">O valor de `numeric_expression` especificado a `power_expression`especificado.</span><span class="sxs-lookup"><span data-stu-id="3929b-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="3929b-240">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="3929b-241">ASSINAR (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-241">SIGN(expression)</span></span> 

<span data-ttu-id="3929b-242">Retorna o positivo (+1), 0 (zero), ou (- o sinal de subtração de 1) da expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="3929b-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="3929b-243">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-243">**Arguments**</span></span> 

<span data-ttu-id="3929b-244">`expression`: `Int32`, `Int64`, `Double` ou `Decimal`</span><span class="sxs-lookup"><span data-stu-id="3929b-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="3929b-245">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-245">**Return Value**</span></span> 

<span data-ttu-id="3929b-246">Um `Int32`, `Int64`, ou`Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="3929b-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="3929b-247">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="3929b-248">SIN(expression)</span><span class="sxs-lookup"><span data-stu-id="3929b-248">SIN(expression)</span></span>

<span data-ttu-id="3929b-249">Calcula o seno trigonométricas do ângulo especificado em radianos, e retorna uma expressão de `Double` .</span><span class="sxs-lookup"><span data-stu-id="3929b-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="3929b-250">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-250">**Arguments**</span></span> 

<span data-ttu-id="3929b-251">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="3929b-252">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-252">**Return Value**</span></span> 

<span data-ttu-id="3929b-253">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-253">A `Double`.</span></span> 

<span data-ttu-id="3929b-254">**Exemplo**`SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="3929b-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="3929b-255">SQRT (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-255">SQRT(expression)</span></span>

<span data-ttu-id="3929b-256">Retorna a raiz quadrada de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="3929b-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="3929b-257">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-257">**Arguments**</span></span> 

<span data-ttu-id="3929b-258">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="3929b-259">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-259">**Return Value**</span></span> 

<span data-ttu-id="3929b-260">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-260">A `Double`.</span></span> 

<span data-ttu-id="3929b-261">**Exemplo**`SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="3929b-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="3929b-262">SQUARE (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-262">SQUARE(expression)</span></span>

<span data-ttu-id="3929b-263">Retorna o quadrado de expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="3929b-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="3929b-264">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-264">**Arguments**</span></span> 

<span data-ttu-id="3929b-265">`expression`: UM `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="3929b-266">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-266">**Return Value**</span></span> 

<span data-ttu-id="3929b-267">Um `Double`.</span><span class="sxs-lookup"><span data-stu-id="3929b-267">A `Double`.</span></span> 

<span data-ttu-id="3929b-268">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="3929b-269">TAN (expressão)</span><span class="sxs-lookup"><span data-stu-id="3929b-269">TAN(expression)</span></span>

<span data-ttu-id="3929b-270">Calcula a tangente de uma expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="3929b-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="3929b-271">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="3929b-271">**Arguments**</span></span> 

<span data-ttu-id="3929b-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="3929b-272">`expression`: `Double`</span></span> 

<span data-ttu-id="3929b-273">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="3929b-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="3929b-274">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="3929b-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="3929b-275">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3929b-275">See also</span></span>

<span data-ttu-id="3929b-276">Para obter mais informações sobre as funções matemáticas que suporta SqlClient, consulte a documentação para a versão do SQL Server que você especificou no manifesto do provedor SqlClient:</span><span class="sxs-lookup"><span data-stu-id="3929b-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="3929b-277">**SQL Server 2005:** [Funções matemáticas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="3929b-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>
- <span data-ttu-id="3929b-278">**SQL Server 2008:** [Funções matemáticas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="3929b-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>
- <span data-ttu-id="3929b-279">**SQL Server 2012 e posterior:** [Funções matemáticas (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="3929b-279">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)</span></span>

- [<span data-ttu-id="3929b-280">SqlClient para funções de Entity Framework</span><span class="sxs-lookup"><span data-stu-id="3929b-280">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
