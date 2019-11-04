---
title: Opções de valores
description: Saiba mais sobre F# o tipo de opção de valor, que é uma versão de struct do tipo de opção.
ms.date: 02/06/2019
ms.openlocfilehash: 4dc3f7217943345b7aaf1165fd648ab2e01bd727
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424014"
---
# <a name="value-options"></a><span data-ttu-id="99433-103">Opções de valores</span><span class="sxs-lookup"><span data-stu-id="99433-103">Value Options</span></span>

<span data-ttu-id="99433-104">O tipo de opção de F# valor em é usado quando as duas circunstâncias a seguir têm:</span><span class="sxs-lookup"><span data-stu-id="99433-104">The Value Option type in F# is used when the following two circumstances hold:</span></span>

1. <span data-ttu-id="99433-105">Um cenário é apropriado para uma [ F# opção](options.md).</span><span class="sxs-lookup"><span data-stu-id="99433-105">A scenario is appropriate for an [F# Option](options.md).</span></span>
2. <span data-ttu-id="99433-106">O uso de uma estrutura fornece um benefício de desempenho em seu cenário.</span><span class="sxs-lookup"><span data-stu-id="99433-106">Using a struct provides a performance benefit in your scenario.</span></span>

<span data-ttu-id="99433-107">Nem todos os cenários sensíveis ao desempenho são "resolvidos" usando structs.</span><span class="sxs-lookup"><span data-stu-id="99433-107">Not all performance-sensitive scenarios are "solved" by using structs.</span></span> <span data-ttu-id="99433-108">Você deve considerar o custo adicional de copiar ao usá-los em vez de tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="99433-108">You must consider the additional cost of copying when using them instead of reference types.</span></span> <span data-ttu-id="99433-109">No entanto F# , programas grandes normalmente instanciam muitos tipos opcionais que fluem por meio de caminhos ativos e, nesses casos, as estruturas geralmente podem produzir melhor desempenho geral durante o tempo de vida de um programa.</span><span class="sxs-lookup"><span data-stu-id="99433-109">However, large F# programs commonly instantiate many optional types that flow through hot paths, and in such cases, structs can often yield better overall performance over the lifetime of a program.</span></span>

## <a name="definition"></a><span data-ttu-id="99433-110">Definição</span><span class="sxs-lookup"><span data-stu-id="99433-110">Definition</span></span>

<span data-ttu-id="99433-111">A opção Value é definida como uma [união discriminada de struct](discriminated-unions.md#struct-discriminated-unions) que é semelhante ao tipo de opção de referência.</span><span class="sxs-lookup"><span data-stu-id="99433-111">Value Option is defined as a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions) that is similar to the reference option type.</span></span> <span data-ttu-id="99433-112">Sua definição pode ser considerada desta forma:</span><span class="sxs-lookup"><span data-stu-id="99433-112">Its definition can be thought of this way:</span></span>

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

<span data-ttu-id="99433-113">Opção de valor está de acordo com a igualdade estrutural e a comparação.</span><span class="sxs-lookup"><span data-stu-id="99433-113">Value Option conforms to structural equality and comparison.</span></span> <span data-ttu-id="99433-114">A principal diferença é que o nome compilado, o nome do tipo e os nomes de caso indicam que ele é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="99433-114">The main difference is that the compiled name, type name, and case names all indicate that it is a value type.</span></span>

## <a name="using-value-options"></a><span data-ttu-id="99433-115">Usando opções de valor</span><span class="sxs-lookup"><span data-stu-id="99433-115">Using Value Options</span></span>

<span data-ttu-id="99433-116">As opções de valor são usadas apenas como [Opções](options.md).</span><span class="sxs-lookup"><span data-stu-id="99433-116">Value Options are used just like [Options](options.md).</span></span> <span data-ttu-id="99433-117">`ValueSome` é usado para indicar que um valor está presente e `ValueNone` é usado quando um valor não está presente:</span><span class="sxs-lookup"><span data-stu-id="99433-117">`ValueSome` is used to indicate that a value is present, and `ValueNone` is used when a value is not present:</span></span>

```fsharp
let tryParseDateTime (s: string) =
    match System.DateTime.TryParse(s) with
    | (true, dt) -> ValueSome dt
    | (false, _) -> ValueNone

let possibleDateString1 = "1990-12-25"
let possibleDateString2 = "This is not a date"

let result1 = tryParseDateTime possibleDateString1
let result2 = tryParseDateTime possibleDateString2

match (result1, result2) with
| ValueSome d1, ValueSome d2 -> printfn "Both are dates!"
| ValueSome d1, ValueNone -> printfn "Only the first is a date!"
| ValueNone, ValueSome d2 -> printfn "Only the second is a date!"
| ValueNone, ValueNone -> printfn "None of them are dates!"
```

<span data-ttu-id="99433-118">Assim como acontece com [Opções](options.md), a Convenção de nomenclatura para uma função que retorna `ValueOption` é prefixada com `try`.</span><span class="sxs-lookup"><span data-stu-id="99433-118">As with [Options](options.md), the naming convention for a function that returns `ValueOption` is to prefix it with `try`.</span></span>

## <a name="value-option-properties-and-methods"></a><span data-ttu-id="99433-119">Métodos e propriedades da opção de valor</span><span class="sxs-lookup"><span data-stu-id="99433-119">Value Option properties and methods</span></span>

<span data-ttu-id="99433-120">Há uma propriedade para opções de valor neste momento: `Value`.</span><span class="sxs-lookup"><span data-stu-id="99433-120">There is one property for Value Options at this time: `Value`.</span></span> <span data-ttu-id="99433-121">Um <xref:System.InvalidOperationException> será gerado se nenhum valor estiver presente quando essa propriedade for chamada.</span><span class="sxs-lookup"><span data-stu-id="99433-121">An <xref:System.InvalidOperationException> is raised if no value is present when this property is invoked.</span></span>

## <a name="value-option-functions"></a><span data-ttu-id="99433-122">Funções de opção de valor</span><span class="sxs-lookup"><span data-stu-id="99433-122">Value Option functions</span></span>

<span data-ttu-id="99433-123">Atualmente, há uma função com limite de módulo para opções de valor, `defaultValueArg`:</span><span class="sxs-lookup"><span data-stu-id="99433-123">There is currently one module-bound function for Value Options, `defaultValueArg`:</span></span>

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

<span data-ttu-id="99433-124">Assim como ocorre com a função `defaultArg`, `defaultValueArg` retorna o valor subjacente da opção de valor fornecido, se existir; caso contrário, retornará o valor padrão especificado.</span><span class="sxs-lookup"><span data-stu-id="99433-124">As with the `defaultArg` function, `defaultValueArg` returns the underlying value of the given Value Option if it exists; otherwise, it returns the specified default value.</span></span>

<span data-ttu-id="99433-125">Neste momento, não há outras funções associadas ao módulo para as opções de valor.</span><span class="sxs-lookup"><span data-stu-id="99433-125">At this time, there are no other module-bound functions for Value Options.</span></span>

## <a name="see-also"></a><span data-ttu-id="99433-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99433-126">See also</span></span>

- [<span data-ttu-id="99433-127">Opções</span><span class="sxs-lookup"><span data-stu-id="99433-127">Options</span></span>](options.md)
