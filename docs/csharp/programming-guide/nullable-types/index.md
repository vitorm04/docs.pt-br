---
title: "Tipos anuláveis (Guia de Programação em C#)"
ms.date: 2017-05-15
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
caps.latest.revision: 44
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
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: 56e22638457017688ff380f6683b463b47c53a17
ms.contentlocale: pt-br
ms.lasthandoff: 09/02/2017

---
# <a name="nullable-types-c-programming-guide"></a><span data-ttu-id="27f90-102">Tipos anuláveis (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="27f90-102">Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="27f90-103">Os tipos que permitem valor nulo são instâncias do struct <xref:System.Nullable%601?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="27f90-103">Nullable types are instances of the <xref:System.Nullable%601?displayProperty=fullName> struct.</span></span> <span data-ttu-id="27f90-104">Um tipo que permite valor nulo pode representar o intervalo de valores para seu tipo de valor subjacente, além de um valor `null` adicional.</span><span class="sxs-lookup"><span data-stu-id="27f90-104">A nullable type can represent the correct range of values for its underlying value type, plus an additional `null` value.</span></span> <span data-ttu-id="27f90-105">Por exemplo, `Nullable<Int32>`, também indicado como “Nullable de Int32”, pode receber qualquer valor de –2147483648 a 2147483647 ou receber um valor `null`.</span><span class="sxs-lookup"><span data-stu-id="27f90-105">For example, a `Nullable<Int32>`, pronounced "Nullable of Int32," can be assigned any value from -2147483648 to 2147483647, or it can be assigned the `null` value.</span></span> <span data-ttu-id="27f90-106">Um `Nullable<bool>` pode ser atribuído aos valores [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) ou [nulo](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="27f90-106">A `Nullable<bool>` can be assigned the values [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), or [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="27f90-107">A capacidade de atribuir `null` para tipos numéricos e boolianos é especialmente útil quando você está lidando com bancos de dados e outros tipos de dados que contêm elementos que não podem ser atribuídos a um valor.</span><span class="sxs-lookup"><span data-stu-id="27f90-107">The ability to assign `null` to numeric and Boolean types is especially useful when you are dealing with databases and other data types that contain elements that may not be assigned a value.</span></span> <span data-ttu-id="27f90-108">Por exemplo, um campo booliano em um banco de dados pode armazenar os valores `true` ou `false` ou pode ser indefinido.</span><span class="sxs-lookup"><span data-stu-id="27f90-108">For example, a Boolean field in a database can store the values `true` or `false`, or it may be undefined.</span></span> 
  
