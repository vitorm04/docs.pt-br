---
title: Tipos básicos (F#)
description: Descobrir os tipos básicos fundamentais que são usados no F# idioma.
ms.date: 07/09/2018
ms.openlocfilehash: a8a1154a211d8c87571b47cb41cb091096569472
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145118"
---
# <a name="basic-types"></a><span data-ttu-id="599da-103">Tipos básicos</span><span class="sxs-lookup"><span data-stu-id="599da-103">Basic types</span></span>

<span data-ttu-id="599da-104">Este tópico lista os tipos básicos que são definidos no F# idioma.</span><span class="sxs-lookup"><span data-stu-id="599da-104">This topic lists the basic types that are defined in the F# language.</span></span> <span data-ttu-id="599da-105">Esses tipos são mais fundamental no F#, que formam a base para quase todos F# programa.</span><span class="sxs-lookup"><span data-stu-id="599da-105">These types are the most fundamental in F#, forming the basis of nearly every F# program.</span></span> <span data-ttu-id="599da-106">Eles são um subconjunto de tipos primitivos do .NET.</span><span class="sxs-lookup"><span data-stu-id="599da-106">They are a superset of .NET primitive types.</span></span>

|<span data-ttu-id="599da-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="599da-107">Type</span></span>|<span data-ttu-id="599da-108">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="599da-108">.NET type</span></span>|<span data-ttu-id="599da-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="599da-109">Description</span></span>|
|----|---------|-----------|
|`bool`|<xref:System.Boolean>|<span data-ttu-id="599da-110">Os valores possíveis são `true` e `false`.</span><span class="sxs-lookup"><span data-stu-id="599da-110">Possible values are `true` and `false`.</span></span>|
|`byte`|<xref:System.Byte>|<span data-ttu-id="599da-111">Valores de 0 a 255.</span><span class="sxs-lookup"><span data-stu-id="599da-111">Values from 0 to 255.</span></span>|
|`sbyte`|<xref:System.SByte>|<span data-ttu-id="599da-112">Valores de -128 a 127.</span><span class="sxs-lookup"><span data-stu-id="599da-112">Values from -128 to 127.</span></span>|
|`int16`|<xref:System.Int16>|<span data-ttu-id="599da-113">Valores de -32768 a 32767.</span><span class="sxs-lookup"><span data-stu-id="599da-113">Values from -32768 to 32767.</span></span>|
|`uint16`|<xref:System.UInt16>|<span data-ttu-id="599da-114">Valores de 0 a 65535.</span><span class="sxs-lookup"><span data-stu-id="599da-114">Values from 0 to 65535.</span></span>|
|`int`|<xref:System.Int32>|<span data-ttu-id="599da-115">Valores de -2.147.483.648 a 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="599da-115">Values from -2,147,483,648 to 2,147,483,647.</span></span>|
|`uint32`|<xref:System.UInt32>|<span data-ttu-id="599da-116">Valores de 0 a 4.294.967.295.</span><span class="sxs-lookup"><span data-stu-id="599da-116">Values from 0 to 4,294,967,295.</span></span>|
|`int64`|<xref:System.Int64>|<span data-ttu-id="599da-117">Valores de -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807.</span><span class="sxs-lookup"><span data-stu-id="599da-117">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|
|`uint64`|<xref:System.UInt64>|<span data-ttu-id="599da-118">Valores de 0 a 18.446.744.073.709.551.615.</span><span class="sxs-lookup"><span data-stu-id="599da-118">Values from 0 to 18,446,744,073,709,551,615.</span></span>|
|`nativeint`|<xref:System.IntPtr>|<span data-ttu-id="599da-119">Um ponteiro nativo como um inteiro com sinal.</span><span class="sxs-lookup"><span data-stu-id="599da-119">A native pointer as a signed integer.</span></span>|
|`unativeint`|<xref:System.UIntPtr>|<span data-ttu-id="599da-120">Um ponteiro nativo como um inteiro sem sinal.</span><span class="sxs-lookup"><span data-stu-id="599da-120">A native pointer as an unsigned integer.</span></span>|
|`char`|<xref:System.Char>|<span data-ttu-id="599da-121">Valores de caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="599da-121">Unicode character values.</span></span>|
|`string`|<xref:System.String>|<span data-ttu-id="599da-122">Texto Unicode.</span><span class="sxs-lookup"><span data-stu-id="599da-122">Unicode text.</span></span>|
|`decimal`|<xref:System.Decimal>|<span data-ttu-id="599da-123">Tipo de dados que tem pelo menos 28 dígitos significativos de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="599da-123">A floating point data type that has at least 28 significant digits.</span></span>|
|`unit`|<span data-ttu-id="599da-124">não aplicável</span><span class="sxs-lookup"><span data-stu-id="599da-124">not applicable</span></span>|<span data-ttu-id="599da-125">Indica a ausência de um valor real.</span><span class="sxs-lookup"><span data-stu-id="599da-125">Indicates the absence of an actual value.</span></span> <span data-ttu-id="599da-126">O tipo tem apenas um valor formal, que é denotado `()`.</span><span class="sxs-lookup"><span data-stu-id="599da-126">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="599da-127">O valor de unidade, `()`, geralmente é usado como um espaço reservado em que um valor é necessário, mas nenhum valor real está disponível ou faz sentido.</span><span class="sxs-lookup"><span data-stu-id="599da-127">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|
|`void`|<xref:System.Void>|<span data-ttu-id="599da-128">Não indica que nenhum tipo ou valor.</span><span class="sxs-lookup"><span data-stu-id="599da-128">Indicates no type or value.</span></span>|
|<span data-ttu-id="599da-129">`float32`, `single`</span><span class="sxs-lookup"><span data-stu-id="599da-129">`float32`, `single`</span></span>|<xref:System.Single>|<span data-ttu-id="599da-130">Um tipo de ponto flutuante de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="599da-130">A 32-bit floating point type.</span></span>|
|<span data-ttu-id="599da-131">`float`, `double`</span><span class="sxs-lookup"><span data-stu-id="599da-131">`float`, `double`</span></span>|<xref:System.Double>|<span data-ttu-id="599da-132">Um tipo de ponto flutuante de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="599da-132">A 64-bit floating point type.</span></span>|

> [!NOTE]
> <span data-ttu-id="599da-133">Você pode executar cálculos com números inteiros grandes demais para o tipo de inteiro de 64 bits usando o [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) tipo.</span><span class="sxs-lookup"><span data-stu-id="599da-133">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span></span> <span data-ttu-id="599da-134">`bigint` não é considerado um tipo básico; ele é uma abreviação de `System.Numerics.BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="599da-134">`bigint` is not considered a basic type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="599da-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="599da-135">See also</span></span>

- [<span data-ttu-id="599da-136">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="599da-136">F# Language Reference</span></span>](index.md)
