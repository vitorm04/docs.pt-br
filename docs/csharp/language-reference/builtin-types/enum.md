---
title: Tipos de enumeração - Referência C#
description: Saiba mais sobre os tipos de enumeração C# que representam uma escolha ou uma combinação de escolhas
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
ms.openlocfilehash: 617c5ec037ad7a47b43cca2c13da4a77aa682997
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739084"
---
# <a name="enumeration-types-c-reference"></a><span data-ttu-id="d6205-103">Tipos de enumeração (referência C#)</span><span class="sxs-lookup"><span data-stu-id="d6205-103">Enumeration types (C# reference)</span></span>

<span data-ttu-id="d6205-104">Um *tipo de enumeração* (ou *tipo enum)* é um tipo de [valor](value-types.md) definido por um conjunto de constantes nomeadas do tipo [numérico integral](integral-numeric-types.md) subjacente.</span><span class="sxs-lookup"><span data-stu-id="d6205-104">An *enumeration type* (or *enum type*) is a [value type](value-types.md) defined by a set of named constants of the underlying [integral numeric](integral-numeric-types.md) type.</span></span> <span data-ttu-id="d6205-105">Para definir um tipo de `enum` enumeração, use a palavra-chave e especifique os nomes dos membros do *enum:*</span><span class="sxs-lookup"><span data-stu-id="d6205-105">To define an enumeration type, use the `enum` keyword and specify the names of *enum members*:</span></span>

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

<span data-ttu-id="d6205-106">Por padrão, os valores constantes associados `int`dos membros enum são do tipo; eles começam com zero e aumentam por um seguindo a ordem de texto de definição.</span><span class="sxs-lookup"><span data-stu-id="d6205-106">By default, the associated constant values of enum members are of type `int`; they start with zero and increase by one following the definition text order.</span></span> <span data-ttu-id="d6205-107">Você pode especificar explicitamente qualquer outro tipo [numérico integral](integral-numeric-types.md) como um tipo subjacente de um tipo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="d6205-107">You can explicitly specify any other [integral numeric](integral-numeric-types.md) type as an underlying type of an enumeration type.</span></span> <span data-ttu-id="d6205-108">Você também pode especificar explicitamente os valores constantes associados, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d6205-108">You can also explicitly specify the associated constant values, as the following example shows:</span></span>

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

