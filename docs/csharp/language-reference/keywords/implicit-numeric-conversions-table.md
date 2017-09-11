---
title: "Tabela de conversões numéricas implícitas (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: 12
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
ms.openlocfilehash: 4c7aa29f9bdeb5f30918e6d7b990c5197e7fe1a1
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="50dd6-102">Tabela de conversões numéricas implícitas (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="50dd6-102">Implicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="50dd6-103">A tabela a seguir mostra as conversões numéricas implícitas predefinidas.</span><span class="sxs-lookup"><span data-stu-id="50dd6-103">The following table shows the predefined implicit numeric conversions.</span></span> <span data-ttu-id="50dd6-104">As conversões implícitas podem ocorrer em diversas situações, incluindo instruções de atribuição e invocações de método.</span><span class="sxs-lookup"><span data-stu-id="50dd6-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
|<span data-ttu-id="50dd6-105">De</span><span class="sxs-lookup"><span data-stu-id="50dd6-105">From</span></span>|<span data-ttu-id="50dd6-106">Para</span><span class="sxs-lookup"><span data-stu-id="50dd6-106">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="50dd6-107">sbyte</span><span class="sxs-lookup"><span data-stu-id="50dd6-107">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="50dd6-108">`short`, `int`, `long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="50dd6-108">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="50dd6-109">byte</span><span class="sxs-lookup"><span data-stu-id="50dd6-109">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="50dd6-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="50dd6-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="50dd6-111">short</span><span class="sxs-lookup"><span data-stu-id="50dd6-111">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="50dd6-112">`int`, `long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="50dd6-112">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="50dd6-113">ushort</span><span class="sxs-lookup"><span data-stu-id="50dd6-113">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="50dd6-114">`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="50dd6-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="50dd6-115">int</span><span class="sxs-lookup"><span data-stu-id="50dd6-115">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="50dd6-116">`long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="50dd6-116">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="50dd6-117">uint</span><span class="sxs-lookup"><span data-stu-id="50dd6-117">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="50dd6-118">`long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="50dd6-118">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="50dd6-119">long</span><span class="sxs-lookup"><span data-stu-id="50dd6-119">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="50dd6-120">`float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="50dd6-120">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="50dd6-121">char</span><span class="sxs-lookup"><span data-stu-id="50dd6-121">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="50dd6-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="50dd6-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="50dd6-123">float</span><span class="sxs-lookup"><span data-stu-id="50dd6-123">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[<span data-ttu-id="50dd6-124">ulong</span><span class="sxs-lookup"><span data-stu-id="50dd6-124">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="50dd6-125">`float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="50dd6-125">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50dd6-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="50dd6-126">Remarks</span></span>  
  
-   <span data-ttu-id="50dd6-127">A precisão, mas não a magnitude, poderá ser perdida em conversões de `int`, `uint`, `long` ou `ulong` para `float` e de `long` ou `ulong` para `double`.</span><span class="sxs-lookup"><span data-stu-id="50dd6-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`,  `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
-   <span data-ttu-id="50dd6-128">Não há conversões implícitas para o tipo `char`.</span><span class="sxs-lookup"><span data-stu-id="50dd6-128">There are no implicit conversions to the `char` type.</span></span>  
  
-   <span data-ttu-id="50dd6-129">Não há conversões implícitas entre tipos de ponto flutuante e o tipo `decimal`.</span><span class="sxs-lookup"><span data-stu-id="50dd6-129">There are no implicit conversions between floating-point types and the `decimal` type.</span></span>  
  
-   <span data-ttu-id="50dd6-130">Uma expressão constante do tipo `int` pode ser convertida em `sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`, desde que o valor da expressão constante esteja dentro do intervalo do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="50dd6-130">A constant expression of type `int` can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided the value of the constant expression is within the range of the destination type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="50dd6-131">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="50dd6-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="50dd6-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50dd6-132">See Also</span></span>  
 <span data-ttu-id="50dd6-133">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="50dd6-133">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="50dd6-134">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="50dd6-134">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="50dd6-135">[Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="50dd6-135">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="50dd6-136">[Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="50dd6-136">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="50dd6-137">[Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="50dd6-137">[Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="50dd6-138">Transmissões e conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="50dd6-138">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)

