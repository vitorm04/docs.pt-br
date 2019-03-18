---
title: Enums em C# - um tour pela linguagem C#
description: Saiba mais sobre enums, constantes nomeadas discretas no C#
ms.date: 08/10/2016
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 8c1c29c3c06829da81a9c9be8bb5bd99f1c9e395
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "57843118"
---
# <a name="enums"></a><span data-ttu-id="d4c3a-103">Enums</span><span class="sxs-lookup"><span data-stu-id="d4c3a-103">Enums</span></span>

<span data-ttu-id="d4c3a-104">Um ***tipo enum*** é um tipo de valor diferente com um conjunto de constantes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-104">An ***enum type*** is a distinct value type with a set of named constants.</span></span> <span data-ttu-id="d4c3a-105">Você define enums quando precisa definir um tipo que pode ter um conjunto de valores discretos.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-105">You define enums when you need to define a type that can have a set of discrete values.</span></span> <span data-ttu-id="d4c3a-106">Eles usam um dos tipos de valor integral como o armazenamento subjacente.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-106">They use one of the integral value types as their underlying storage.</span></span> <span data-ttu-id="d4c3a-107">Eles fornecem um significado semântico aos valores discretos.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-107">They provide semantic meaning to the discrete values.</span></span>

<span data-ttu-id="d4c3a-108">O exemplo a seguir declara e usa um tipo `enum` chamado `Color` com três valores de constantes, `Red`, `Green` e `Blue`.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-108">The following example declares and uses an `enum` type named `Color` with three constant values, `Red`, `Green`, and `Blue`.</span></span>

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

<span data-ttu-id="d4c3a-109">Cada tipo `enum` tem um tipo integral correspondente chamado de ***tipo subjacente*** do tipo `enum`.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-109">Each `enum` type has a corresponding integral type called the ***underlying type*** of the `enum` type.</span></span> <span data-ttu-id="d4c3a-110">Um tipo `enum` que não declara explicitamente um tipo subjacente tem um tipo subjacente de `int`.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-110">An `enum` type that does not explicitly declare an underlying type has an underlying type of `int`.</span></span> <span data-ttu-id="d4c3a-111">Um formato de armazenamento do tipo `enum` e o intervalo de valores possíveis são determinados pelo seu tipo subjacente.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-111">An `enum` type’s storage format and range of possible values are determined by its underlying type.</span></span> <span data-ttu-id="d4c3a-112">O conjunto de valores que um tipo `enum` pode lidar não é limitado pelos seus membros `enum`.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-112">The set of values that an `enum` type can take on is not limited by its `enum` members.</span></span> <span data-ttu-id="d4c3a-113">Em particular, qualquer valor do tipo subjacente de um `enum` pode ser convertido em um tipo `enum` e é um valor válido diferente do que o do tipo `enum`.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-113">In particular, any value of the underlying type of an `enum` can be cast to the `enum` type and is a distinct valid value of that `enum` type.</span></span>

<span data-ttu-id="d4c3a-114">O exemplo a seguir declara um tipo `enum` chamado `Alignment` com um tipo subjacente de `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-114">The following example declares an `enum` type named `Alignment` with an underlying type of `sbyte`.</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

<span data-ttu-id="d4c3a-115">Conforme mostrado no exemplo anterior, uma declaração de membro `enum` pode incluir uma expressão constante que especifica o valor do membro.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-115">As shown by the previous example, an `enum` member declaration can include a constant expression that specifies the value of the member.</span></span> <span data-ttu-id="d4c3a-116">O valor da constante para cada membro `enum` deve estar no intervalo do tipo subjacente do `enum`.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-116">The constant value for each `enum` member must be in the range of the underlying type of the `enum`.</span></span> <span data-ttu-id="d4c3a-117">Quando uma declaração de membro `enum` não especifica explicitamente um valor, o membro recebe o valor zero (se ele é o primeiro membro no tipo `enum`) ou o valor do membro `enum` textualmente precedente mais um.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-117">When an `enum` member declaration does not explicitly specify a value, the member is given the value zero (if it is the first member in the `enum` type) or the value of the textually preceding `enum` member plus one.</span></span>

<span data-ttu-id="d4c3a-118">Os valores `Enum` podem ser convertidos em valores integrais e vice-versa usando conversões de tipo.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-118">`Enum` values can be converted to integral values and vice versa using type casts.</span></span> <span data-ttu-id="d4c3a-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d4c3a-119">For example:</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

<span data-ttu-id="d4c3a-120">O valor padrão de qualquer tipo `enum` é o valor integral zero convertido para o tipo `enum`.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-120">The default value of any `enum` type is the integral value zero converted to the `enum` type.</span></span> <span data-ttu-id="d4c3a-121">Em casos nos quais as variáveis são inicializadas automaticamente como um valor padrão, esse é o valor fornecido para variáveis de tipos `enum`.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-121">In cases where variables are automatically initialized to a default value, this is the value given to variables of `enum` types.</span></span> <span data-ttu-id="d4c3a-122">Para que o valor padrão de um tipo `enum` fique facilmente disponível, o `0` literal é convertido implicitamente para qualquer tipo `enum`.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-122">In order for the default value of an `enum` type to be easily available, the literal `0` implicitly converts to any `enum` type.</span></span> <span data-ttu-id="d4c3a-123">Dessa forma, o seguinte é permitido.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-123">Thus, the following is permitted.</span></span>

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

> [!div class="step-by-step"]
> <span data-ttu-id="d4c3a-124">[Anterior](interfaces.md)
> [Próximo](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="d4c3a-124">[Previous](interfaces.md)
[Next](delegates.md)</span></span>
