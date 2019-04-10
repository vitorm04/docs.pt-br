---
title: Funções canônicas matemáticas
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: f575785bb198251ef50ba3563e736946253c9526
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228764"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="d8405-102">Funções canônicas matemáticas</span><span class="sxs-lookup"><span data-stu-id="d8405-102">Math Canonical Functions</span></span>

<span data-ttu-id="d8405-103">Entity SQL inclui as seguintes funções canônicas de matemáticas:</span><span class="sxs-lookup"><span data-stu-id="d8405-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="d8405-104">Abs (valor)</span><span class="sxs-lookup"><span data-stu-id="d8405-104">Abs(value)</span></span>

<span data-ttu-id="d8405-105">Retorna o valor absoluto de `value`.</span><span class="sxs-lookup"><span data-stu-id="d8405-105">Returns the absolute value of `value`.</span></span>

**<span data-ttu-id="d8405-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="d8405-106">Arguments</span></span>**

<span data-ttu-id="d8405-107">Uma `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d8405-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="d8405-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d8405-108">Return Value</span></span>**

<span data-ttu-id="d8405-109">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="d8405-109">The type of `value`.</span></span>

**<span data-ttu-id="d8405-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8405-110">Example</span></span>**

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="d8405-111">Teto (valor)</span><span class="sxs-lookup"><span data-stu-id="d8405-111">Ceiling(value)</span></span>

<span data-ttu-id="d8405-112">Retorna o número inteiro o menor que não é menor que `value`.</span><span class="sxs-lookup"><span data-stu-id="d8405-112">Returns the smallest integer that is not less than `value`.</span></span>

**<span data-ttu-id="d8405-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="d8405-113">Arguments</span></span>**

<span data-ttu-id="d8405-114">Um `Single`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d8405-114">A `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="d8405-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d8405-115">Return Value</span></span>**

<span data-ttu-id="d8405-116">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="d8405-116">The type of `value`.</span></span>

**<span data-ttu-id="d8405-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8405-117">Example</span></span>**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="d8405-118">Andar (valor)</span><span class="sxs-lookup"><span data-stu-id="d8405-118">Floor(value)</span></span>

<span data-ttu-id="d8405-119">Retorna o número inteiro maior que não é maior do que `value`.</span><span class="sxs-lookup"><span data-stu-id="d8405-119">Returns the largest integer that is not greater than `value`.</span></span>

**<span data-ttu-id="d8405-120">Arguments</span><span class="sxs-lookup"><span data-stu-id="d8405-120">Arguments</span></span>**

<span data-ttu-id="d8405-121">Um `Single`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d8405-121">A `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="d8405-122">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d8405-122">Return Value</span></span>**

<span data-ttu-id="d8405-123">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="d8405-123">The type of `value`.</span></span>

**<span data-ttu-id="d8405-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8405-124">Example</span></span>**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="d8405-125">Põe (valor, expoente)</span><span class="sxs-lookup"><span data-stu-id="d8405-125">Power(value, exponent)</span></span>

<span data-ttu-id="d8405-126">Retorna o resultado de `value` especificado a `exponent`especificado.</span><span class="sxs-lookup"><span data-stu-id="d8405-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

**<span data-ttu-id="d8405-127">Arguments</span><span class="sxs-lookup"><span data-stu-id="d8405-127">Arguments</span></span>**

|  |  |
|--|--|
|`value` | <span data-ttu-id="d8405-128">Um `Int32, Int64, Double` ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d8405-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="d8405-129">Uma `Int64`, `Double`, ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d8405-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

**<span data-ttu-id="d8405-130">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d8405-130">Return Value</span></span>**

<span data-ttu-id="d8405-131">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="d8405-131">The type of `value`.</span></span>

**<span data-ttu-id="d8405-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8405-132">Example</span></span>**

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="d8405-133">Redondo (valor)</span><span class="sxs-lookup"><span data-stu-id="d8405-133">Round(value)</span></span>

<span data-ttu-id="d8405-134">Retorna a parte inteira de `value`, arredondada para o inteiro mais próximo.</span><span class="sxs-lookup"><span data-stu-id="d8405-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

**<span data-ttu-id="d8405-135">Arguments</span><span class="sxs-lookup"><span data-stu-id="d8405-135">Arguments</span></span>**

<span data-ttu-id="d8405-136">Um `Single`, `Double`, e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d8405-136">A `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="d8405-137">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d8405-137">Return Value</span></span>**

<span data-ttu-id="d8405-138">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="d8405-138">The type of `value`.</span></span>

**<span data-ttu-id="d8405-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8405-139">Example</span></span>**

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="d8405-140">Redondo (valor, dígitos)</span><span class="sxs-lookup"><span data-stu-id="d8405-140">Round(value, digits)</span></span>

<span data-ttu-id="d8405-141">Retorna `value`, arredondado a `digits`especificado o mais próximo.</span><span class="sxs-lookup"><span data-stu-id="d8405-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

**<span data-ttu-id="d8405-142">Arguments</span><span class="sxs-lookup"><span data-stu-id="d8405-142">Arguments</span></span>**

|  |  |
|--|--|
|`value`|`Double` <span data-ttu-id="d8405-143">ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d8405-143">or `Decimal`.</span></span>|
|`digits`|`Int16` <span data-ttu-id="d8405-144">ou `Int32`.</span><span class="sxs-lookup"><span data-stu-id="d8405-144">or `Int32`.</span></span>|

**<span data-ttu-id="d8405-145">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d8405-145">Return Value</span></span>**

<span data-ttu-id="d8405-146">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="d8405-146">The type of `value`.</span></span>

**<span data-ttu-id="d8405-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8405-147">Example</span></span>**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="d8405-148">Truncar (valor, dígitos)</span><span class="sxs-lookup"><span data-stu-id="d8405-148">Truncate(value, digits)</span></span>

<span data-ttu-id="d8405-149">Retorna `value`, truncado a `digits`especificado o mais próximo.</span><span class="sxs-lookup"><span data-stu-id="d8405-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

**<span data-ttu-id="d8405-150">Arguments</span><span class="sxs-lookup"><span data-stu-id="d8405-150">Arguments</span></span>**

|  |  |
|--|--|
|`value`|`Double` <span data-ttu-id="d8405-151">ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d8405-151">or `Decimal`.</span></span>|
|`digits`|`Int16` <span data-ttu-id="d8405-152">ou `Int32`.</span><span class="sxs-lookup"><span data-stu-id="d8405-152">or `Int32`.</span></span>|

**<span data-ttu-id="d8405-153">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d8405-153">Return Value</span></span>**

<span data-ttu-id="d8405-154">O tipo de `value`.</span><span class="sxs-lookup"><span data-stu-id="d8405-154">The type of `value`.</span></span>

**<span data-ttu-id="d8405-155">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8405-155">Example</span></span>**

`Truncate(748.58,1)`  
  
 <span data-ttu-id="d8405-156">Essas funções retornará `null` se entrada dada de `null` .</span><span class="sxs-lookup"><span data-stu-id="d8405-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="d8405-157">Funcionalidade equivalente está disponível no provedor gerenciado cliente do Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="d8405-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="d8405-158">Para obter mais informações, consulte [SqlClient para funções de Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d8405-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8405-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8405-159">See also</span></span>

- [<span data-ttu-id="d8405-160">Funções canônicas</span><span class="sxs-lookup"><span data-stu-id="d8405-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
