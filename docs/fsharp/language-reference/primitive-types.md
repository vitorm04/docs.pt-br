---
title: Tipos primitivos (F#)
description: "Descobre os tipos primitivos fundamentais que são usados na linguagem F #."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f23d98b-551b-4fd2-9f4f-0fd7254288ed
ms.openlocfilehash: b493cdf7116d94f66940d03b86e584bcecbbb0f1
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2017
---
# <a name="primitive-types"></a><span data-ttu-id="93c05-104">Tipos primitivos</span><span class="sxs-lookup"><span data-stu-id="93c05-104">Primitive Types</span></span>

<span data-ttu-id="93c05-105">Este tópico lista os tipos primitivos fundamentais que são usados na linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="93c05-105">This topic lists the fundamental primitive types that are used in the F# language.</span></span> <span data-ttu-id="93c05-106">Ele também fornece os tipos .NET correspondentes e os valores mínimos e máximos para cada tipo.</span><span class="sxs-lookup"><span data-stu-id="93c05-106">It also provides the corresponding .NET types and the minimum and maximum values for each type.</span></span>

## <a name="summary-of-primitive-types"></a><span data-ttu-id="93c05-107">Resumo de tipos primitivos</span><span class="sxs-lookup"><span data-stu-id="93c05-107">Summary of Primitive Types</span></span>
<span data-ttu-id="93c05-108">A tabela a seguir resume as propriedades de tipos F # primitivos.</span><span class="sxs-lookup"><span data-stu-id="93c05-108">The following table summarizes the properties of the primitive F# types.</span></span>

|<span data-ttu-id="93c05-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="93c05-109">Type</span></span>|<span data-ttu-id="93c05-110">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="93c05-110">.NET type</span></span>|<span data-ttu-id="93c05-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="93c05-111">Description</span></span>|
|----|---------|-----------|
|`bool`|`System.Boolean`|<span data-ttu-id="93c05-112">Os valores possíveis são `true` e `false`.</span><span class="sxs-lookup"><span data-stu-id="93c05-112">Possible values are `true` and `false`.</span></span>|
|`byte`|`System.Byte`|<span data-ttu-id="93c05-113">Valores de 0 a 255.</span><span class="sxs-lookup"><span data-stu-id="93c05-113">Values from 0 to 255.</span></span>|
|`sbyte`|`System.SByte`|<span data-ttu-id="93c05-114">Valores de -128 a 127.</span><span class="sxs-lookup"><span data-stu-id="93c05-114">Values from -128 to 127.</span></span>|
|`int16`|`System.Int16`|<span data-ttu-id="93c05-115">Valores de -32768 e 32767.</span><span class="sxs-lookup"><span data-stu-id="93c05-115">Values from -32768 to 32767.</span></span>|
|`uint16`|`System.UInt16`|<span data-ttu-id="93c05-116">Valores de 0 a 65535.</span><span class="sxs-lookup"><span data-stu-id="93c05-116">Values from 0 to 65535.</span></span>|
|`int`|`System.Int32`|<span data-ttu-id="93c05-117">Valores de -2.147.483.648 a 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="93c05-117">Values from -2,147,483,648 to 2,147,483,647.</span></span>|
|`uint32`|`System.UInt32`|<span data-ttu-id="93c05-118">Valores entre 0 e 4.294.967.295.</span><span class="sxs-lookup"><span data-stu-id="93c05-118">Values from 0 to 4,294,967,295.</span></span>|
|`int64`|`System.Int64`|<span data-ttu-id="93c05-119">Valores de -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807.</span><span class="sxs-lookup"><span data-stu-id="93c05-119">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|
|`uint64`|`System.UInt64`|<span data-ttu-id="93c05-120">Valores de 0 a 18.446.744.073.709.551.615.</span><span class="sxs-lookup"><span data-stu-id="93c05-120">Values from 0 to 18,446,744,073,709,551,615.</span></span>|
|`nativeint`|`System.IntPtr`|<span data-ttu-id="93c05-121">Um ponteiro nativo como um inteiro com sinal.</span><span class="sxs-lookup"><span data-stu-id="93c05-121">A native pointer as a signed integer.</span></span>|
|`unativeint`|`System.UIntPtr`|<span data-ttu-id="93c05-122">Um ponteiro nativo como um inteiro não assinado.</span><span class="sxs-lookup"><span data-stu-id="93c05-122">A native pointer as an unsigned integer.</span></span>|
|`char`|`System.Char`|<span data-ttu-id="93c05-123">Valores de caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="93c05-123">Unicode character values.</span></span>|
|`string`|`System.String`|<span data-ttu-id="93c05-124">Texto Unicode.</span><span class="sxs-lookup"><span data-stu-id="93c05-124">Unicode text.</span></span>|
|`decimal`|`System.Decimal`|<span data-ttu-id="93c05-125">Um ponto flutuante tipo de dados que tenha pelo menos 28 os dígitos significativos.</span><span class="sxs-lookup"><span data-stu-id="93c05-125">A floating point data type that has at least 28 significant digits.</span></span>|
|`unit`|<span data-ttu-id="93c05-126">não aplicável</span><span class="sxs-lookup"><span data-stu-id="93c05-126">not applicable</span></span>|<span data-ttu-id="93c05-127">Indica a ausência de um valor real.</span><span class="sxs-lookup"><span data-stu-id="93c05-127">Indicates the absence of an actual value.</span></span> <span data-ttu-id="93c05-128">O tipo tem apenas um valor formal, que é indicado `()`.</span><span class="sxs-lookup"><span data-stu-id="93c05-128">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="93c05-129">O valor unitário, `()`, geralmente é usada como um espaço reservado em que um valor é necessário, mas nenhum valor real está disponível ou faz sentido.</span><span class="sxs-lookup"><span data-stu-id="93c05-129">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|
|`void`|`System.Void`|<span data-ttu-id="93c05-130">Não indica que nenhum tipo ou valor.</span><span class="sxs-lookup"><span data-stu-id="93c05-130">Indicates no type or value.</span></span>|
|`float32, single`|`System.Single`|<span data-ttu-id="93c05-131">Um tipo de ponto flutuante de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="93c05-131">A 32-bit floating point type.</span></span>|
|`float, double`|`System.Double`|<span data-ttu-id="93c05-132">Um tipo de ponto flutuante de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="93c05-132">A 64-bit floating point type.</span></span>|

>[!NOTE]
<span data-ttu-id="93c05-133">Você pode executar cálculos com números inteiros muito grandes para o tipo de inteiro de 64 bits usando o [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) tipo.</span><span class="sxs-lookup"><span data-stu-id="93c05-133">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span></span> <span data-ttu-id="93c05-134">`bigint`não é considerado um tipo primitivo; é uma abreviação de `System.Numerics.BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="93c05-134">`bigint` is not considered a primitive type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="93c05-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93c05-135">See Also</span></span>
[<span data-ttu-id="93c05-136">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="93c05-136">F# Language Reference</span></span>](index.md)