<span data-ttu-id="d6205-109">Você não pode definir um método dentro da definição de um tipo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="d6205-109">You cannot define a method inside the definition of an enumeration type.</span></span> <span data-ttu-id="d6205-110">Para adicionar funcionalidade a um tipo de enumeração, crie um [método de extensão](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="d6205-110">To add functionality to an enumeration type, create an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="d6205-111">O valor padrão de um `E` tipo de enumeração é o valor produzido pela expressão, `(E)0`mesmo que zero não tenha o membro enum correspondente.</span><span class="sxs-lookup"><span data-stu-id="d6205-111">The default value of an enumeration type `E` is the value produced by expression `(E)0`, even if zero doesn't have the corresponding enum member.</span></span>

<span data-ttu-id="d6205-112">Você usa um tipo de enumeração para representar uma escolha de um conjunto de valores mutuamente exclusivos ou uma combinação de escolhas.</span><span class="sxs-lookup"><span data-stu-id="d6205-112">You use an enumeration type to represent a choice from a set of mutually exclusive values or a combination of choices.</span></span> <span data-ttu-id="d6205-113">Para representar uma combinação de opções, defina um tipo de enumeração como sinalizadores de bit.</span><span class="sxs-lookup"><span data-stu-id="d6205-113">To represent a combination of choices, define an enumeration type as bit flags.</span></span>

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="d6205-114">Tipos de Enumeração como Sinalizadores de Bit</span><span class="sxs-lookup"><span data-stu-id="d6205-114">Enumeration types as bit flags</span></span>

<span data-ttu-id="d6205-115">Se você quiser que um tipo de enumeração represente uma combinação de escolhas, defina os membros do enum para essas escolhas de tal forma que uma escolha individual seja um pouco de campo.</span><span class="sxs-lookup"><span data-stu-id="d6205-115">If you want an enumeration type to represent a combination of choices, define enum members for those choices such that an individual choice is a bit field.</span></span> <span data-ttu-id="d6205-116">Ou seja, os valores associados desses membros do enum devem ser os poderes de dois.</span><span class="sxs-lookup"><span data-stu-id="d6205-116">That is, the associated values of those enum members should be the powers of two.</span></span> <span data-ttu-id="d6205-117">Em seguida, você pode usar os [operadores lógicos `|` bitwise ou `&` ](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) para combinar escolhas ou interceptar combinações de escolhas, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="d6205-117">Then, you can use the [bitwise logical operators `|` or `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) to combine choices or intersect combinations of choices, respectively.</span></span> <span data-ttu-id="d6205-118">Para indicar que um tipo de enumeração declara campos de bits, aplique o atributo [Sinalizadores](xref:System.FlagsAttribute) a ele.</span><span class="sxs-lookup"><span data-stu-id="d6205-118">To indicate that an enumeration type declares bit fields, apply the [Flags](xref:System.FlagsAttribute) attribute to it.</span></span> <span data-ttu-id="d6205-119">Como o exemplo a seguir mostra, você também pode incluir algumas combinações típicas na definição de um tipo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="d6205-119">As the following example shows, you can also include some typical combinations in the definition of an enumeration type.</span></span>

[!code-csharp[enum flags](snippets/EnumType.cs#Flags)]

<span data-ttu-id="d6205-120">Para obter mais informações e <xref:System.FlagsAttribute?displayProperty=nameWithType> exemplos, consulte a página de referência da API e os membros não exclusivos e a seção de [atributoS da](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) página de referência da <xref:System.Enum?displayProperty=nameWithType> API.</span><span class="sxs-lookup"><span data-stu-id="d6205-120">For more information and examples, see the <xref:System.FlagsAttribute?displayProperty=nameWithType> API reference page and the [Non-exclusive members and the Flags attribute](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) section of the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

## <a name="the-systemenum-type-and-enum-constraint"></a><span data-ttu-id="d6205-121">A restrição system.enum e enum</span><span class="sxs-lookup"><span data-stu-id="d6205-121">The System.Enum type and enum constraint</span></span>

<span data-ttu-id="d6205-122">O <xref:System.Enum?displayProperty=nameWithType> tipo é a classe base abstrata de todos os tipos de enumeração.</span><span class="sxs-lookup"><span data-stu-id="d6205-122">The <xref:System.Enum?displayProperty=nameWithType> type is the abstract base class of all enumeration types.</span></span> <span data-ttu-id="d6205-123">Ele fornece uma série de métodos para obter informações sobre um tipo de enumeração e seus valores.</span><span class="sxs-lookup"><span data-stu-id="d6205-123">It provides a number of methods to get information about an enumeration type and its values.</span></span> <span data-ttu-id="d6205-124">Para obter mais informações e <xref:System.Enum?displayProperty=nameWithType> exemplos, consulte a página de referência da API.</span><span class="sxs-lookup"><span data-stu-id="d6205-124">For more information and examples, see the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

<span data-ttu-id="d6205-125">Começando com C# 7.3, `System.Enum` você pode usar em uma restrição de classe base (que é conhecida como [restrição de enum](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) para especificar que um parâmetro de tipo é um tipo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="d6205-125">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="conversions"></a><span data-ttu-id="d6205-126">Conversões</span><span class="sxs-lookup"><span data-stu-id="d6205-126">Conversions</span></span>

<span data-ttu-id="d6205-127">Para qualquer tipo de enumeração, existem conversões explícitas entre o tipo de enumeração e seu tipo integral subjacente.</span><span class="sxs-lookup"><span data-stu-id="d6205-127">For any enumeration type, there exist explicit conversions between the enumeration type and its underlying integral type.</span></span> <span data-ttu-id="d6205-128">Se você [lançar](../operators/type-testing-and-cast.md#cast-expression) um valor de enum para o seu tipo subjacente, o resultado é o valor integral associado de um membro enum.</span><span class="sxs-lookup"><span data-stu-id="d6205-128">If you [cast](../operators/type-testing-and-cast.md#cast-expression) an enum value to its underlying type, the result is the associated integral value of an enum member.</span></span>

[!code-csharp[enum conversions](snippets/EnumType.cs#Conversions)]

<span data-ttu-id="d6205-129">Use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> o método para determinar se um tipo de enumeração contém um membro enum com o determinado valor associado.</span><span class="sxs-lookup"><span data-stu-id="d6205-129">Use the <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> method to determine whether an enumeration type contains an enum member with the certain associated value.</span></span>

<span data-ttu-id="d6205-130">Para qualquer tipo de enumeração, existem conversões <xref:System.Enum?displayProperty=nameWithType> de boxe e [unboxing](../../programming-guide/types/boxing-and-unboxing.md) para e do tipo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="d6205-130">For any enumeration type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.Enum?displayProperty=nameWithType> type, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d6205-131">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d6205-131">C# language specification</span></span>

<span data-ttu-id="d6205-132">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="d6205-132">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="d6205-133">Enums</span><span class="sxs-lookup"><span data-stu-id="d6205-133">Enums</span></span>](~/_csharplang/spec/enums.md)
- [<span data-ttu-id="d6205-134">Operações e valores de enum</span><span class="sxs-lookup"><span data-stu-id="d6205-134">Enum values and operations</span></span>](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [<span data-ttu-id="d6205-135">Operadores lógicos de enumeração</span><span class="sxs-lookup"><span data-stu-id="d6205-135">Enumeration logical operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [<span data-ttu-id="d6205-136">Operadores de comparação de enumeração</span><span class="sxs-lookup"><span data-stu-id="d6205-136">Enumeration comparison operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [<span data-ttu-id="d6205-137">Conversões explícitas de enumeração</span><span class="sxs-lookup"><span data-stu-id="d6205-137">Explicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [<span data-ttu-id="d6205-138">Conversões implícitas de enumeração</span><span class="sxs-lookup"><span data-stu-id="d6205-138">Implicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a><span data-ttu-id="d6205-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="d6205-139">See also</span></span>

- [<span data-ttu-id="d6205-140">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="d6205-140">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d6205-141">Cadeias de caracteres de formato de enumeração</span><span class="sxs-lookup"><span data-stu-id="d6205-141">Enumeration format strings</span></span>](../../../standard/base-types/enumeration-format-strings.md)
- [<span data-ttu-id="d6205-142">Diretrizes de design - Design enum</span><span class="sxs-lookup"><span data-stu-id="d6205-142">Design guidelines - Enum design</span></span>](../../../standard/design-guidelines/enum.md)
- [<span data-ttu-id="d6205-143">Diretrizes de design - Convenções de nomeação enum</span><span class="sxs-lookup"><span data-stu-id="d6205-143">Design guidelines - Enum naming conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [<span data-ttu-id="d6205-144">Instrução switch</span><span class="sxs-lookup"><span data-stu-id="d6205-144">switch statement</span></span>](../keywords/switch.md)
