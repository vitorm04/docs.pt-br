---
title: Tipos de enumeração C# -referência
description: Saiba mais C# sobre tipos de enumeração que representam uma opção ou uma combinação de opções
ms.date: 12/13/2019
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
- enum type [C#]
- enumeration type [C#]
- bit flags [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 72bc867bf0a789279da9a01f97c85d96b78684ed
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75444343"
---
# <a name="enumeration-types-c-reference"></a><span data-ttu-id="e0c57-103">Tipos de enumeraçãoC# (referência)</span><span class="sxs-lookup"><span data-stu-id="e0c57-103">Enumeration types (C# reference)</span></span>

<span data-ttu-id="e0c57-104">Um tipo de enumeração (ou tipo de enumeração) é um tipo de valor definido por um conjunto de constantes nomeadas do tipo [numérico integral](integral-numeric-types.md) subjacente.</span><span class="sxs-lookup"><span data-stu-id="e0c57-104">An enumeration type (or enum type) is a value type defined by a set of named constants of the underlying [integral numeric](integral-numeric-types.md) type.</span></span> <span data-ttu-id="e0c57-105">Para definir um tipo de enumeração, use a palavra-chave `enum` e especifique os nomes dos *membros de enumeração*:</span><span class="sxs-lookup"><span data-stu-id="e0c57-105">To define an enumeration type, use the `enum` keyword and specify the names of *enum members*:</span></span>

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

<span data-ttu-id="e0c57-106">Por padrão, os valores constantes associados de membros de enumeração são do tipo `int`; Eles começam com zero e aumentam em um seguindo a ordem de texto de definição.</span><span class="sxs-lookup"><span data-stu-id="e0c57-106">By default, the associated constant values of enum members are of type `int`; they start with zero and increase by one following the definition text order.</span></span> <span data-ttu-id="e0c57-107">Você pode especificar explicitamente qualquer outro tipo [numérico integral](integral-numeric-types.md) como um tipo subjacente de um tipo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="e0c57-107">You can explicitly specify any other [integral numeric](integral-numeric-types.md) type as an underlying type of an enumeration type.</span></span> <span data-ttu-id="e0c57-108">Você também pode especificar explicitamente os valores constantes associados, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e0c57-108">You also can explicitly specify the associated constant values, as the following example shows:</span></span>

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

<span data-ttu-id="e0c57-109">Você não pode definir um método dentro da definição de um tipo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="e0c57-109">You cannot define a method inside the definition of an enumeration type.</span></span> <span data-ttu-id="e0c57-110">Para adicionar funcionalidade a um tipo de enumeração, crie um [método de extensão](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e0c57-110">To add functionality to an enumeration type, create an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="e0c57-111">O valor padrão de um tipo de enumeração `E` é o valor produzido pelo Expression `(E)0`, mesmo se zero não tiver o membro enum correspondente.</span><span class="sxs-lookup"><span data-stu-id="e0c57-111">The default value of an enumeration type `E` is the value produced by expression `(E)0`, even if zero doesn't have the corresponding enum member.</span></span>

<span data-ttu-id="e0c57-112">Você usa um tipo de enumeração para representar uma escolha de um conjunto de valores mutuamente exclusivos ou uma combinação de opções.</span><span class="sxs-lookup"><span data-stu-id="e0c57-112">You use an enumeration type to represent a choice from a set of mutually exclusive values or a combination of choices.</span></span> <span data-ttu-id="e0c57-113">Para representar uma combinação de opções, defina um tipo de enumeração como sinalizadores de bits.</span><span class="sxs-lookup"><span data-stu-id="e0c57-113">To represent a combination of choices, define an enumeration type as bit flags.</span></span>

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="e0c57-114">Tipos de Enumeração como Sinalizadores de Bit</span><span class="sxs-lookup"><span data-stu-id="e0c57-114">Enumeration types as bit flags</span></span>

<span data-ttu-id="e0c57-115">Se você quiser que um tipo de enumeração represente uma combinação de opções, defina membros de enum para essas opções, de modo que uma opção individual seja um campo de bits.</span><span class="sxs-lookup"><span data-stu-id="e0c57-115">If you want an enumeration type to represent a combination of choices, define enum members for those choices such that an individual choice is a bit field.</span></span> <span data-ttu-id="e0c57-116">Ou seja, os valores associados desses membros de enumeração devem ser as potências de dois.</span><span class="sxs-lookup"><span data-stu-id="e0c57-116">That is, the associated values of those enum members should be the powers of two.</span></span> <span data-ttu-id="e0c57-117">Em seguida, você pode usar os [operadores lógicos de bits bit a `|` ou `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) para combinar opções ou combinações de interseção de opções, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e0c57-117">Then, you can use the [bitwise logical operators `|` or `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) to combine choices or intersect combinations of choices, respectively.</span></span> <span data-ttu-id="e0c57-118">Para indicar que um tipo de enumeração declara campos de bits, aplique o atributo [flags](xref:System.FlagsAttribute) a ele.</span><span class="sxs-lookup"><span data-stu-id="e0c57-118">To indicate that an enumeration type declares bit fields, apply the [Flags](xref:System.FlagsAttribute) attribute to it.</span></span> <span data-ttu-id="e0c57-119">Como mostra o exemplo a seguir, você também pode incluir algumas combinações típicas na definição de um tipo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="e0c57-119">As the following example shows, you also can include some typical combinations in the definition of an enumeration type.</span></span>

[!code-csharp[enum flags](~/samples/csharp/language-reference/builtin-types/EnumType.cs#Flags)]

<span data-ttu-id="e0c57-120">Para obter mais informações e exemplos, consulte a página de referência da API <xref:System.FlagsAttribute?displayProperty=nameWithType> e os [Membros não exclusivos e a seção de atributo flags](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) da página de referência da API <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e0c57-120">For more information and examples, see the <xref:System.FlagsAttribute?displayProperty=nameWithType> API reference page and the [Non-exclusive members and the Flags attribute](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) section of the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

## <a name="the-systemenum-type-and-enum-constraint"></a><span data-ttu-id="e0c57-121">O tipo System. Enum e a restrição enum</span><span class="sxs-lookup"><span data-stu-id="e0c57-121">The System.Enum type and enum constraint</span></span>

<span data-ttu-id="e0c57-122">O tipo de <xref:System.Enum?displayProperty=nameWithType> é a classe base abstrata de todos os tipos de enumeração.</span><span class="sxs-lookup"><span data-stu-id="e0c57-122">The <xref:System.Enum?displayProperty=nameWithType> type is the abstract base class of all enumeration types.</span></span> <span data-ttu-id="e0c57-123">Ele fornece vários métodos para obter informações sobre um tipo de enumeração e seus valores.</span><span class="sxs-lookup"><span data-stu-id="e0c57-123">It provides a number of methods to get information about an enumeration type and its values.</span></span> <span data-ttu-id="e0c57-124">Para obter mais informações e exemplos, consulte a página de referência da API <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e0c57-124">For more information and examples, see the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

<span data-ttu-id="e0c57-125">A partir C# do 7,3, você pode usar `System.Enum` em uma restrição de classe base (que é conhecida como [restrição de enumeração](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) para especificar que um parâmetro de tipo é um tipo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="e0c57-125">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="conversions"></a><span data-ttu-id="e0c57-126">Conversões</span><span class="sxs-lookup"><span data-stu-id="e0c57-126">Conversions</span></span>

<span data-ttu-id="e0c57-127">Para qualquer tipo de enumeração, existem conversões explícitas entre o tipo de enumeração e seu tipo integral subjacente.</span><span class="sxs-lookup"><span data-stu-id="e0c57-127">For any enumeration type, there exist explicit conversions between the enumeration type and its underlying integral type.</span></span> <span data-ttu-id="e0c57-128">Se você [converter](../operators/type-testing-and-cast.md#cast-operator-) um valor de enumeração para seu tipo subjacente, o resultado será o valor integral associado de um membro de enumeração.</span><span class="sxs-lookup"><span data-stu-id="e0c57-128">If you [cast](../operators/type-testing-and-cast.md#cast-operator-) an enum value to its underlying type, the result is the associated integral value of an enum member.</span></span>

[!code-csharp[enum conversions](~/samples/csharp/language-reference/builtin-types/EnumType.cs#Conversions)]

<span data-ttu-id="e0c57-129">Use o método <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> para determinar se um tipo de enumeração contém um membro enum com determinado valor associado.</span><span class="sxs-lookup"><span data-stu-id="e0c57-129">Use the <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> method to determine whether an enumeration type contains an enum member with the certain associated value.</span></span>

<span data-ttu-id="e0c57-130">Para qualquer tipo de enumeração, existem conversões [boxing e unboxing](../../programming-guide/types/boxing-and-unboxing.md) de e para o tipo <xref:System.Enum?displayProperty=nameWithType>, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e0c57-130">For any enumeration type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.Enum?displayProperty=nameWithType> type, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e0c57-131">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e0c57-131">C# language specification</span></span>

<span data-ttu-id="e0c57-132">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="e0c57-132">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="e0c57-133">Enums</span><span class="sxs-lookup"><span data-stu-id="e0c57-133">Enums</span></span>](~/_csharplang/spec/enums.md)
- [<span data-ttu-id="e0c57-134">Operações e valores de enum</span><span class="sxs-lookup"><span data-stu-id="e0c57-134">Enum values and operations</span></span>](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [<span data-ttu-id="e0c57-135">Operadores lógicos de enumeração</span><span class="sxs-lookup"><span data-stu-id="e0c57-135">Enumeration logical operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [<span data-ttu-id="e0c57-136">Operadores de comparação de enumeração</span><span class="sxs-lookup"><span data-stu-id="e0c57-136">Enumeration comparison operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [<span data-ttu-id="e0c57-137">Conversões de enumeração explícitas</span><span class="sxs-lookup"><span data-stu-id="e0c57-137">Explicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [<span data-ttu-id="e0c57-138">Conversões implícitas de enumeração</span><span class="sxs-lookup"><span data-stu-id="e0c57-138">Implicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a><span data-ttu-id="e0c57-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="e0c57-139">See also</span></span>

- [<span data-ttu-id="e0c57-140">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e0c57-140">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e0c57-141">Cadeias de caracteres de formato de enumeração</span><span class="sxs-lookup"><span data-stu-id="e0c57-141">Enumeration format strings</span></span>](../../../standard/base-types/enumeration-format-strings.md)
- [<span data-ttu-id="e0c57-142">Convenções de nomenclatura de enumeração</span><span class="sxs-lookup"><span data-stu-id="e0c57-142">Enum naming conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [<span data-ttu-id="e0c57-143">instrução switch</span><span class="sxs-lookup"><span data-stu-id="e0c57-143">switch statement</span></span>](../keywords/switch.md)
