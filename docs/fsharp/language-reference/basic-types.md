---
title: Tipos Básicos
description: 'Descubra os tipos básicos fundamentais que são usados na linguagem F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 659ac8424c62985affcca1741e1b2a74c9c3ee8d
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557692"
---
# <a name="basic-types"></a><span data-ttu-id="879a9-103">Tipos básicos</span><span class="sxs-lookup"><span data-stu-id="879a9-103">Basic types</span></span>

<span data-ttu-id="879a9-104">Este tópico lista os tipos básicos que são definidos na linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="879a9-104">This topic lists the basic types that are defined in the F# language.</span></span> <span data-ttu-id="879a9-105">Esses tipos são os mais fundamentais em F #, que formam a base de quase todos os programas em F #.</span><span class="sxs-lookup"><span data-stu-id="879a9-105">These types are the most fundamental in F#, forming the basis of nearly every F# program.</span></span> <span data-ttu-id="879a9-106">Eles são um superconjunto de tipos primitivos .NET.</span><span class="sxs-lookup"><span data-stu-id="879a9-106">They are a superset of .NET primitive types.</span></span>

|<span data-ttu-id="879a9-107">Type</span><span class="sxs-lookup"><span data-stu-id="879a9-107">Type</span></span>|<span data-ttu-id="879a9-108">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="879a9-108">.NET type</span></span>|<span data-ttu-id="879a9-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="879a9-109">Description</span></span>|<span data-ttu-id="879a9-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="879a9-110">Example</span></span>|
|----|---------|-----------|-------|
|`bool`|<xref:System.Boolean>|<span data-ttu-id="879a9-111">Os valores possíveis são `true` e `false`.</span><span class="sxs-lookup"><span data-stu-id="879a9-111">Possible values are `true` and `false`.</span></span>|`true`/`false`|
|`byte`|<xref:System.Byte>|<span data-ttu-id="879a9-112">Valores de 0 a 255.</span><span class="sxs-lookup"><span data-stu-id="879a9-112">Values from 0 to 255.</span></span>|`1uy`|
|`sbyte`|<xref:System.SByte>|<span data-ttu-id="879a9-113">Valores de-128 a 127.</span><span class="sxs-lookup"><span data-stu-id="879a9-113">Values from -128 to 127.</span></span>|`1y`|
|`int16`|<xref:System.Int16>|<span data-ttu-id="879a9-114">Valores de-32768 a 32767.</span><span class="sxs-lookup"><span data-stu-id="879a9-114">Values from -32768 to 32767.</span></span>|`1s`|
|`uint16`|<xref:System.UInt16>|<span data-ttu-id="879a9-115">Valores de 0 a 65535.</span><span class="sxs-lookup"><span data-stu-id="879a9-115">Values from 0 to 65535.</span></span>|`1us`|
|`int`|<xref:System.Int32>|<span data-ttu-id="879a9-116">Valores de-2.147.483.648 a 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="879a9-116">Values from -2,147,483,648 to 2,147,483,647.</span></span>|`1`|
|`uint`|<xref:System.UInt32>|<span data-ttu-id="879a9-117">Valores de 0 a 4.294.967.295.</span><span class="sxs-lookup"><span data-stu-id="879a9-117">Values from 0 to 4,294,967,295.</span></span>|`1u`|
|`int64`|<xref:System.Int64>|<span data-ttu-id="879a9-118">Valores de-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807.</span><span class="sxs-lookup"><span data-stu-id="879a9-118">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|`1L`|
|`uint64`|<xref:System.UInt64>|<span data-ttu-id="879a9-119">Valores de 0 a 18446744073709551615.</span><span class="sxs-lookup"><span data-stu-id="879a9-119">Values from 0 to 18,446,744,073,709,551,615.</span></span>|`1UL`|
|`nativeint`|<xref:System.IntPtr>|<span data-ttu-id="879a9-120">Um ponteiro nativo como um inteiro assinado.</span><span class="sxs-lookup"><span data-stu-id="879a9-120">A native pointer as a signed integer.</span></span>|`nativeint 1`|
|`unativeint`|<xref:System.UIntPtr>|<span data-ttu-id="879a9-121">Um ponteiro nativo como um inteiro não assinado.</span><span class="sxs-lookup"><span data-stu-id="879a9-121">A native pointer as an unsigned integer.</span></span>|`unativeint 1`|
|`decimal`|<xref:System.Decimal>|<span data-ttu-id="879a9-122">Um tipo de dados de ponto flutuante que tem pelo menos 28 dígitos significativos.</span><span class="sxs-lookup"><span data-stu-id="879a9-122">A floating point data type that has at least 28 significant digits.</span></span>|`1.0`|
|<span data-ttu-id="879a9-123">`float`, `double`</span><span class="sxs-lookup"><span data-stu-id="879a9-123">`float`, `double`</span></span>|<xref:System.Double>|<span data-ttu-id="879a9-124">Um tipo de ponto flutuante de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="879a9-124">A 64-bit floating point type.</span></span>|`1.0`|
|<span data-ttu-id="879a9-125">`float32`, `single`</span><span class="sxs-lookup"><span data-stu-id="879a9-125">`float32`, `single`</span></span>|<xref:System.Single>|<span data-ttu-id="879a9-126">Um tipo de ponto flutuante de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="879a9-126">A 32-bit floating point type.</span></span>|`1.0f`|
|`char`|<xref:System.Char>|<span data-ttu-id="879a9-127">Valores de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="879a9-127">Unicode character values.</span></span>|`'c'`|
|`string`|<xref:System.String>|<span data-ttu-id="879a9-128">Texto Unicode.</span><span class="sxs-lookup"><span data-stu-id="879a9-128">Unicode text.</span></span>|`"str"`|
|`unit`|<span data-ttu-id="879a9-129">não aplicável</span><span class="sxs-lookup"><span data-stu-id="879a9-129">not applicable</span></span>|<span data-ttu-id="879a9-130">Indica a ausência de um valor real.</span><span class="sxs-lookup"><span data-stu-id="879a9-130">Indicates the absence of an actual value.</span></span> <span data-ttu-id="879a9-131">O tipo tem apenas um valor formal, que é indicado `()` .</span><span class="sxs-lookup"><span data-stu-id="879a9-131">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="879a9-132">O valor de unidade, `()` , geralmente é usado como um espaço reservado onde um valor é necessário, mas nenhum valor real está disponível ou faz sentido.</span><span class="sxs-lookup"><span data-stu-id="879a9-132">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|`()`|

> [!NOTE]
> <span data-ttu-id="879a9-133">Você pode executar cálculos com números inteiros muito grandes para o tipo inteiro de 64 bits usando o tipo [bigint](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-bigint.html) .</span><span class="sxs-lookup"><span data-stu-id="879a9-133">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-bigint.html) type.</span></span> <span data-ttu-id="879a9-134">`bigint` Não é considerado um tipo básico; é uma abreviação do `System.Numerics.BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="879a9-134">`bigint` is not considered a basic type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="879a9-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="879a9-135">See also</span></span>

- [<span data-ttu-id="879a9-136">Referência de linguagem F #</span><span class="sxs-lookup"><span data-stu-id="879a9-136">F# Language Reference</span></span>](index.md)
