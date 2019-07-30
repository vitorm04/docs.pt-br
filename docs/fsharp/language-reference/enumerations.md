---
title: Enumerações
description: Saiba como usar F# enumerações em vez de literais para tornar seu código mais legível e passível de manutenção.
ms.date: 05/16/2016
ms.openlocfilehash: 784cd9612b199e4648bb64432d3b4422ad35f649
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630342"
---
# <a name="enumerations"></a><span data-ttu-id="cab0d-103">Enumerações</span><span class="sxs-lookup"><span data-stu-id="cab0d-103">Enumerations</span></span>

<span data-ttu-id="cab0d-104">*Enumerações*, também conhecidas como *enums*, são tipos integrais em que os rótulos são atribuídos a um subconjunto dos valores.</span><span class="sxs-lookup"><span data-stu-id="cab0d-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="cab0d-105">Você pode usá-los no lugar de literais para tornar o código mais legível e fácil de manter.</span><span class="sxs-lookup"><span data-stu-id="cab0d-105">You can use them in place of literals to make code more readable and maintainable.</span></span>

## <a name="syntax"></a><span data-ttu-id="cab0d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cab0d-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="cab0d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="cab0d-107">Remarks</span></span>

<span data-ttu-id="cab0d-108">Uma enumeração é muito parecida com uma união discriminada que tem valores simples, exceto que os valores podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="cab0d-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="cab0d-109">Os valores normalmente são inteiros que começam com 0 ou 1, ou inteiros que representam posições de bits.</span><span class="sxs-lookup"><span data-stu-id="cab0d-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="cab0d-110">Se uma enumeração for destinada a representar posições de bits, você também deverá usar o atributo [flags](xref:System.FlagsAttribute) .</span><span class="sxs-lookup"><span data-stu-id="cab0d-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="cab0d-111">O tipo subjacente da enumeração é determinado a partir do literal que é usado, de modo que, por exemplo, você possa usar literais com um sufixo, `1u`como, `2u`e assim por diante, para um tipo inteiro não assinado (`uint32`).</span><span class="sxs-lookup"><span data-stu-id="cab0d-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="cab0d-112">Quando você se referir aos valores nomeados, deverá usar o nome do tipo de enumeração como um qualificador, ou seja `enum-name.value1`,, não `value1`apenas.</span><span class="sxs-lookup"><span data-stu-id="cab0d-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="cab0d-113">Esse comportamento é diferente do de uniões discriminadas.</span><span class="sxs-lookup"><span data-stu-id="cab0d-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="cab0d-114">Isso ocorre porque as enumerações sempre têm o atributo [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) .</span><span class="sxs-lookup"><span data-stu-id="cab0d-114">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="cab0d-115">O código a seguir mostra a declaração e o uso de uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="cab0d-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="cab0d-116">Você pode facilmente converter enumerações para o tipo subjacente usando o operador apropriado, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="cab0d-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="cab0d-117">Os tipos enumerados podem ter um dos seguintes tipos subjacentes `sbyte`: `byte` `int16`,, `uint16`, `int32` `uint32`,, `int64`, `uint16` `uint64`,, e `char`.</span><span class="sxs-lookup"><span data-stu-id="cab0d-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="cab0d-118">Os tipos de enumeração são representados no .NET Framework como tipos herdados `System.Enum`de, que, por sua vez `System.ValueType`, são herdados de.</span><span class="sxs-lookup"><span data-stu-id="cab0d-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="cab0d-119">Portanto, eles são tipos de valor que estão localizados na pilha ou embutidos no objeto contentor, e qualquer valor do tipo subjacente é um valor válido da enumeração.</span><span class="sxs-lookup"><span data-stu-id="cab0d-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="cab0d-120">Isso é significativo quando o padrão corresponde aos valores de enumeração, pois você precisa fornecer um padrão que captura os valores sem nome.</span><span class="sxs-lookup"><span data-stu-id="cab0d-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="cab0d-121">A `enum` função na F# biblioteca pode ser usada para gerar um valor de enumeração, mesmo um valor diferente de um dos valores nomeados predefinidos.</span><span class="sxs-lookup"><span data-stu-id="cab0d-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="cab0d-122">Você usa a `enum` função da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="cab0d-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="cab0d-123">A função `enum` padrão funciona com o `int32`tipo.</span><span class="sxs-lookup"><span data-stu-id="cab0d-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="cab0d-124">Portanto, ele não pode ser usado com tipos de enumeração que têm outros tipos subjacentes.</span><span class="sxs-lookup"><span data-stu-id="cab0d-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="cab0d-125">Em vez disso, use o seguinte.</span><span class="sxs-lookup"><span data-stu-id="cab0d-125">Instead, use the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

<span data-ttu-id="cab0d-126">Além disso, os casos de enums são sempre emitidos como `public`.</span><span class="sxs-lookup"><span data-stu-id="cab0d-126">Additionally, cases for enums are always emitted as `public`.</span></span> <span data-ttu-id="cab0d-127">Isso é para que eles se alinhem com C# o e o restante da plataforma .net.</span><span class="sxs-lookup"><span data-stu-id="cab0d-127">This is so that they align with C# and the rest of the .NET platform.</span></span>

## <a name="see-also"></a><span data-ttu-id="cab0d-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cab0d-128">See also</span></span>

- [<span data-ttu-id="cab0d-129">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="cab0d-129">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="cab0d-130">Conversões Cast e conversões</span><span class="sxs-lookup"><span data-stu-id="cab0d-130">Casting and Conversions</span></span>](casting-and-conversions.md)
