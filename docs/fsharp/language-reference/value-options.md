---
title: 'Opções de valor (F #)'
description: 'Saiba mais sobre o tipo de opção de valor de F #, que é uma versão de estrutura do tipo de opção.'
ms.date: 06/16/2018
ms.openlocfilehash: 4c255cbbcfd9cb480230de09cd370a401c87343a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398022"
---
# <a name="value-options"></a><span data-ttu-id="0b6ee-103">Opções de valor</span><span class="sxs-lookup"><span data-stu-id="0b6ee-103">Value Options</span></span>

<span data-ttu-id="0b6ee-104">O tipo de opção de valor em F # é usado quando mantém as duas circunstâncias a seguir:</span><span class="sxs-lookup"><span data-stu-id="0b6ee-104">The Value Option type in F# is used when the following two circumstances hold:</span></span>

1. <span data-ttu-id="0b6ee-105">Um cenário é adequado para um [opção de F #](options.md).</span><span class="sxs-lookup"><span data-stu-id="0b6ee-105">A scenario is appropriate for an [F# Option](options.md).</span></span>
2. <span data-ttu-id="0b6ee-106">Usar um struct fornece um benefício de desempenho em seu cenário.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-106">Using a struct provides a performance benefit in your scenario.</span></span>

<span data-ttu-id="0b6ee-107">Nem todos os cenários sensíveis a desempenho são "resolvidos" usando structs.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-107">Not all performance-sensitive scenarios are "solved" by using structs.</span></span> <span data-ttu-id="0b6ee-108">Você deve considerar o custo adicional de cópia quando usá-los em vez de tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-108">You must consider the additional cost of copying when using them instead of reference types.</span></span> <span data-ttu-id="0b6ee-109">No entanto, grandes programas em F # geralmente instanciar muitos tipos opcionais que fluem por meio de caminhos de acesso, pois structs, às vezes, pode gerar o melhor desempenho geral ao longo do tempo de vida de um programa.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-109">However, large F# programs commonly instantiate many optional types that flow through hot paths, because structs can sometimes yield better overall performance over the lifetime of a program.</span></span>

## <a name="definition"></a><span data-ttu-id="0b6ee-110">Definição</span><span class="sxs-lookup"><span data-stu-id="0b6ee-110">Definition</span></span>

<span data-ttu-id="0b6ee-111">Opção de valor é definida como um [união discriminada de struct](discriminated-unions.md#struct-discriminated-unions) que é semelhante ao tipo de opção de referência:</span><span class="sxs-lookup"><span data-stu-id="0b6ee-111">Value Option is defined as a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions) that is similar to the reference option type:</span></span>

```fsharp
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpValueOption`1")>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone: 'T voption
    | ValueSome: 'T -> 'T voption

    member Value : 'T

and 'T voption = ValueOption<'T>
```

<span data-ttu-id="0b6ee-112">Opção de valor está em conformidade com a comparação e igualdade estrutural.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-112">Value Option conforms to structural equality and comparison.</span></span> <span data-ttu-id="0b6ee-113">A principal diferença é que o nome compilado, o nome do tipo e o casos nomes indicam que ele é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-113">The main difference is that the compiled name, type name, and case names all indicate that it is a value type.</span></span>

## <a name="using-value-options"></a><span data-ttu-id="0b6ee-114">Usando as opções de valor</span><span class="sxs-lookup"><span data-stu-id="0b6ee-114">Using Value Options</span></span>

<span data-ttu-id="0b6ee-115">Opções de valor são usadas exatamente como qualquer [opções](options.md).</span><span class="sxs-lookup"><span data-stu-id="0b6ee-115">Value Options are used just like [Options](options.md).</span></span> <span data-ttu-id="0b6ee-116">`ValueSome` é usado para indicar que um valor está presente, e `ValueNone` é usado quando um valor não está presente:</span><span class="sxs-lookup"><span data-stu-id="0b6ee-116">`ValueSome` is used to indicate that a value is present, and `ValueNone` is used when a value is not present:</span></span>

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

<span data-ttu-id="0b6ee-117">Assim como acontece com [opções](options.md), a convenção de nomenclatura para uma função que retorna `ValueOption` é um prefixo com `try`.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-117">As with [Options](options.md), the naming convention for a function that returns `ValueOption` is to prefix it with `try`.</span></span>

## <a name="value-option-properties-and-methods"></a><span data-ttu-id="0b6ee-118">Métodos e propriedades do valor de opção</span><span class="sxs-lookup"><span data-stu-id="0b6ee-118">Value Option properties and methods</span></span>

<span data-ttu-id="0b6ee-119">Há uma propriedade para opções de valor no momento: `Value`.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-119">There is one property for Value Options at this time: `Value`.</span></span> <span data-ttu-id="0b6ee-120">Um <xref:System.InvalidOperationException> será gerado se nenhum valor está presente quando essa propriedade é invocada.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-120">An <xref:System.InvalidOperationException> is raised if no value is present when this property is invoked.</span></span>

## <a name="value-option-functions"></a><span data-ttu-id="0b6ee-121">Funções com valor de opção</span><span class="sxs-lookup"><span data-stu-id="0b6ee-121">Value Option functions</span></span>

<span data-ttu-id="0b6ee-122">Atualmente, há uma função de módulo associada para opções de valor, `defaultValueArg`:</span><span class="sxs-lookup"><span data-stu-id="0b6ee-122">There is currently one module-bound function for Value Options, `defaultValueArg`:</span></span>

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T 
```

<span data-ttu-id="0b6ee-123">Assim como acontece com o `defaultArg` função, `defaultValueArg` retorna o valor subjacente da opção de valor determinado, se ela existir; caso contrário, ele retornará o valor padrão especificado.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-123">As with the `defaultArg` function, `defaultValueArg` returns the underlying value of the given Value Option if it exists; otherwise, it returns the specified default value.</span></span>

<span data-ttu-id="0b6ee-124">Neste momento, não há nenhuma outra função do módulo associado para opções de valor.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-124">At this time, there are no other module-bound functions for Value Options.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b6ee-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b6ee-125">See also</span></span>

[<span data-ttu-id="0b6ee-126">Opções</span><span class="sxs-lookup"><span data-stu-id="0b6ee-126">Options</span></span>](options.md)