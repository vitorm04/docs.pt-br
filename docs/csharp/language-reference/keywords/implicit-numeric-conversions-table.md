---
title: "Tabela de conversões numéricas implícitas (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6b1705dca357fd2a155fc1ea9c7fe0f65bad8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="6e4de-102">Tabela de conversões numéricas implícitas (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="6e4de-102">Implicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="6e4de-103">A tabela a seguir mostra as conversões numéricas implícitas predefinidas.</span><span class="sxs-lookup"><span data-stu-id="6e4de-103">The following table shows the predefined implicit numeric conversions.</span></span> <span data-ttu-id="6e4de-104">As conversões implícitas podem ocorrer em diversas situações, incluindo instruções de atribuição e invocações de método.</span><span class="sxs-lookup"><span data-stu-id="6e4de-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
|<span data-ttu-id="6e4de-105">De</span><span class="sxs-lookup"><span data-stu-id="6e4de-105">From</span></span>|<span data-ttu-id="6e4de-106">Para</span><span class="sxs-lookup"><span data-stu-id="6e4de-106">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="6e4de-107">sbyte</span><span class="sxs-lookup"><span data-stu-id="6e4de-107">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="6e4de-108">`short`, `int`, `long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="6e4de-108">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6e4de-109">byte</span><span class="sxs-lookup"><span data-stu-id="6e4de-109">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="6e4de-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="6e4de-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6e4de-111">short</span><span class="sxs-lookup"><span data-stu-id="6e4de-111">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="6e4de-112">`int`, `long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="6e4de-112">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6e4de-113">ushort</span><span class="sxs-lookup"><span data-stu-id="6e4de-113">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="6e4de-114">`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="6e4de-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6e4de-115">int</span><span class="sxs-lookup"><span data-stu-id="6e4de-115">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="6e4de-116">`long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="6e4de-116">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6e4de-117">uint</span><span class="sxs-lookup"><span data-stu-id="6e4de-117">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="6e4de-118">`long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="6e4de-118">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6e4de-119">long</span><span class="sxs-lookup"><span data-stu-id="6e4de-119">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="6e4de-120">`float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="6e4de-120">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6e4de-121">char</span><span class="sxs-lookup"><span data-stu-id="6e4de-121">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="6e4de-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="6e4de-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6e4de-123">float</span><span class="sxs-lookup"><span data-stu-id="6e4de-123">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[<span data-ttu-id="6e4de-124">ulong</span><span class="sxs-lookup"><span data-stu-id="6e4de-124">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="6e4de-125">`float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="6e4de-125">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e4de-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e4de-126">Remarks</span></span>  
  
-   <span data-ttu-id="6e4de-127">A precisão, mas não a magnitude, poderá ser perdida em conversões de `int`, `uint`, `long` ou `ulong` para `float` e de `long` ou `ulong` para `double`.</span><span class="sxs-lookup"><span data-stu-id="6e4de-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`,  `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
-   <span data-ttu-id="6e4de-128">Não há conversões implícitas para o tipo `char`.</span><span class="sxs-lookup"><span data-stu-id="6e4de-128">There are no implicit conversions to the `char` type.</span></span>  
  
-   <span data-ttu-id="6e4de-129">Não há conversões implícitas entre tipos de ponto flutuante e o tipo `decimal`.</span><span class="sxs-lookup"><span data-stu-id="6e4de-129">There are no implicit conversions between floating-point types and the `decimal` type.</span></span>  
  
-   <span data-ttu-id="6e4de-130">Uma expressão constante do tipo `int` pode ser convertida em `sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`, desde que o valor da expressão constante esteja dentro do intervalo do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="6e4de-130">A constant expression of type `int` can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided the value of the constant expression is within the range of the destination type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6e4de-131">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="6e4de-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6e4de-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e4de-132">See Also</span></span>  
 [<span data-ttu-id="6e4de-133">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="6e4de-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6e4de-134">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6e4de-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6e4de-135">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="6e4de-135">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="6e4de-136">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="6e4de-136">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="6e4de-137">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="6e4de-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="6e4de-138">Transmissões e conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="6e4de-138">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
