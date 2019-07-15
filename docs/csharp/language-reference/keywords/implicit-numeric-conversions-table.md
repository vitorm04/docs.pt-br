---
title: Tabela de conversões numéricas implícitas – Referência de C#
ms.custom: seodec18
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 516505ccacfd2a8a5c275b0de033e1316fa06d3a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661328"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="4f5b6-102">Tabela de conversões numéricas implícitas (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4f5b6-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="4f5b6-103">A tabela a seguir mostra as conversões implícitas predefinidas entre tipos numéricos do .NET.</span><span class="sxs-lookup"><span data-stu-id="4f5b6-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="4f5b6-104">De</span><span class="sxs-lookup"><span data-stu-id="4f5b6-104">From</span></span>|<span data-ttu-id="4f5b6-105">Para</span><span class="sxs-lookup"><span data-stu-id="4f5b6-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="4f5b6-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="4f5b6-106">sbyte</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="4f5b6-107">`short`, `int`, `long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="4f5b6-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4f5b6-108">byte</span><span class="sxs-lookup"><span data-stu-id="4f5b6-108">byte</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="4f5b6-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="4f5b6-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4f5b6-110">char</span><span class="sxs-lookup"><span data-stu-id="4f5b6-110">char</span></span>](char.md)|<span data-ttu-id="4f5b6-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="4f5b6-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4f5b6-112">short</span><span class="sxs-lookup"><span data-stu-id="4f5b6-112">short</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="4f5b6-113">`int`, `long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="4f5b6-113">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4f5b6-114">ushort</span><span class="sxs-lookup"><span data-stu-id="4f5b6-114">ushort</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="4f5b6-115">`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="4f5b6-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4f5b6-116">int</span><span class="sxs-lookup"><span data-stu-id="4f5b6-116">int</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="4f5b6-117">`long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="4f5b6-117">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4f5b6-118">uint</span><span class="sxs-lookup"><span data-stu-id="4f5b6-118">uint</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="4f5b6-119">`long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="4f5b6-119">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4f5b6-120">long</span><span class="sxs-lookup"><span data-stu-id="4f5b6-120">long</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="4f5b6-121">`float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="4f5b6-121">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4f5b6-122">ulong</span><span class="sxs-lookup"><span data-stu-id="4f5b6-122">ulong</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="4f5b6-123">`float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="4f5b6-123">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4f5b6-124">float</span><span class="sxs-lookup"><span data-stu-id="4f5b6-124">float</span></span>](../builtin-types/floating-point-numeric-types.md)|`double`|  
  
## <a name="remarks"></a><span data-ttu-id="4f5b6-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f5b6-125">Remarks</span></span>  

- <span data-ttu-id="4f5b6-126">Qualquer [tipo integral](../builtin-types/integral-numeric-types.md) pode ser implicitamente convertido em qualquer [tipo de ponto flutuante](../builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="4f5b6-126">Any [integral type](../builtin-types/integral-numeric-types.md) is implicitly convertible to any [floating-point type](../builtin-types/floating-point-numeric-types.md).</span></span>

- <span data-ttu-id="4f5b6-127">A precisão, mas não a magnitude, poderá ser perdida nas conversões de `int`, `uint`, `long` ou `ulong` em `float` e de `long` ou `ulong` em `double`.</span><span class="sxs-lookup"><span data-stu-id="4f5b6-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="4f5b6-128">Não há nenhuma conversão implícita para os tipos `char`, `byte` e `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="4f5b6-128">There are no implicit conversions to the `char`, `byte`, and `sbyte` types.</span></span>  

- <span data-ttu-id="4f5b6-129">Não há nenhuma conversão implícita dos tipos `double` e `decimal`.</span><span class="sxs-lookup"><span data-stu-id="4f5b6-129">There are no implicit conversions from the `double` and `decimal` types.</span></span>
  
- <span data-ttu-id="4f5b6-130">Não há nenhuma conversão implícita entre os tipos `decimal` e `float` ou os tipos `double`.</span><span class="sxs-lookup"><span data-stu-id="4f5b6-130">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>  
  
- <span data-ttu-id="4f5b6-131">Um valor de uma expressão de constante de tipo `int` (por exemplo, um valor representado por um literal integral) pode ser convertido em `sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`, contanto que esteja dentro do intervalo do tipo de destino:</span><span class="sxs-lookup"><span data-stu-id="4f5b6-131">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="4f5b6-132">Para obter mais informações sobre conversões implícitas, consulte a seção [Conversões implícitas](~/_csharplang/spec/conversions.md#implicit-conversions) da [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4f5b6-132">For more information about implicit conversions, see the [Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4f5b6-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f5b6-133">See also</span></span>

- [<span data-ttu-id="4f5b6-134">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="4f5b6-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4f5b6-135">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="4f5b6-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4f5b6-136">Tipos integrais</span><span class="sxs-lookup"><span data-stu-id="4f5b6-136">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="4f5b6-137">Tabela de tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="4f5b6-137">Floating-point types table</span></span>](../builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="4f5b6-138">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="4f5b6-138">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="4f5b6-139">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="4f5b6-139">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="4f5b6-140">Conversão e conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="4f5b6-140">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
