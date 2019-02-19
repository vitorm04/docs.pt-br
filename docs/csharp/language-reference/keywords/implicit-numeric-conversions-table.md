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
ms.openlocfilehash: 703f60f48e1e569e0ffcab66ff7ccc91d4a49514
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093548"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="1ca53-102">Tabela de conversões numéricas implícitas (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1ca53-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="1ca53-103">A tabela a seguir mostra as conversões implícitas predefinidas entre tipos numéricos do .NET.</span><span class="sxs-lookup"><span data-stu-id="1ca53-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="1ca53-104">De</span><span class="sxs-lookup"><span data-stu-id="1ca53-104">From</span></span>|<span data-ttu-id="1ca53-105">Para</span><span class="sxs-lookup"><span data-stu-id="1ca53-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="1ca53-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="1ca53-106">sbyte</span></span>](sbyte.md)|<span data-ttu-id="1ca53-107">`short`, `int`, `long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="1ca53-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1ca53-108">byte</span><span class="sxs-lookup"><span data-stu-id="1ca53-108">byte</span></span>](byte.md)|<span data-ttu-id="1ca53-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="1ca53-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1ca53-110">char</span><span class="sxs-lookup"><span data-stu-id="1ca53-110">char</span></span>](char.md)|<span data-ttu-id="1ca53-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="1ca53-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1ca53-112">short</span><span class="sxs-lookup"><span data-stu-id="1ca53-112">short</span></span>](short.md)|<span data-ttu-id="1ca53-113">`int`, `long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="1ca53-113">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1ca53-114">ushort</span><span class="sxs-lookup"><span data-stu-id="1ca53-114">ushort</span></span>](ushort.md)|<span data-ttu-id="1ca53-115">`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="1ca53-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1ca53-116">int</span><span class="sxs-lookup"><span data-stu-id="1ca53-116">int</span></span>](int.md)|<span data-ttu-id="1ca53-117">`long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="1ca53-117">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1ca53-118">uint</span><span class="sxs-lookup"><span data-stu-id="1ca53-118">uint</span></span>](uint.md)|<span data-ttu-id="1ca53-119">`long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="1ca53-119">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1ca53-120">long</span><span class="sxs-lookup"><span data-stu-id="1ca53-120">long</span></span>](long.md)|<span data-ttu-id="1ca53-121">`float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="1ca53-121">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1ca53-122">ulong</span><span class="sxs-lookup"><span data-stu-id="1ca53-122">ulong</span></span>](ulong.md)|<span data-ttu-id="1ca53-123">`float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="1ca53-123">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1ca53-124">float</span><span class="sxs-lookup"><span data-stu-id="1ca53-124">float</span></span>](float.md)|`double`|  
  
## <a name="remarks"></a><span data-ttu-id="1ca53-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ca53-125">Remarks</span></span>  

- <span data-ttu-id="1ca53-126">Qualquer [tipo integral](integral-types-table.md) pode ser implicitamente convertido em qualquer [tipo de ponto flutuante](floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="1ca53-126">Any [integral type](integral-types-table.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="1ca53-127">A precisão, mas não a magnitude, poderá ser perdida nas conversões de `int`, `uint`, `long` ou `ulong` em `float` e de `long` ou `ulong` em `double`.</span><span class="sxs-lookup"><span data-stu-id="1ca53-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="1ca53-128">Não há nenhuma conversão implícita para os tipos `char`, `byte` e `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="1ca53-128">There are no implicit conversions to the `char`, `byte`, and `sbyte` types.</span></span>  

- <span data-ttu-id="1ca53-129">Não há nenhuma conversão implícita dos tipos `double` e `decimal`.</span><span class="sxs-lookup"><span data-stu-id="1ca53-129">There are no implicit conversions from the `double` and `decimal` types.</span></span>
  
- <span data-ttu-id="1ca53-130">Não há nenhuma conversão implícita entre os tipos `decimal` e `float` ou os tipos `double`.</span><span class="sxs-lookup"><span data-stu-id="1ca53-130">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>  
  
- <span data-ttu-id="1ca53-131">Um valor de uma expressão de constante de tipo `int` (por exemplo, um valor representado por um literal integral) pode ser convertido em `sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`, contanto que esteja dentro do intervalo do tipo de destino:</span><span class="sxs-lookup"><span data-stu-id="1ca53-131">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="1ca53-132">Para obter mais informações sobre conversões implícitas, consulte a seção [Conversões implícitas](~/_csharplang/spec/conversions.md#implicit-conversions) da [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="1ca53-132">For more information about implicit conversions, see the [Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1ca53-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ca53-133">See also</span></span>

- [<span data-ttu-id="1ca53-134">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1ca53-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1ca53-135">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1ca53-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1ca53-136">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="1ca53-136">Integral types table</span></span>](integral-types-table.md)
- [<span data-ttu-id="1ca53-137">Tabela de tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="1ca53-137">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="1ca53-138">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="1ca53-138">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="1ca53-139">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="1ca53-139">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="1ca53-140">Conversão e conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="1ca53-140">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