<span data-ttu-id="27f90-109">[!code-cs[tipos que permitem valor nulo](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]</span><span class="sxs-lookup"><span data-stu-id="27f90-109">[!code-cs[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]</span></span>  
  
<span data-ttu-id="27f90-110">Para obter mais informações, consulte [Usando tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)</span><span class="sxs-lookup"><span data-stu-id="27f90-110">For more examples, see [Using Nullable Types](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)</span></span>  
  
## <a name="nullable-types-overview"></a><span data-ttu-id="27f90-111">Visão geral dos tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="27f90-111">Nullable Types Overview</span></span>  
 <span data-ttu-id="27f90-112">Os tipos que permitem valor nulo têm as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="27f90-112">Nullable types have the following characteristics:</span></span>  
  
-   <span data-ttu-id="27f90-113">Os tipos que permitem valor nulo representam variáveis de tipo de valor que podem ser atribuídas ao valor de `null`.</span><span class="sxs-lookup"><span data-stu-id="27f90-113">Nullable types represent value-type variables that can be assigned the value of `null`.</span></span> <span data-ttu-id="27f90-114">Você não pode criar um tipo que permite valor nulo com base em um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="27f90-114">You cannot create a nullable type based on a reference type.</span></span> <span data-ttu-id="27f90-115">(Os tipos de referência já dão suporte ao valor `null`.)</span><span class="sxs-lookup"><span data-stu-id="27f90-115">(Reference types already support the `null` value.)</span></span>  
  
-   <span data-ttu-id="27f90-116">A sintaxe `T?` é a abreviação de <xref:System.Nullable%601>, em que `T` é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="27f90-116">The syntax `T?` is shorthand for <xref:System.Nullable%601>, where `T` is a value type.</span></span> <span data-ttu-id="27f90-117">As duas formas são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="27f90-117">The two forms are interchangeable.</span></span>  
  
-   <span data-ttu-id="27f90-118">Atribuir um valor a um tipo que permite valor nulo exatamente como faria para um tipo de valor comum, por exemplo `int? x = 10;` ou `double? d = 4.108`.</span><span class="sxs-lookup"><span data-stu-id="27f90-118">Assign a value to a nullable type just as you would for an ordinary value type, for example `int? x = 10;` or `double? d = 4.108`.</span></span> <span data-ttu-id="27f90-119">Um tipo que permite valor nulo também pode ser atribuído ao valor `null`:`int? x = null.`</span><span class="sxs-lookup"><span data-stu-id="27f90-119">A nullable type can also be assigned the value `null`: `int? x = null.`</span></span>  
  
-   <span data-ttu-id="27f90-120">Use o método <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> para retornar o valor atribuído ou o valor padrão do tipo subjacente se o valor for `null`, por exemplo `int j = x.GetValueOrDefault();`</span><span class="sxs-lookup"><span data-stu-id="27f90-120">Use the <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> method to return either the assigned value, or the default value for the underlying type if the value is `null`, for example `int j = x.GetValueOrDefault();`</span></span>  
  
-   <span data-ttu-id="27f90-121">Use as propriedades somente leitura <xref:System.Nullable%601.HasValue%2A> e <xref:System.Nullable%601.Value%2A> para testar em relação ao valor nulo e recupere o valor, conforme mostrado no exemplo a seguir: `if(x.HasValue) j = x.Value;`</span><span class="sxs-lookup"><span data-stu-id="27f90-121">Use the <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> read-only properties to test for null and retrieve the value, as shown in the following example: `if(x.HasValue) j = x.Value;`</span></span>  
  
    -   <span data-ttu-id="27f90-122">A propriedade `HasValue` retornará `true` se a variável contiver um valor ou `false` se for `null`.</span><span class="sxs-lookup"><span data-stu-id="27f90-122">The `HasValue` property returns `true` if the variable contains a value, or `false` if it is `null`.</span></span>  
  
    -   <span data-ttu-id="27f90-123">A propriedade `Value` retorna um valor se atribuído.</span><span class="sxs-lookup"><span data-stu-id="27f90-123">The `Value` property returns a value if one is assigned.</span></span> <span data-ttu-id="27f90-124">Caso contrário, uma <xref:System.InvalidOperationException?displayProperty=fullName> será gerada.</span><span class="sxs-lookup"><span data-stu-id="27f90-124">Otherwise, a <xref:System.InvalidOperationException?displayProperty=fullName> is thrown.</span></span>  
  
    -   <span data-ttu-id="27f90-125">O valor padrão para `HasValue` é `false`.</span><span class="sxs-lookup"><span data-stu-id="27f90-125">The default value for `HasValue` is `false`.</span></span> <span data-ttu-id="27f90-126">A propriedade `Value` não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="27f90-126">The `Value` property has no default value.</span></span>  
  
    -   <span data-ttu-id="27f90-127">Você também pode usar os operadores `==` e `!=` com um tipo que permite valor nulo, conforme mostrado no exemplo a seguir: `if (x != null) y = x;`</span><span class="sxs-lookup"><span data-stu-id="27f90-127">You can also use the `==` and `!=` operators with a nullable type, as shown in the following example: `if (x != null) y = x;`</span></span>  
  
-   <span data-ttu-id="27f90-128">Use o operador `??` para atribuir um valor padrão que será aplicado quando um tipo que permite valor nulo cujo valor atual é `null` for atribuído a um tipo não anulável, por exemplo, `int? x = null; int y = x ?? -1;`</span><span class="sxs-lookup"><span data-stu-id="27f90-128">Use the `??` operator to assign a default value that will be applied when a nullable type whose current value is `null` is assigned to a non-nullable type, for example `int? x = null; int y = x ?? -1;`</span></span>  
  
-   <span data-ttu-id="27f90-129">Os tipos que permitem valor nulo aninhados não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="27f90-129">Nested nullable types are not allowed.</span></span> <span data-ttu-id="27f90-130">A linha a seguir não será compilada: `Nullable<Nullable<int>> n;`</span><span class="sxs-lookup"><span data-stu-id="27f90-130">The following line will not compile: `Nullable<Nullable<int>> n;`</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="27f90-131">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="27f90-131">Related Sections</span></span>  
 <span data-ttu-id="27f90-132">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="27f90-132">For more information:</span></span>  
  
-   [<span data-ttu-id="27f90-133">Usando tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="27f90-133">Using Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [<span data-ttu-id="27f90-134">Conversão boxing de tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="27f90-134">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [<span data-ttu-id="27f90-135">Operador ??</span><span class="sxs-lookup"><span data-stu-id="27f90-135">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="27f90-136">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="27f90-136">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="27f90-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27f90-137">See Also</span></span>  
 <span data-ttu-id="27f90-138"><xref:System.Nullable></span><span class="sxs-lookup"><span data-stu-id="27f90-138"><xref:System.Nullable></span></span>   
 <span data-ttu-id="27f90-139">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="27f90-139">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="27f90-140">[C#](../../../csharp/index.md) </span><span class="sxs-lookup"><span data-stu-id="27f90-140">[C#](../../../csharp/index.md) </span></span>  
 <span data-ttu-id="27f90-141">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="27f90-141">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 [<span data-ttu-id="27f90-142">O que exatamente "levantado" significa?</span><span class="sxs-lookup"><span data-stu-id="27f90-142">What exactly does 'lifted' mean?</span></span>](http://go.microsoft.com/fwlink/?LinkId=112382)

