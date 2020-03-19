---
title: O que há de novo em F# 4.7 - F# Guide
description: Obtenha uma visão geral dos novos recursos disponíveis em F# 4.7.
ms.date: 11/27/2019
ms.openlocfilehash: 7a6e744a398719bcb55d168dd700459e0b122dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185872"
---
# <a name="whats-new-in-f-47"></a><span data-ttu-id="ae0cb-103">O que há de novo em F# 4.7</span><span class="sxs-lookup"><span data-stu-id="ae0cb-103">What's new in F# 4.7</span></span>

<span data-ttu-id="ae0cb-104">F# 4.7 adiciona várias melhorias ao idioma F#.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-104">F# 4.7 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="ae0cb-105">Introdução</span><span class="sxs-lookup"><span data-stu-id="ae0cb-105">Get started</span></span>

<span data-ttu-id="ae0cb-106">F# 4.7 está disponível em todas as distribuições .NET Core e ferramentas do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-106">F# 4.7 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="ae0cb-107">[Comece com F#](../get-started/index.md) para aprender mais.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="language-version"></a><span data-ttu-id="ae0cb-108">Versão da linguagem</span><span class="sxs-lookup"><span data-stu-id="ae0cb-108">Language version</span></span>

<span data-ttu-id="ae0cb-109">O compilador F# 4.7 introduz a capacidade de definir sua versão de idioma eficaz através de uma propriedade no arquivo do projeto:</span><span class="sxs-lookup"><span data-stu-id="ae0cb-109">The F# 4.7 compiler introduces the ability to set your effective language version via a property in your project file:</span></span>

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="ae0cb-110">Você pode defini-lo `4.6` `4.7`para `latest`os `preview`valores, e .</span><span class="sxs-lookup"><span data-stu-id="ae0cb-110">You can set it to the values `4.6`, `4.7`, `latest`, and `preview`.</span></span> <span data-ttu-id="ae0cb-111">O padrão é `latest`.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-111">The default is `latest`.</span></span>

<span data-ttu-id="ae0cb-112">Se você configurá-lo para `preview`, seu compilador ativará todos os recursos de visualização F# que são implementados em seu compilador.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-112">If you set it to `preview`, your compiler will activate all F# preview features that are implemented in your compiler.</span></span>

## <a name="implicit-yields"></a><span data-ttu-id="ae0cb-113">Rendimentos implícitos</span><span class="sxs-lookup"><span data-stu-id="ae0cb-113">Implicit yields</span></span>

<span data-ttu-id="ae0cb-114">Você não precisa mais `yield` aplicar a palavra-chave em matrizes, listas, seqüências ou expressões de computação onde o tipo pode ser inferido.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-114">You no longer need to apply the `yield` keyword in arrays, lists, sequences, or computation expressions where the type can be inferred.</span></span> <span data-ttu-id="ae0cb-115">No exemplo a seguir, ambas `yield` as expressões exigiram a declaração para cada entrada antes do F# 4.7:</span><span class="sxs-lookup"><span data-stu-id="ae0cb-115">In the following example, both expressions required the `yield` statement for each entry prior to F# 4.7:</span></span>

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

<span data-ttu-id="ae0cb-116">Se você introduzir `yield` uma única palavra-chave, `yield` todos os outros itens também devem ter aplicado a ela.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-116">If you introduce a single `yield` keyword, every other item must also have `yield` applied to it.</span></span>

<span data-ttu-id="ae0cb-117">Os rendimentos implícitos não são ativados quando usados em uma expressão que também usa `yield!` para fazer algo como achatar uma seqüência.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-117">Implicit yields are not activated when used in an expression that also uses `yield!` to do something like flatten a sequence.</span></span> <span data-ttu-id="ae0cb-118">Você deve continuar `yield` a usar hoje nestes casos.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-118">You must continue to use `yield` today in these cases.</span></span>

## <a name="wildcard-identifiers"></a><span data-ttu-id="ae0cb-119">Identificadores curinga</span><span class="sxs-lookup"><span data-stu-id="ae0cb-119">Wildcard identifiers</span></span>

<span data-ttu-id="ae0cb-120">No código F# envolvendo classes, o auto-identificador precisa ser sempre explícito nas declarações dos membros.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-120">In F# code involving classes, the self-identifier needs to always be explicit in member declarations.</span></span> <span data-ttu-id="ae0cb-121">Mas nos casos em que o auto-identificador nunca é usado, tradicionalmente tem sido convenção usar um sublinhado duplo para indicar um auto-identificador sem nome.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-121">But in cases where the self-identifier is never used, it has traditionally been convention to use a double-underscore to indicate a nameless self-identifiers.</span></span> <span data-ttu-id="ae0cb-122">Agora você pode usar um único sublinhado:</span><span class="sxs-lookup"><span data-stu-id="ae0cb-122">You can now use a single underscore:</span></span>

```fsharp
type C() =
    member _.M() = ()
```

<span data-ttu-id="ae0cb-123">Isso também se `for` aplica a loops:</span><span class="sxs-lookup"><span data-stu-id="ae0cb-123">This also applies for `for` loops:</span></span>

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a><span data-ttu-id="ae0cb-124">Relaxamentos de recuo</span><span class="sxs-lookup"><span data-stu-id="ae0cb-124">Indentation relaxations</span></span>

<span data-ttu-id="ae0cb-125">Antes do F# 4.7, os requisitos de recuo para argumentos de membros primários e estáticos exigiam recuo excessivo.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-125">Prior to F# 4.7, the indentation requirements for primary constructor and static member arguments required excessive indentation.</span></span> <span data-ttu-id="ae0cb-126">Eles agora exigem apenas um único escopo de recuo:</span><span class="sxs-lookup"><span data-stu-id="ae0cb-126">They now only require a single indentation scope:</span></span>

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
