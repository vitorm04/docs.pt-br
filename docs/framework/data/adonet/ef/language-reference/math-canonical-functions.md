---
title: Funções canônicas matemáticas
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 0fc9f4942c3f76f139ab7e4400005f0bfe80204e
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087603"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="6c2d8-102">Funções canônicas matemáticas</span><span class="sxs-lookup"><span data-stu-id="6c2d8-102">Math Canonical Functions</span></span>

<span data-ttu-id="6c2d8-103">Entity SQL inclui as seguintes funções canônicas de matemáticas:</span><span class="sxs-lookup"><span data-stu-id="6c2d8-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="6c2d8-104">Abs (valor)</span><span class="sxs-lookup"><span data-stu-id="6c2d8-104">Abs(value)</span></span>

<span data-ttu-id="6c2d8-105">Retorna o valor absoluto de `value`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="6c2d8-106">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-106">**Arguments**</span></span>

<span data-ttu-id="6c2d8-107">Uma `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="6c2d8-108">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-108">**Return Value**</span></span>

<span data-ttu-id="6c2d8-109">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-109">The type of `value`.</span></span>

<span data-ttu-id="6c2d8-110">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="6c2d8-111">Teto (valor)</span><span class="sxs-lookup"><span data-stu-id="6c2d8-111">Ceiling(value)</span></span>

<span data-ttu-id="6c2d8-112">Retorna o número inteiro o menor que não é menor que `value`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="6c2d8-113">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-113">**Arguments**</span></span>

<span data-ttu-id="6c2d8-114">Um `Single`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="6c2d8-115">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-115">**Return Value**</span></span>

<span data-ttu-id="6c2d8-116">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-116">The type of `value`.</span></span>

<span data-ttu-id="6c2d8-117">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="6c2d8-118">Andar (valor)</span><span class="sxs-lookup"><span data-stu-id="6c2d8-118">Floor(value)</span></span>

<span data-ttu-id="6c2d8-119">Retorna o número inteiro maior que não é maior do que `value`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="6c2d8-120">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-120">**Arguments**</span></span>

<span data-ttu-id="6c2d8-121">Um `Single`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="6c2d8-122">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-122">**Return Value**</span></span>

<span data-ttu-id="6c2d8-123">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-123">The type of `value`.</span></span>

<span data-ttu-id="6c2d8-124">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="6c2d8-125">Põe (valor, expoente)</span><span class="sxs-lookup"><span data-stu-id="6c2d8-125">Power(value, exponent)</span></span>

<span data-ttu-id="6c2d8-126">Retorna o resultado de `value` especificado a `exponent`especificado.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="6c2d8-127">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="6c2d8-128">Um `Int32, Int64, Double` ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="6c2d8-129">Uma `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="6c2d8-130">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-130">**Return Value**</span></span>

<span data-ttu-id="6c2d8-131">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-131">The type of `value`.</span></span>

<span data-ttu-id="6c2d8-132">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="6c2d8-133">Redondo (valor)</span><span class="sxs-lookup"><span data-stu-id="6c2d8-133">Round(value)</span></span>

<span data-ttu-id="6c2d8-134">Retorna a parte inteira de `value`, arredondada para o inteiro mais próximo.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="6c2d8-135">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-135">**Arguments**</span></span>

<span data-ttu-id="6c2d8-136">Um `Single`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="6c2d8-137">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-137">**Return Value**</span></span>

<span data-ttu-id="6c2d8-138">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-138">The type of `value`.</span></span>

<span data-ttu-id="6c2d8-139">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="6c2d8-140">Redondo (valor, dígitos)</span><span class="sxs-lookup"><span data-stu-id="6c2d8-140">Round(value, digits)</span></span>

<span data-ttu-id="6c2d8-141">Retorna `value`, arredondado a `digits`especificado o mais próximo.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="6c2d8-142">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="6c2d8-143">`Double` ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="6c2d8-144">`Int16` ou `Int32`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="6c2d8-145">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-145">**Return Value**</span></span>

<span data-ttu-id="6c2d8-146">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-146">The type of `value`.</span></span>

<span data-ttu-id="6c2d8-147">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="6c2d8-148">Truncar (valor, dígitos)</span><span class="sxs-lookup"><span data-stu-id="6c2d8-148">Truncate(value, digits)</span></span>

<span data-ttu-id="6c2d8-149">Retorna `value`, truncado a `digits`especificado o mais próximo.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="6c2d8-150">**Argumentos**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="6c2d8-151">`Double` ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="6c2d8-152">`Int16` ou `Int32`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="6c2d8-153">**Valor retornado**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-153">**Return Value**</span></span>

<span data-ttu-id="6c2d8-154">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-154">The type of `value`.</span></span>

<span data-ttu-id="6c2d8-155">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="6c2d8-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="6c2d8-156">Essas funções retornará `null` se entrada dada de `null` .</span><span class="sxs-lookup"><span data-stu-id="6c2d8-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="6c2d8-157">Funcionalidade equivalente está disponível no provedor gerenciado cliente do Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="6c2d8-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="6c2d8-158">Para obter mais informações, consulte [SqlClient para funções de Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="6c2d8-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c2d8-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c2d8-159">See Also</span></span>  
 <span data-ttu-id="6c2d8-160">[Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) (Funções canônicas)</span><span class="sxs-lookup"><span data-stu-id="6c2d8-160">[Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)</span></span>
