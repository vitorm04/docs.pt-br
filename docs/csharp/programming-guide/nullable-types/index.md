---
title: Tipos anuláveis (Guia de Programação em C#)
ms.date: 05/15/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
caps.latest.revision: 44
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9b874b265f4adb131a056ea1ef6fb5ffc820343f
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="nullable-types-c-programming-guide"></a><span data-ttu-id="46da2-102">Tipos anuláveis (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="46da2-102">Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="46da2-103">Os tipos que permitem valor nulo são instâncias do struct <xref:System.Nullable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="46da2-103">Nullable types are instances of the <xref:System.Nullable%601?displayProperty=nameWithType> struct.</span></span> <span data-ttu-id="46da2-104">Um tipo que permite valor nulo pode representar o intervalo de valores para seu tipo de valor subjacente, além de um valor `null` adicional.</span><span class="sxs-lookup"><span data-stu-id="46da2-104">A nullable type can represent the correct range of values for its underlying value type, plus an additional `null` value.</span></span> <span data-ttu-id="46da2-105">Por exemplo, `Nullable<Int32>`, também indicado como “Nullable de Int32”, pode receber qualquer valor de –2147483648 a 2147483647 ou receber um valor `null`.</span><span class="sxs-lookup"><span data-stu-id="46da2-105">For example, a `Nullable<Int32>`, pronounced "Nullable of Int32," can be assigned any value from -2147483648 to 2147483647, or it can be assigned the `null` value.</span></span> <span data-ttu-id="46da2-106">Um `Nullable<bool>` pode ser atribuído aos valores [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) ou [nulo](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="46da2-106">A `Nullable<bool>` can be assigned the values [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), or [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="46da2-107">A capacidade de atribuir `null` para tipos numéricos e boolianos é especialmente útil quando você está lidando com bancos de dados e outros tipos de dados que contêm elementos que não podem ser atribuídos a um valor.</span><span class="sxs-lookup"><span data-stu-id="46da2-107">The ability to assign `null` to numeric and Boolean types is especially useful when you are dealing with databases and other data types that contain elements that may not be assigned a value.</span></span> <span data-ttu-id="46da2-108">Por exemplo, um campo booliano em um banco de dados pode armazenar os valores `true` ou `false` ou pode ser indefinido.</span><span class="sxs-lookup"><span data-stu-id="46da2-108">For example, a Boolean field in a database can store the values `true` or `false`, or it may be undefined.</span></span> 
  
[!code-csharp[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]  
  
<span data-ttu-id="46da2-109">Para obter mais informações, consulte [Usando tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)</span><span class="sxs-lookup"><span data-stu-id="46da2-109">For more examples, see [Using Nullable Types](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)</span></span>  
  
## <a name="nullable-types-overview"></a><span data-ttu-id="46da2-110">Visão geral dos tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="46da2-110">Nullable Types Overview</span></span>  
 <span data-ttu-id="46da2-111">Os tipos que permitem valor nulo têm as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="46da2-111">Nullable types have the following characteristics:</span></span>  
  
-   <span data-ttu-id="46da2-112">Os tipos que permitem valor nulo representam variáveis de tipo de valor que podem ser atribuídas ao valor de `null`.</span><span class="sxs-lookup"><span data-stu-id="46da2-112">Nullable types represent value-type variables that can be assigned the value of `null`.</span></span> <span data-ttu-id="46da2-113">Você não pode criar um tipo que permite valor nulo com base em um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="46da2-113">You cannot create a nullable type based on a reference type.</span></span> <span data-ttu-id="46da2-114">(Os tipos de referência já dão suporte ao valor `null`.)</span><span class="sxs-lookup"><span data-stu-id="46da2-114">(Reference types already support the `null` value.)</span></span>  
  
-   <span data-ttu-id="46da2-115">A sintaxe `T?` é a abreviação de <xref:System.Nullable%601>, em que `T` é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="46da2-115">The syntax `T?` is shorthand for <xref:System.Nullable%601>, where `T` is a value type.</span></span> <span data-ttu-id="46da2-116">As duas formas são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="46da2-116">The two forms are interchangeable.</span></span>  
  
-   <span data-ttu-id="46da2-117">Atribuir um valor a um tipo que permite valor nulo exatamente como faria para um tipo de valor comum, por exemplo `int? x = 10;` ou `double? d = 4.108`.</span><span class="sxs-lookup"><span data-stu-id="46da2-117">Assign a value to a nullable type just as you would for an ordinary value type, for example `int? x = 10;` or `double? d = 4.108`.</span></span> <span data-ttu-id="46da2-118">Um tipo que permite valor nulo também pode ser atribuído ao valor `null`:`int? x = null.`</span><span class="sxs-lookup"><span data-stu-id="46da2-118">A nullable type can also be assigned the value `null`: `int? x = null.`</span></span>  
  
-   <span data-ttu-id="46da2-119">Use o método <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> para retornar o valor atribuído ou o valor padrão do tipo subjacente se o valor for `null`, por exemplo `int j = x.GetValueOrDefault();`</span><span class="sxs-lookup"><span data-stu-id="46da2-119">Use the <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> method to return either the assigned value, or the default value for the underlying type if the value is `null`, for example `int j = x.GetValueOrDefault();`</span></span>  
  
-   <span data-ttu-id="46da2-120">Use as propriedades somente leitura <xref:System.Nullable%601.HasValue%2A> e <xref:System.Nullable%601.Value%2A> para testar em relação ao valor nulo e recupere o valor, conforme mostrado no exemplo a seguir: `if(x.HasValue) j = x.Value;`</span><span class="sxs-lookup"><span data-stu-id="46da2-120">Use the <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> read-only properties to test for null and retrieve the value, as shown in the following example: `if(x.HasValue) j = x.Value;`</span></span>  
  
    -   <span data-ttu-id="46da2-121">A propriedade `HasValue` retornará `true` se a variável contiver um valor ou `false` se for `null`.</span><span class="sxs-lookup"><span data-stu-id="46da2-121">The `HasValue` property returns `true` if the variable contains a value, or `false` if it is `null`.</span></span>  
  
    -   <span data-ttu-id="46da2-122">A propriedade `Value` retorna um valor se atribuído.</span><span class="sxs-lookup"><span data-stu-id="46da2-122">The `Value` property returns a value if one is assigned.</span></span> <span data-ttu-id="46da2-123">Caso contrário, uma <xref:System.InvalidOperationException?displayProperty=nameWithType> será gerada.</span><span class="sxs-lookup"><span data-stu-id="46da2-123">Otherwise, a <xref:System.InvalidOperationException?displayProperty=nameWithType> is thrown.</span></span>  
  
    -   <span data-ttu-id="46da2-124">O valor padrão para `HasValue` é `false`.</span><span class="sxs-lookup"><span data-stu-id="46da2-124">The default value for `HasValue` is `false`.</span></span> <span data-ttu-id="46da2-125">A propriedade `Value` não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="46da2-125">The `Value` property has no default value.</span></span>  
  
    -   <span data-ttu-id="46da2-126">Você também pode usar os operadores `==` e `!=` com um tipo que permite valor nulo, conforme mostrado no exemplo a seguir: `if (x != null) y = x;`</span><span class="sxs-lookup"><span data-stu-id="46da2-126">You can also use the `==` and `!=` operators with a nullable type, as shown in the following example: `if (x != null) y = x;`</span></span>  
  
-   <span data-ttu-id="46da2-127">Use o operador `??` para atribuir um valor padrão que será aplicado quando um tipo que permite valor nulo cujo valor atual é `null` for atribuído a um tipo não anulável, por exemplo, `int? x = null; int y = x ?? -1;`</span><span class="sxs-lookup"><span data-stu-id="46da2-127">Use the `??` operator to assign a default value that will be applied when a nullable type whose current value is `null` is assigned to a non-nullable type, for example `int? x = null; int y = x ?? -1;`</span></span>  
  
-   <span data-ttu-id="46da2-128">Os tipos que permitem valor nulo aninhados não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="46da2-128">Nested nullable types are not allowed.</span></span> <span data-ttu-id="46da2-129">A linha a seguir não será compilada: `Nullable<Nullable<int>> n;`</span><span class="sxs-lookup"><span data-stu-id="46da2-129">The following line will not compile: `Nullable<Nullable<int>> n;`</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="46da2-130">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="46da2-130">Related Sections</span></span>  
 <span data-ttu-id="46da2-131">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="46da2-131">For more information:</span></span>  
  
-   [<span data-ttu-id="46da2-132">Usando tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="46da2-132">Using Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [<span data-ttu-id="46da2-133">Conversão boxing de tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="46da2-133">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [<span data-ttu-id="46da2-134">Operador ??</span><span class="sxs-lookup"><span data-stu-id="46da2-134">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="46da2-135">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="46da2-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="46da2-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46da2-136">See Also</span></span>  
 <xref:System.Nullable>  
 [<span data-ttu-id="46da2-137">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="46da2-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="46da2-138">C#</span><span class="sxs-lookup"><span data-stu-id="46da2-138">C#</span></span>](../../../csharp/index.md)  
 [<span data-ttu-id="46da2-139">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="46da2-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="46da2-140">O que exatamente "levantado" significa?</span><span class="sxs-lookup"><span data-stu-id="46da2-140">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
