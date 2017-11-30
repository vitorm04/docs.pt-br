---
title: Operadores bit a bit (F#)
description: "Saiba mais sobre os operadores bit a bit que estão disponíveis no F # linguagem de programação."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8a2c87f5-b4c7-47fe-8580-82c956f605e5
ms.openlocfilehash: 61a8e6bafe97a229480c967a4afb5d2a256474c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="bitwise-operators"></a><span data-ttu-id="be12e-104">Operadores Bit a Bit</span><span class="sxs-lookup"><span data-stu-id="be12e-104">Bitwise Operators</span></span>

<span data-ttu-id="be12e-105">Este tópico descreve os operadores bit a bit que estão disponíveis na linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="be12e-105">This topic describes bitwise operators that are available in the F# language.</span></span>

## <a name="summary-of-bitwise-operators"></a><span data-ttu-id="be12e-106">Resumo de operadores bit a bit</span><span class="sxs-lookup"><span data-stu-id="be12e-106">Summary of Bitwise Operators</span></span>
<span data-ttu-id="be12e-107">A tabela a seguir descreve os operadores bit a bit com suporte para tipos integrais não demarcados em linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="be12e-107">The following table describes the bitwise operators that are supported for unboxed integral types in the F# language.</span></span>

|<span data-ttu-id="be12e-108">Operador</span><span class="sxs-lookup"><span data-stu-id="be12e-108">Operator</span></span>|<span data-ttu-id="be12e-109">Observações</span><span class="sxs-lookup"><span data-stu-id="be12e-109">Notes</span></span>|
|--------|-----|
|`&&&`|<span data-ttu-id="be12e-110">Operador AND bit a bit.</span><span class="sxs-lookup"><span data-stu-id="be12e-110">Bitwise AND operator.</span></span> <span data-ttu-id="be12e-111">Bits no resultado tem o valor 1 se e somente se os bits correspondentes em ambos os operandos de origem são de 1.</span><span class="sxs-lookup"><span data-stu-id="be12e-111">Bits in the result have the value 1 if and only if the corresponding bits in both source operands are 1.</span></span>|
|<code>&#124;&#124;&#124;</code>|<span data-ttu-id="be12e-112">Operador OR bit a bit.</span><span class="sxs-lookup"><span data-stu-id="be12e-112">Bitwise OR operator.</span></span> <span data-ttu-id="be12e-113">Bits no resultado tem o valor 1 se os bits correspondentes na fonte de operandos são 1.</span><span class="sxs-lookup"><span data-stu-id="be12e-113">Bits in the result have the value 1 if either of the corresponding bits in the source operands are 1.</span></span>|
|`^^^`|<span data-ttu-id="be12e-114">Bit a bit operador OR exclusivo.</span><span class="sxs-lookup"><span data-stu-id="be12e-114">Bitwise exclusive OR operator.</span></span> <span data-ttu-id="be12e-115">Bits no resultado tem o valor 1 se e somente se bits nos operandos de origem têm valores diferentes.</span><span class="sxs-lookup"><span data-stu-id="be12e-115">Bits in the result have the value 1 if and only if bits in the source operands have unequal values.</span></span>|
|`~~~`|<span data-ttu-id="be12e-116">Operador de negação bit a bit.</span><span class="sxs-lookup"><span data-stu-id="be12e-116">Bitwise negation operator.</span></span> <span data-ttu-id="be12e-117">Este é um operador unário e produz um resultado em que todos os bits 0 do operando de origem são convertidos em bits 1 e todos os bits 1 são convertidos em bits 0.</span><span class="sxs-lookup"><span data-stu-id="be12e-117">This is a unary operator and produces a result in which all 0 bits in the source operand are converted to 1 bits and all 1 bits are converted to 0 bits.</span></span>|
|`<<<`|<span data-ttu-id="be12e-118">Bit a bit operador left shift.</span><span class="sxs-lookup"><span data-stu-id="be12e-118">Bitwise left-shift operator.</span></span> <span data-ttu-id="be12e-119">O resultado é que o primeiro operando com os bits deslocados esquerda pelo número de bits no segundo operando.</span><span class="sxs-lookup"><span data-stu-id="be12e-119">The result is the first operand with bits shifted left by the number of bits in the second operand.</span></span> <span data-ttu-id="be12e-120">Bits deslocadas a posição mais significativa não são girados na posição menos significativa.</span><span class="sxs-lookup"><span data-stu-id="be12e-120">Bits shifted off the most significant position are not rotated into the least significant position.</span></span> <span data-ttu-id="be12e-121">Os bits menos significativos são preenchidos com zeros.</span><span class="sxs-lookup"><span data-stu-id="be12e-121">The least significant bits are padded with zeros.</span></span> <span data-ttu-id="be12e-122">O tipo do segundo argumento é `int32`.</span><span class="sxs-lookup"><span data-stu-id="be12e-122">The type of the second argument is `int32`.</span></span>|
|`>>>`|<span data-ttu-id="be12e-123">Bit a bit operador right shift.</span><span class="sxs-lookup"><span data-stu-id="be12e-123">Bitwise right-shift operator.</span></span> <span data-ttu-id="be12e-124">O resultado é o primeiro operando com bits deslocados direita pelo número de bits no segundo operando.</span><span class="sxs-lookup"><span data-stu-id="be12e-124">The result is the first operand with bits shifted right by the number of bits in the second operand.</span></span> <span data-ttu-id="be12e-125">Bits deslocadas a posição menos significativa não são girados para a posição mais significativa.</span><span class="sxs-lookup"><span data-stu-id="be12e-125">Bits shifted off the least significant position are not rotated into the most significant position.</span></span> <span data-ttu-id="be12e-126">Para tipos não assinados, os bits mais significativos são preenchidos com zeros.</span><span class="sxs-lookup"><span data-stu-id="be12e-126">For unsigned types, the most significant bits are padded with zeros.</span></span> <span data-ttu-id="be12e-127">Para tipos assinados, os bits mais significativos são preenchidos com aquelas.</span><span class="sxs-lookup"><span data-stu-id="be12e-127">For signed types, the most significant bits are padded with ones.</span></span> <span data-ttu-id="be12e-128">O tipo do segundo argumento é `int32`.</span><span class="sxs-lookup"><span data-stu-id="be12e-128">The type of the second argument is `int32`.</span></span>|

<span data-ttu-id="be12e-129">Os tipos a seguir podem ser usados com operadores bit a bit: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, e `unativeint`.</span><span class="sxs-lookup"><span data-stu-id="be12e-129">The following types can be used with bitwise operators: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, and `unativeint`.</span></span>

## <a name="see-also"></a><span data-ttu-id="be12e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be12e-130">See Also</span></span>
[<span data-ttu-id="be12e-131">Referência de Símbolos e Operadores</span><span class="sxs-lookup"><span data-stu-id="be12e-131">Symbol and Operator Reference</span></span>](index.md)

[<span data-ttu-id="be12e-132">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="be12e-132">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="be12e-133">Operadores Boolianos</span><span class="sxs-lookup"><span data-stu-id="be12e-133">Boolean Operators</span></span>](boolean-operators.md)

