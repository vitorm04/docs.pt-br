---
title: Funções canônicas matemáticas
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 0fc9f4942c3f76f139ab7e4400005f0bfe80204e
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708082"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="4573e-102">Funções canônicas matemáticas</span><span class="sxs-lookup"><span data-stu-id="4573e-102">Math Canonical Functions</span></span>

<span data-ttu-id="4573e-103">Entity SQL inclui as seguintes funções canônicas de matemáticas:</span><span class="sxs-lookup"><span data-stu-id="4573e-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="4573e-104">Abs (valor)</span><span class="sxs-lookup"><span data-stu-id="4573e-104">Abs(value)</span></span>

<span data-ttu-id="4573e-105">Retorna o valor absoluto de `value`.</span><span class="sxs-lookup"><span data-stu-id="4573e-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="4573e-106">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="4573e-106">**Arguments**</span></span>

<span data-ttu-id="4573e-107">Uma `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4573e-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="4573e-108">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="4573e-108">**Return Value**</span></span>

<span data-ttu-id="4573e-109">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="4573e-109">The type of `value`.</span></span>

<span data-ttu-id="4573e-110">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="4573e-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="4573e-111">Teto (valor)</span><span class="sxs-lookup"><span data-stu-id="4573e-111">Ceiling(value)</span></span>

<span data-ttu-id="4573e-112">Retorna o número inteiro o menor que não é menor que `value`.</span><span class="sxs-lookup"><span data-stu-id="4573e-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="4573e-113">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="4573e-113">**Arguments**</span></span>

<span data-ttu-id="4573e-114">Um `Single`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4573e-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="4573e-115">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="4573e-115">**Return Value**</span></span>

<span data-ttu-id="4573e-116">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="4573e-116">The type of `value`.</span></span>

<span data-ttu-id="4573e-117">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="4573e-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="4573e-118">Andar (valor)</span><span class="sxs-lookup"><span data-stu-id="4573e-118">Floor(value)</span></span>

<span data-ttu-id="4573e-119">Retorna o número inteiro maior que não é maior do que `value`.</span><span class="sxs-lookup"><span data-stu-id="4573e-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="4573e-120">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="4573e-120">**Arguments**</span></span>

<span data-ttu-id="4573e-121">Um `Single`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4573e-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="4573e-122">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="4573e-122">**Return Value**</span></span>

<span data-ttu-id="4573e-123">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="4573e-123">The type of `value`.</span></span>

<span data-ttu-id="4573e-124">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="4573e-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="4573e-125">Põe (valor, expoente)</span><span class="sxs-lookup"><span data-stu-id="4573e-125">Power(value, exponent)</span></span>

<span data-ttu-id="4573e-126">Retorna o resultado de `value` especificado a `exponent`especificado.</span><span class="sxs-lookup"><span data-stu-id="4573e-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="4573e-127">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="4573e-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="4573e-128">Um `Int32, Int64, Double` ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4573e-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="4573e-129">Uma `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4573e-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="4573e-130">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="4573e-130">**Return Value**</span></span>

<span data-ttu-id="4573e-131">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="4573e-131">The type of `value`.</span></span>

<span data-ttu-id="4573e-132">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="4573e-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="4573e-133">Redondo (valor)</span><span class="sxs-lookup"><span data-stu-id="4573e-133">Round(value)</span></span>

<span data-ttu-id="4573e-134">Retorna a parte inteira de `value`, arredondada para o inteiro mais próximo.</span><span class="sxs-lookup"><span data-stu-id="4573e-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="4573e-135">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="4573e-135">**Arguments**</span></span>

<span data-ttu-id="4573e-136">Um `Single`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4573e-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="4573e-137">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="4573e-137">**Return Value**</span></span>

<span data-ttu-id="4573e-138">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="4573e-138">The type of `value`.</span></span>

<span data-ttu-id="4573e-139">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="4573e-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="4573e-140">Redondo (valor, dígitos)</span><span class="sxs-lookup"><span data-stu-id="4573e-140">Round(value, digits)</span></span>

<span data-ttu-id="4573e-141">Retorna `value`, arredondado a `digits`especificado o mais próximo.</span><span class="sxs-lookup"><span data-stu-id="4573e-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="4573e-142">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="4573e-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="4573e-143">`Double` ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4573e-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="4573e-144">`Int16` ou `Int32`.</span><span class="sxs-lookup"><span data-stu-id="4573e-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="4573e-145">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="4573e-145">**Return Value**</span></span>

<span data-ttu-id="4573e-146">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="4573e-146">The type of `value`.</span></span>

<span data-ttu-id="4573e-147">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="4573e-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="4573e-148">Truncar (valor, dígitos)</span><span class="sxs-lookup"><span data-stu-id="4573e-148">Truncate(value, digits)</span></span>

<span data-ttu-id="4573e-149">Retorna `value`, truncado a `digits`especificado o mais próximo.</span><span class="sxs-lookup"><span data-stu-id="4573e-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="4573e-150">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="4573e-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="4573e-151">`Double` ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4573e-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="4573e-152">`Int16` ou `Int32`.</span><span class="sxs-lookup"><span data-stu-id="4573e-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="4573e-153">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="4573e-153">**Return Value**</span></span>

<span data-ttu-id="4573e-154">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="4573e-154">The type of `value`.</span></span>

<span data-ttu-id="4573e-155">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="4573e-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="4573e-156">Essas funções retornará `null` se entrada dada de `null` .</span><span class="sxs-lookup"><span data-stu-id="4573e-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="4573e-157">Funcionalidade equivalente está disponível no provedor gerenciado cliente do Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="4573e-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="4573e-158">Para obter mais informações, consulte [SqlClient para funções de Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4573e-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4573e-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4573e-159">See Also</span></span>  
 <span data-ttu-id="4573e-160">[Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) (Funções canônicas)</span><span class="sxs-lookup"><span data-stu-id="4573e-160">[Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)</span></span>
