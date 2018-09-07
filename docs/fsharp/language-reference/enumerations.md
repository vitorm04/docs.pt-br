---
title: Enumerações (F#)
description: 'Saiba como usar F # enumerações no lugar de literais para tornar seu código mais legível e sustentável.'
ms.date: 05/16/2016
ms.openlocfilehash: 47fb353c2698f8b1474834ebbd1b0eff2c7f76e7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097081"
---
# <a name="enumerations"></a><span data-ttu-id="5e71a-103">Enumerações</span><span class="sxs-lookup"><span data-stu-id="5e71a-103">Enumerations</span></span>

<span data-ttu-id="5e71a-104">*Enumerações*, também conhecido como *enums*, são tipos integrais onde os rótulos são atribuídos a um subconjunto dos valores.</span><span class="sxs-lookup"><span data-stu-id="5e71a-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="5e71a-105">Você pode usá-los no lugar de literais para tornar o código mais legível e fácil de manter.</span><span class="sxs-lookup"><span data-stu-id="5e71a-105">You can use them in place of literals to make code more readable and maintainable.</span></span>

## <a name="syntax"></a><span data-ttu-id="5e71a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e71a-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="5e71a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e71a-107">Remarks</span></span>

<span data-ttu-id="5e71a-108">Uma enumeração se parece muito com uma união discriminada que tem valores simples, exceto que os valores podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="5e71a-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="5e71a-109">Normalmente, os valores são inteiros que começam em 0 ou 1, ou inteiros que representam as posições de bit.</span><span class="sxs-lookup"><span data-stu-id="5e71a-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="5e71a-110">Se uma enumeração destina-se para representar as posições de bit, você também deve usar o [sinalizadores](xref:System.FlagsAttribute) atributo.</span><span class="sxs-lookup"><span data-stu-id="5e71a-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="5e71a-111">O tipo subjacente da enumeração é determinado de literal que é usado, para que, por exemplo, você pode usar literais com um sufixo, tal como `1u`, `2u`e assim por diante, para um inteiro sem sinal (`uint32`) tipo.</span><span class="sxs-lookup"><span data-stu-id="5e71a-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="5e71a-112">Quando você faz referência os valores nomeados, você deve usar o nome do próprio tipo de enumeração como um qualificador, ou seja, `enum-name.value1`, não apenas `value1`.</span><span class="sxs-lookup"><span data-stu-id="5e71a-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="5e71a-113">Esse comportamento é diferente do de uniões discriminadas.</span><span class="sxs-lookup"><span data-stu-id="5e71a-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="5e71a-114">Isso ocorre porque as enumerações sempre têm o [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atributo.</span><span class="sxs-lookup"><span data-stu-id="5e71a-114">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="5e71a-115">O código a seguir mostra a declaração e o uso de uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="5e71a-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="5e71a-116">Você pode converter facilmente enumerações para o tipo subjacente, usando o operador apropriado, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5e71a-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="5e71a-117">Tipos enumerados podem ter um dos seguintes tipos de base: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, e `char`.</span><span class="sxs-lookup"><span data-stu-id="5e71a-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="5e71a-118">Tipos de enumeração são representados no .NET Framework como tipos que são herdados de `System.Enum`, que por sua vez é herdado da `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="5e71a-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="5e71a-119">Assim, eles são tipos de valor que estão localizados na pilha ou embutido no objeto recipiente e qualquer valor do tipo subjacente é um valor válido da enumeração.</span><span class="sxs-lookup"><span data-stu-id="5e71a-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="5e71a-120">Isso é significativo quando valores de correspondência de padrões na enumeração, porque você precisa fornecer um padrão que captura os valores sem nome.</span><span class="sxs-lookup"><span data-stu-id="5e71a-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="5e71a-121">O `enum` função na biblioteca do F # pode ser usada para gerar um valor de enumeração, até mesmo um valor diferente de predefinida, valores nomeados.</span><span class="sxs-lookup"><span data-stu-id="5e71a-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="5e71a-122">Você usa o `enum` funcionam da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="5e71a-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="5e71a-123">O padrão `enum` função funciona com o tipo `int32`.</span><span class="sxs-lookup"><span data-stu-id="5e71a-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="5e71a-124">Portanto, ele não pode ser usado com tipos de enumeração que têm outros tipos subjacentes.</span><span class="sxs-lookup"><span data-stu-id="5e71a-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="5e71a-125">Em vez disso, use o seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e71a-125">Instead, use the following.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

<span data-ttu-id="5e71a-126">Além disso, casos para enums sempre são emitidos como `public`.</span><span class="sxs-lookup"><span data-stu-id="5e71a-126">Additionally, cases for enums are always emitted as `public`.</span></span> <span data-ttu-id="5e71a-127">Isso é para que eles se alinham com c# e o restante da plataforma .NET.</span><span class="sxs-lookup"><span data-stu-id="5e71a-127">This is so that they align with C# and the rest of the .NET platform.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e71a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e71a-128">See also</span></span>

- [<span data-ttu-id="5e71a-129">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="5e71a-129">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="5e71a-130">Conversões Cast e conversões</span><span class="sxs-lookup"><span data-stu-id="5e71a-130">Casting and Conversions</span></span>](casting-and-conversions.md)
