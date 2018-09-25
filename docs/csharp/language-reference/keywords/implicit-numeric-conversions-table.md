---
title: Tabela de conversões numéricas implícitas (Referência de C#)
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: e46816fc8f3a6ff71dcba3561098d3cfce1e1054
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44213258"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="a1414-102">Tabela de conversões numéricas implícitas (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a1414-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="a1414-103">A tabela a seguir mostra as conversões implícitas predefinidas entre tipos numéricos do .NET.</span><span class="sxs-lookup"><span data-stu-id="a1414-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="a1414-104">De</span><span class="sxs-lookup"><span data-stu-id="a1414-104">From</span></span>|<span data-ttu-id="a1414-105">Para</span><span class="sxs-lookup"><span data-stu-id="a1414-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="a1414-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="a1414-106">sbyte</span></span>](sbyte.md)|<span data-ttu-id="a1414-107">`short`, `int`, `long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="a1414-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="a1414-108">byte</span><span class="sxs-lookup"><span data-stu-id="a1414-108">byte</span></span>](byte.md)|<span data-ttu-id="a1414-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="a1414-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="a1414-110">short</span><span class="sxs-lookup"><span data-stu-id="a1414-110">short</span></span>](short.md)|<span data-ttu-id="a1414-111">`int`, `long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="a1414-111">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="a1414-112">ushort</span><span class="sxs-lookup"><span data-stu-id="a1414-112">ushort</span></span>](ushort.md)|<span data-ttu-id="a1414-113">`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="a1414-113">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="a1414-114">int</span><span class="sxs-lookup"><span data-stu-id="a1414-114">int</span></span>](int.md)|<span data-ttu-id="a1414-115">`long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="a1414-115">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="a1414-116">uint</span><span class="sxs-lookup"><span data-stu-id="a1414-116">uint</span></span>](uint.md)|<span data-ttu-id="a1414-117">`long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="a1414-117">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="a1414-118">long</span><span class="sxs-lookup"><span data-stu-id="a1414-118">long</span></span>](long.md)|<span data-ttu-id="a1414-119">`float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="a1414-119">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="a1414-120">char</span><span class="sxs-lookup"><span data-stu-id="a1414-120">char</span></span>](char.md)|<span data-ttu-id="a1414-121">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="a1414-121">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="a1414-122">float</span><span class="sxs-lookup"><span data-stu-id="a1414-122">float</span></span>](float.md)|`double`|  
|[<span data-ttu-id="a1414-123">ulong</span><span class="sxs-lookup"><span data-stu-id="a1414-123">ulong</span></span>](ulong.md)|<span data-ttu-id="a1414-124">`float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="a1414-124">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1414-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1414-125">Remarks</span></span>  

- <span data-ttu-id="a1414-126">Qualquer [tipo integral](integral-types-table.md) pode ser implicitamente convertido em qualquer [tipo de ponto flutuante](floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="a1414-126">Any [integral type](integral-types-table.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="a1414-127">A precisão, mas não a magnitude, poderá ser perdida nas conversões de `int`, `uint`, `long` ou `ulong` em `float` e de `long` ou `ulong` em `double`.</span><span class="sxs-lookup"><span data-stu-id="a1414-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="a1414-128">Não há conversões implícitas para o tipo `char`.</span><span class="sxs-lookup"><span data-stu-id="a1414-128">There are no implicit conversions to the `char` type.</span></span>  
  
- <span data-ttu-id="a1414-129">Não há conversões implícitas entre os tipos `float` e `double` e o tipo `decimal`.</span><span class="sxs-lookup"><span data-stu-id="a1414-129">There are no implicit conversions between the `float` and `double` types and the `decimal` type.</span></span>  
  
- <span data-ttu-id="a1414-130">Um valor de uma expressão de constante de tipo `int` (por exemplo, um valor representado por um literal integral) pode ser convertido em `sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`, contanto que esteja dentro do intervalo do tipo de destino:</span><span class="sxs-lookup"><span data-stu-id="a1414-130">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="a1414-131">Para obter mais informações sobre conversões implícitas, consulte a seção [Conversões implícitas](/dotnet/csharp/language-reference/language-specification/conversions#implicit-conversions) da [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1414-131">For more information about implicit conversions, see the [Implicit conversions](/dotnet/csharp/language-reference/language-specification/conversions#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a1414-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1414-132">See also</span></span>

- [<span data-ttu-id="a1414-133">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a1414-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a1414-134">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a1414-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a1414-135">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="a1414-135">Integral types table</span></span>](integral-types-table.md)
- [<span data-ttu-id="a1414-136">Tabela de tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="a1414-136">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="a1414-137">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="a1414-137">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="a1414-138">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="a1414-138">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="a1414-139">Conversão e conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="a1414-139">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
