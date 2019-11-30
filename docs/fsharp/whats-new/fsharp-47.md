---
title: O que há de F# novo no F# guia de 4,7
description: Obtenha uma visão geral dos novos recursos disponíveis em F# 4,7.
ms.date: 11/27/2019
ms.openlocfilehash: 203b258466cb9f1f50215ecf8884e92e7e86416b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644064"
---
# <a name="whats-new-in-f-47"></a><span data-ttu-id="60fcb-103">O que há de F# novo no 4,7</span><span class="sxs-lookup"><span data-stu-id="60fcb-103">What's new in F# 4.7</span></span>

<span data-ttu-id="60fcb-104">F#4,7 adiciona várias melhorias ao F# idioma.</span><span class="sxs-lookup"><span data-stu-id="60fcb-104">F# 4.7 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="60fcb-105">Introdução</span><span class="sxs-lookup"><span data-stu-id="60fcb-105">Get started</span></span>

<span data-ttu-id="60fcb-106">F#o 4,7 está disponível em todas as distribuições do .NET Core e ferramentas do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="60fcb-106">F# 4.7 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="60fcb-107">[Introdução F# ](../get-started/index.md) ao para saber mais.</span><span class="sxs-lookup"><span data-stu-id="60fcb-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="language-version"></a><span data-ttu-id="60fcb-108">Versão da linguagem</span><span class="sxs-lookup"><span data-stu-id="60fcb-108">Language version</span></span>

<span data-ttu-id="60fcb-109">O F# compilador 4,7 apresenta a capacidade de definir sua versão de linguagem em vigor por meio de uma propriedade no arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="60fcb-109">The F# 4.7 compiler introduces the ability to set your effective language version via a property in your project file:</span></span>

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="60fcb-110">Você pode defini-lo com os valores `4.6`, `4.7`, `latest`e `preview`.</span><span class="sxs-lookup"><span data-stu-id="60fcb-110">You can set it to the values `4.6`, `4.7`, `latest`, and `preview`.</span></span> <span data-ttu-id="60fcb-111">O padrão é `latest`.</span><span class="sxs-lookup"><span data-stu-id="60fcb-111">The default is `latest`.</span></span>

<span data-ttu-id="60fcb-112">Se você defini-lo como `preview`, o compilador ativará F# todos os recursos de visualização implementados em seu compilador.</span><span class="sxs-lookup"><span data-stu-id="60fcb-112">If you set it to `preview`, your compiler will activate all F# preview features that are implemented in your compiler.</span></span>

## <a name="implicit-yields"></a><span data-ttu-id="60fcb-113">Rendimento implícito</span><span class="sxs-lookup"><span data-stu-id="60fcb-113">Implicit yields</span></span>

<span data-ttu-id="60fcb-114">Você não precisa mais aplicar a palavra-chave `yield` em matrizes, listas, sequências ou expressões de computação em que o tipo pode ser inferido.</span><span class="sxs-lookup"><span data-stu-id="60fcb-114">You no longer need to apply the `yield` keyword in arrays, lists, sequences, or computation expressions where the type can be inferred.</span></span> <span data-ttu-id="60fcb-115">No exemplo a seguir, as duas expressões exigiam a instrução `yield` para cada entrada F# antes de 4,7:</span><span class="sxs-lookup"><span data-stu-id="60fcb-115">In the following example, both expressions required the `yield` statement for each entry prior to F# 4.7:</span></span>

```fsharp
let s = seq { 1; 2; 3; 4; 5 }

let daysOfWeek includeWeekend =
    [ 
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then 
            "Saturday"
            "Sunday"
    ] 
```

<span data-ttu-id="60fcb-116">Se você introduzir uma única palavra-chave `yield`, todos os outros itens também deverão ter `yield` aplicado a ela.</span><span class="sxs-lookup"><span data-stu-id="60fcb-116">If you introduce a single `yield` keyword, every other item must also have `yield` applied to it.</span></span>

<span data-ttu-id="60fcb-117">Os resultados implícitos não são ativados quando usados em uma expressão que também usa `yield!` para fazer algo como nivelar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="60fcb-117">Implicit yields are not activated when used in an expression that also uses `yield!` to do something like flatten a sequence.</span></span> <span data-ttu-id="60fcb-118">Você deve continuar a usar o `yield` hoje nesses casos.</span><span class="sxs-lookup"><span data-stu-id="60fcb-118">You must continue to use `yield` today in these cases.</span></span>

## <a name="wildcard-identifiers"></a><span data-ttu-id="60fcb-119">Identificadores curinga</span><span class="sxs-lookup"><span data-stu-id="60fcb-119">Wildcard identifiers</span></span>

<span data-ttu-id="60fcb-120">No F# código que envolve classes, o autoidentifier precisa sempre ser explícito em declarações de membro.</span><span class="sxs-lookup"><span data-stu-id="60fcb-120">In F# code involving classes, the self-identifier needs to always be explicit in member declarations.</span></span> <span data-ttu-id="60fcb-121">Mas, nos casos em que o autoidentificador nunca é usado, tradicionalmente, ele tem uma Convenção para usar um caractere de sublinhado duplo para indicar um autoidentificador sem nome.</span><span class="sxs-lookup"><span data-stu-id="60fcb-121">But in cases where the self-identifier is never used, it has traditionally been convention to use a double-underscore to indicate a nameless self-identifiers.</span></span> <span data-ttu-id="60fcb-122">Agora você pode usar um sublinhado simples:</span><span class="sxs-lookup"><span data-stu-id="60fcb-122">You can now use a single underscore:</span></span>

```fsharp
type C() =
    member _.M() = ()
```

<span data-ttu-id="60fcb-123">Isso também se aplica a loops de `for`:</span><span class="sxs-lookup"><span data-stu-id="60fcb-123">This also applies for `for` loops:</span></span>

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a><span data-ttu-id="60fcb-124">Reduções de recuo</span><span class="sxs-lookup"><span data-stu-id="60fcb-124">Indentation relaxations</span></span>

<span data-ttu-id="60fcb-125">Antes de F# 4,7, os requisitos de recuo para o construtor primário e os argumentos de membro estáticos exigiam recuo excessivo.</span><span class="sxs-lookup"><span data-stu-id="60fcb-125">Prior to F# 4.7, the indentation requirements for primary constructor and static member arguments required excessive indentation.</span></span> <span data-ttu-id="60fcb-126">Agora, eles só exigem um único escopo de recuo:</span><span class="sxs-lookup"><span data-stu-id="60fcb-126">They now only require a single indentation scope:</span></span>

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
