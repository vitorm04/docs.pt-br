---
title: Enums em C# - um tour pela linguagem C#
description: Saiba mais sobre enums, constantes nomeadas discretas no C#
keywords: .NET, csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 77d315dd87d9cab32605de415674d146eb9115fa
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
    
# <a name="enums"></a><span data-ttu-id="380e3-104">Enums</span><span class="sxs-lookup"><span data-stu-id="380e3-104">Enums</span></span>

<span data-ttu-id="380e3-105">Um ***tipo enum*** é um tipo de valor diferente com um conjunto de constantes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="380e3-105">An ***enum type*** is a distinct value type with a set of named constants.</span></span> <span data-ttu-id="380e3-106">Você define enums quando precisa definir um tipo que pode ter um conjunto de valores discretos.</span><span class="sxs-lookup"><span data-stu-id="380e3-106">You define enums when you need to define a type that can have a set of discrete values.</span></span> <span data-ttu-id="380e3-107">Eles usam um dos tipos de valor integral como o armazenamento subjacente.</span><span class="sxs-lookup"><span data-stu-id="380e3-107">They use one of the integral value types as their underlying storage.</span></span> <span data-ttu-id="380e3-108">Eles fornecem um significado semântico aos valores discretos.</span><span class="sxs-lookup"><span data-stu-id="380e3-108">They provide semantic meaning to the discrete values.</span></span>

<span data-ttu-id="380e3-109">O exemplo a seguir declara e usa um tipo `enum` chamado `Color` com três valores de constantes, `Red`, `Green` e `Blue`.</span><span class="sxs-lookup"><span data-stu-id="380e3-109">The following example declares and uses an `enum` type named `Color` with three constant values, `Red`, `Green`, and `Blue`.</span></span>

<span data-ttu-id="380e3-110">[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]</span><span class="sxs-lookup"><span data-stu-id="380e3-110">[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]</span></span>

<span data-ttu-id="380e3-111">Cada tipo `enum` tem um tipo integral correspondente chamado de ***tipo subjacente*** do tipo `enum`.</span><span class="sxs-lookup"><span data-stu-id="380e3-111">Each `enum` type has a corresponding integral type called the ***underlying type*** of the `enum` type.</span></span> <span data-ttu-id="380e3-112">Um tipo `enum` que não declara explicitamente um tipo subjacente tem um tipo subjacente de `int`.</span><span class="sxs-lookup"><span data-stu-id="380e3-112">An `enum` type that does not explicitly declare an underlying type has an underlying type of `int`.</span></span> <span data-ttu-id="380e3-113">Um formato de armazenamento do tipo `enum` e o intervalo de valores possíveis são determinados pelo seu tipo subjacente.</span><span class="sxs-lookup"><span data-stu-id="380e3-113">An `enum` type’s storage format and range of possible values are determined by its underlying type.</span></span> <span data-ttu-id="380e3-114">O conjunto de valores que um tipo `enum` pode lidar não é limitado pelos seus membros `enum`.</span><span class="sxs-lookup"><span data-stu-id="380e3-114">The set of values that an `enum` type can take on is not limited by its `enum` members.</span></span> <span data-ttu-id="380e3-115">Em particular, qualquer valor do tipo subjacente de um `enum` pode ser convertido em um tipo `enum` e é um valor válido diferente do que o do tipo `enum`.</span><span class="sxs-lookup"><span data-stu-id="380e3-115">In particular, any value of the underlying type of an `enum` can be cast to the `enum` type and is a distinct valid value of that `enum` type.</span></span>

<span data-ttu-id="380e3-116">O exemplo a seguir declara um tipo `enum` chamado `Alignment` com um tipo subjacente de `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="380e3-116">The following example declares an `enum` type named `Alignment` with an underlying type of `sbyte`.</span></span>

<span data-ttu-id="380e3-117">[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]</span><span class="sxs-lookup"><span data-stu-id="380e3-117">[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]</span></span>

<span data-ttu-id="380e3-118">Conforme mostrado no exemplo anterior, uma declaração de membro `enum` pode incluir uma expressão constante que especifica o valor do membro.</span><span class="sxs-lookup"><span data-stu-id="380e3-118">As shown by the previous example, an `enum` member declaration can include a constant expression that specifies the value of the member.</span></span> <span data-ttu-id="380e3-119">O valor da constante para cada membro `enum` deve estar no intervalo do tipo subjacente do `enum`.</span><span class="sxs-lookup"><span data-stu-id="380e3-119">The constant value for each `enum` member must be in the range of the underlying type of the `enum`.</span></span> <span data-ttu-id="380e3-120">Quando uma declaração de membro `enum` não especifica explicitamente um valor, o membro recebe o valor zero (se ele é o primeiro membro no tipo `enum`) ou o valor do membro `enum` textualmente precedente mais um.</span><span class="sxs-lookup"><span data-stu-id="380e3-120">When an `enum` member declaration does not explicitly specify a value, the member is given the value zero (if it is the first member in the `enum` type) or the value of the textually preceding `enum` member plus one.</span></span>

<span data-ttu-id="380e3-121">Os valores `Enum` podem ser convertidos em valores integrais e vice-versa usando conversões de tipo.</span><span class="sxs-lookup"><span data-stu-id="380e3-121">`Enum` values can be converted to integral values and vice versa using type casts.</span></span> <span data-ttu-id="380e3-122">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="380e3-122">For example:</span></span>

<span data-ttu-id="380e3-123">[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]</span><span class="sxs-lookup"><span data-stu-id="380e3-123">[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]</span></span>

<span data-ttu-id="380e3-124">O valor padrão de qualquer tipo `enum` é o valor integral zero convertido para o tipo `enum`.</span><span class="sxs-lookup"><span data-stu-id="380e3-124">The default value of any `enum` type is the integral value zero converted to the `enum` type.</span></span> <span data-ttu-id="380e3-125">Em casos nos quais as variáveis são inicializadas automaticamente como um valor padrão, esse é o valor fornecido para variáveis de tipos `enum`.</span><span class="sxs-lookup"><span data-stu-id="380e3-125">In cases where variables are automatically initialized to a default value, this is the value given to variables of `enum` types.</span></span> <span data-ttu-id="380e3-126">Para que o valor padrão de um tipo `enum` fique facilmente disponível, o `0` literal é convertido implicitamente para qualquer tipo `enum`.</span><span class="sxs-lookup"><span data-stu-id="380e3-126">In order for the default value of an `enum` type to be easily available, the literal `0` implicitly converts to any `enum` type.</span></span> <span data-ttu-id="380e3-127">Dessa forma, o seguinte é permitido.</span><span class="sxs-lookup"><span data-stu-id="380e3-127">Thus, the following is permitted.</span></span>

<span data-ttu-id="380e3-128">[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]</span><span class="sxs-lookup"><span data-stu-id="380e3-128">[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="380e3-129">[Anterior](interfaces.md)
[Próximo](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="380e3-129">[Previous](interfaces.md)
[Next](delegates.md)</span></span>

