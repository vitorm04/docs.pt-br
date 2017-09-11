---
title: "Tabela de conversões numéricas explícitas (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0315810522be319a6bb565c99e1c8f7d1ba4701b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="explicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="bbafa-102">Tabela de conversões numéricas explícitas (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="bbafa-102">Explicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="bbafa-103">A conversão numérica explícita é usada para converter qualquer tipo numérico para outro tipo numérico para o qual não há conversão implícita, por meio de uma expressão de conversão.</span><span class="sxs-lookup"><span data-stu-id="bbafa-103">Explicit numeric conversion is used to convert any numeric type to any other numeric type, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="bbafa-104">A tabela a seguir mostra essas conversões.</span><span class="sxs-lookup"><span data-stu-id="bbafa-104">The following table shows these conversions.</span></span>  
  
 <span data-ttu-id="bbafa-105">Para obter mais informações sobre conversões, consulte [Conversões e Conversões de Tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="bbafa-105">For more information about conversions, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
|<span data-ttu-id="bbafa-106">De</span><span class="sxs-lookup"><span data-stu-id="bbafa-106">From</span></span>|<span data-ttu-id="bbafa-107">Para</span><span class="sxs-lookup"><span data-stu-id="bbafa-107">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="bbafa-108">sbyte</span><span class="sxs-lookup"><span data-stu-id="bbafa-108">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="bbafa-109">`byte`, `ushort`, `uint`, `ulong` ou `char`</span><span class="sxs-lookup"><span data-stu-id="bbafa-109">`byte`, `ushort`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="bbafa-110">byte</span><span class="sxs-lookup"><span data-stu-id="bbafa-110">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="bbafa-111">`Sbyte` ou `char`</span><span class="sxs-lookup"><span data-stu-id="bbafa-111">`Sbyte` or `char`</span></span>|  
|[<span data-ttu-id="bbafa-112">short</span><span class="sxs-lookup"><span data-stu-id="bbafa-112">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="bbafa-113">`sbyte`, `byte`, `ushort`, `uint`, `ulong` ou `char`</span><span class="sxs-lookup"><span data-stu-id="bbafa-113">`sbyte`, `byte`, `ushort`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="bbafa-114">ushort</span><span class="sxs-lookup"><span data-stu-id="bbafa-114">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="bbafa-115">`sbyte`, `byte`, `short` ou `char`</span><span class="sxs-lookup"><span data-stu-id="bbafa-115">`sbyte`, `byte`, `short`, or `char`</span></span>|  
|[<span data-ttu-id="bbafa-116">int</span><span class="sxs-lookup"><span data-stu-id="bbafa-116">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="bbafa-117">`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong` ou `char`</span><span class="sxs-lookup"><span data-stu-id="bbafa-117">`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`,or `char`</span></span>|  
|[<span data-ttu-id="bbafa-118">uint</span><span class="sxs-lookup"><span data-stu-id="bbafa-118">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="bbafa-119">`sbyte`, `byte`, `short`, `ushort`, `int` ou `char`</span><span class="sxs-lookup"><span data-stu-id="bbafa-119">`sbyte`, `byte`, `short`, `ushort`, `int`, or `char`</span></span>|  
|[<span data-ttu-id="bbafa-120">long</span><span class="sxs-lookup"><span data-stu-id="bbafa-120">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="bbafa-121">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong` ou `char`</span><span class="sxs-lookup"><span data-stu-id="bbafa-121">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="bbafa-122">ulong</span><span class="sxs-lookup"><span data-stu-id="bbafa-122">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="bbafa-123">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long` ou `char`</span><span class="sxs-lookup"><span data-stu-id="bbafa-123">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, or `char`</span></span>|  
|[<span data-ttu-id="bbafa-124">char</span><span class="sxs-lookup"><span data-stu-id="bbafa-124">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="bbafa-125">`sbyte`, `byte` ou `short`</span><span class="sxs-lookup"><span data-stu-id="bbafa-125">`sbyte`, `byte`, or `short`</span></span>|  
|[<span data-ttu-id="bbafa-126">float</span><span class="sxs-lookup"><span data-stu-id="bbafa-126">float</span></span>](../../../csharp/language-reference/keywords/float.md)|<span data-ttu-id="bbafa-127">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="bbafa-127">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`,or `decimal`</span></span>|  
|[<span data-ttu-id="bbafa-128">double</span><span class="sxs-lookup"><span data-stu-id="bbafa-128">double</span></span>](../../../csharp/language-reference/keywords/double.md)|<span data-ttu-id="bbafa-129">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="bbafa-129">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`,or `decimal`</span></span>|  
|[<span data-ttu-id="bbafa-130">decimal</span><span class="sxs-lookup"><span data-stu-id="bbafa-130">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|<span data-ttu-id="bbafa-131">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float` ou `double`</span><span class="sxs-lookup"><span data-stu-id="bbafa-131">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, or `double`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbafa-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="bbafa-132">Remarks</span></span>  
  
-   <span data-ttu-id="bbafa-133">A conversão numérica explícita pode causar perda de precisão ou resultados ao lançar exceções.</span><span class="sxs-lookup"><span data-stu-id="bbafa-133">The explicit numeric conversion may cause loss of precision or result in throwing exceptions.</span></span>  
  
-   <span data-ttu-id="bbafa-134">Ao converter um valor `decimal` para um tipo integral, esse valor será arredondado para zero, para o valor integral mais próximo.</span><span class="sxs-lookup"><span data-stu-id="bbafa-134">When you convert a `decimal` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="bbafa-135">Se o valor integral resultante estiver fora do intervalo do tipo de destino, uma <xref:System.OverflowException> será lançada.</span><span class="sxs-lookup"><span data-stu-id="bbafa-135">If the resulting integral value is outside the range of the destination type, an <xref:System.OverflowException> is thrown.</span></span>  
  
-   <span data-ttu-id="bbafa-136">Ao converter de um valor `double` ou `float` para um tipo integral, o valore será truncado.</span><span class="sxs-lookup"><span data-stu-id="bbafa-136">When you convert from a `double` or `float` value to an integral type, the value is truncated.</span></span> <span data-ttu-id="bbafa-137">Se o valor integral resultante estiver fora do intervalo do valor de destino, o resultado dependerá do contexto de verificação de estouro.</span><span class="sxs-lookup"><span data-stu-id="bbafa-137">If the resulting integral value is outside the range of the destination value, the result depends on the overflow checking context.</span></span> <span data-ttu-id="bbafa-138">Em um contexto verificado, uma `OverflowException` será lançada, ao passo que em um contexto não verificado, o resultado será um valor não especificado do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="bbafa-138">In a checked context, an `OverflowException` is thrown, while in an unchecked context, the result is an unspecified value of the destination type.</span></span>  
  
-   <span data-ttu-id="bbafa-139">Ao converter `double` para `float`, o valor `double` será arredondado para o valor `float` mais próximo.</span><span class="sxs-lookup"><span data-stu-id="bbafa-139">When you convert `double` to `float`, the `double` value is rounded to the nearest `float` value.</span></span> <span data-ttu-id="bbafa-140">Se o valor `double` for muito pequeno ou muito grande para caber no tipo de destino, o resultado será zero ou infinito.</span><span class="sxs-lookup"><span data-stu-id="bbafa-140">If the `double` value is too small or too large to fit into the destination type, the result will be zero or infinity.</span></span>  
  
-   <span data-ttu-id="bbafa-141">Ao converter `float` ou `double` para `decimal`, o valor de origem será convertido para uma representação `decimal` e arredondado para o número mais próximo após a 28ª casa decimal, se necessário.</span><span class="sxs-lookup"><span data-stu-id="bbafa-141">When you convert `float` or `double` to `decimal`, the source value is converted to `decimal` representation and rounded to the nearest number after the 28th decimal place if required.</span></span> <span data-ttu-id="bbafa-142">De acordo com o valor do valor de origem, um dos resultados a seguir podem ocorrer:</span><span class="sxs-lookup"><span data-stu-id="bbafa-142">Depending on the value of the source value, one of the following results may occur:</span></span>  
  
    -   <span data-ttu-id="bbafa-143">Se o valor de origem for muito pequeno para ser representado como um `decimal`, o resultado será zero.</span><span class="sxs-lookup"><span data-stu-id="bbafa-143">If the source value is too small to be represented as a `decimal`, the result becomes zero.</span></span>  
  
    -   <span data-ttu-id="bbafa-144">Se o valor de origem for um NaN (não for um número), infinito ou muito grande para ser representado como um `decimal`, uma `OverflowException` será lançada.</span><span class="sxs-lookup"><span data-stu-id="bbafa-144">If the source value is NaN (not a number), infinity, or too large to be represented as a `decimal`, an `OverflowException` is thrown.</span></span>  
  
-   <span data-ttu-id="bbafa-145">Ao converter `decimal` para `float` ou `double`, o valor `decimal` será arredondado para o valor `double` ou `float` mais próximo.</span><span class="sxs-lookup"><span data-stu-id="bbafa-145">When you convert `decimal` to `float` or `double`, the `decimal` value is rounded to the nearest `double` or `float` value.</span></span>  
  
 <span data-ttu-id="bbafa-146">Para obter mais informações sobre conversões explícitas, consulte Explícito na Especificação da Linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="bbafa-146">For more information on explicit conversion, see Explicit in the C# Language Specification.</span></span> <span data-ttu-id="bbafa-147">Para obter mais informações sobre como acessar a especificação, consulte [Especificação da Linguagem C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="bbafa-147">For more information on how to access the spec, see [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbafa-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbafa-148">See Also</span></span>  
 <span data-ttu-id="bbafa-149">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="bbafa-149">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="bbafa-150">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="bbafa-150">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="bbafa-151">[Conversões cast e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="bbafa-151">[Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span></span>  
 <span data-ttu-id="bbafa-152">[Operador ()](../../../csharp/language-reference/operators/invocation-operator.md) </span><span class="sxs-lookup"><span data-stu-id="bbafa-152">[() Operator](../../../csharp/language-reference/operators/invocation-operator.md) </span></span>  
 <span data-ttu-id="bbafa-153">[Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="bbafa-153">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="bbafa-154">[Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="bbafa-154">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 [<span data-ttu-id="bbafa-155">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="bbafa-155">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)

