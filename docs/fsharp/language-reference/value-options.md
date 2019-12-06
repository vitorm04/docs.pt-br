---
title: Opções de valores
description: Saiba mais sobre F# o tipo de opção de valor, que é uma versão de struct do tipo de opção.
ms.date: 12/04/2019
ms.openlocfilehash: 0e9882ab4acdf2757705ef6022516d3572d87ef2
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837110"
---
# <a name="value-options"></a><span data-ttu-id="971d3-103">Opções de valores</span><span class="sxs-lookup"><span data-stu-id="971d3-103">Value Options</span></span>

<span data-ttu-id="971d3-104">O tipo de opção de F# valor em é usado quando as duas circunstâncias a seguir têm:</span><span class="sxs-lookup"><span data-stu-id="971d3-104">The Value Option type in F# is used when the following two circumstances hold:</span></span>

1. <span data-ttu-id="971d3-105">Um cenário é apropriado para uma [ F# opção](options.md).</span><span class="sxs-lookup"><span data-stu-id="971d3-105">A scenario is appropriate for an [F# Option](options.md).</span></span>
2. <span data-ttu-id="971d3-106">O uso de uma estrutura fornece um benefício de desempenho em seu cenário.</span><span class="sxs-lookup"><span data-stu-id="971d3-106">Using a struct provides a performance benefit in your scenario.</span></span>

<span data-ttu-id="971d3-107">Nem todos os cenários sensíveis ao desempenho são "resolvidos" usando structs.</span><span class="sxs-lookup"><span data-stu-id="971d3-107">Not all performance-sensitive scenarios are "solved" by using structs.</span></span> <span data-ttu-id="971d3-108">Você deve considerar o custo adicional de copiar ao usá-los em vez de tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="971d3-108">You must consider the additional cost of copying when using them instead of reference types.</span></span> <span data-ttu-id="971d3-109">No entanto F# , programas grandes normalmente instanciam muitos tipos opcionais que fluem por meio de caminhos ativos e, nesses casos, as estruturas geralmente podem produzir melhor desempenho geral durante o tempo de vida de um programa.</span><span class="sxs-lookup"><span data-stu-id="971d3-109">However, large F# programs commonly instantiate many optional types that flow through hot paths, and in such cases, structs can often yield better overall performance over the lifetime of a program.</span></span>

## <a name="definition"></a><span data-ttu-id="971d3-110">Definição</span><span class="sxs-lookup"><span data-stu-id="971d3-110">Definition</span></span>

<span data-ttu-id="971d3-111">A opção Value é definida como uma [união discriminada de struct](discriminated-unions.md#struct-discriminated-unions) que é semelhante ao tipo de opção de referência.</span><span class="sxs-lookup"><span data-stu-id="971d3-111">Value Option is defined as a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions) that is similar to the reference option type.</span></span> <span data-ttu-id="971d3-112">Sua definição pode ser considerada desta forma:</span><span class="sxs-lookup"><span data-stu-id="971d3-112">Its definition can be thought of this way:</span></span>

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

<span data-ttu-id="971d3-113">Opção de valor está de acordo com a igualdade estrutural e a comparação.</span><span class="sxs-lookup"><span data-stu-id="971d3-113">Value Option conforms to structural equality and comparison.</span></span> <span data-ttu-id="971d3-114">A principal diferença é que o nome compilado, o nome do tipo e os nomes de caso indicam que ele é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="971d3-114">The main difference is that the compiled name, type name, and case names all indicate that it is a value type.</span></span>

## <a name="using-value-options"></a><span data-ttu-id="971d3-115">Usando opções de valor</span><span class="sxs-lookup"><span data-stu-id="971d3-115">Using Value Options</span></span>

<span data-ttu-id="971d3-116">As opções de valor são usadas apenas como [Opções](options.md).</span><span class="sxs-lookup"><span data-stu-id="971d3-116">Value Options are used just like [Options](options.md).</span></span> <span data-ttu-id="971d3-117">`ValueSome` é usado para indicar que um valor está presente e `ValueNone` é usado quando um valor não está presente:</span><span class="sxs-lookup"><span data-stu-id="971d3-117">`ValueSome` is used to indicate that a value is present, and `ValueNone` is used when a value is not present:</span></span>

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

<span data-ttu-id="971d3-118">Assim como acontece com [Opções](options.md), a Convenção de nomenclatura para uma função que retorna `ValueOption` é prefixada com `try`.</span><span class="sxs-lookup"><span data-stu-id="971d3-118">As with [Options](options.md), the naming convention for a function that returns `ValueOption` is to prefix it with `try`.</span></span>

## <a name="value-option-properties-and-methods"></a><span data-ttu-id="971d3-119">Métodos e propriedades da opção de valor</span><span class="sxs-lookup"><span data-stu-id="971d3-119">Value Option properties and methods</span></span>

<span data-ttu-id="971d3-120">Há uma propriedade para opções de valor neste momento: `Value`.</span><span class="sxs-lookup"><span data-stu-id="971d3-120">There is one property for Value Options at this time: `Value`.</span></span> <span data-ttu-id="971d3-121">Um <xref:System.InvalidOperationException> será gerado se nenhum valor estiver presente quando essa propriedade for chamada.</span><span class="sxs-lookup"><span data-stu-id="971d3-121">An <xref:System.InvalidOperationException> is raised if no value is present when this property is invoked.</span></span>

## <a name="value-option-functions"></a><span data-ttu-id="971d3-122">Funções de opção de valor</span><span class="sxs-lookup"><span data-stu-id="971d3-122">Value Option functions</span></span>

<span data-ttu-id="971d3-123">O módulo `ValueOption` no FSharp. Core contém funcionalidade equivalente ao módulo `Option`.</span><span class="sxs-lookup"><span data-stu-id="971d3-123">The `ValueOption` module in FSharp.Core contains equivalent functionality to the `Option` module.</span></span> <span data-ttu-id="971d3-124">Há algumas diferenças no nome, como `defaultValueArg`:</span><span class="sxs-lookup"><span data-stu-id="971d3-124">There are a few differences in name, such as `defaultValueArg`:</span></span>

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

<span data-ttu-id="971d3-125">Isso funciona exatamente como `defaultArg` no módulo `Option`, mas opera em uma opção de valor em vez disso.</span><span class="sxs-lookup"><span data-stu-id="971d3-125">This acts just like `defaultArg` in the `Option` module, but operates on a Value Option instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="971d3-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="971d3-126">See also</span></span>

- [<span data-ttu-id="971d3-127">Opções</span><span class="sxs-lookup"><span data-stu-id="971d3-127">Options</span></span>](options.md)
