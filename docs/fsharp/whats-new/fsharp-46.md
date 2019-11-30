---
title: O que há de F# novo no F# guia de 4,6
description: Obtenha uma visão geral dos novos recursos disponíveis em F# 4,6.
ms.date: 11/27/2019
ms.openlocfilehash: 81d3e988d044cb16f8ec079118fd0ede2dabc587
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644078"
---
# <a name="whats-new-in-f-46"></a>O que há de F# novo no 4,6

F#4,6 adiciona várias melhorias ao F# idioma.

## <a name="get-started"></a>Introdução

F#o 4,6 está disponível em todas as distribuições do .NET Core e ferramentas do Visual Studio. [Introdução F# ](../get-started/index.md) ao para saber mais.

## <a name="anonymous-records"></a>Registros anônimos

Os [registros anônimos](../language-reference/anonymous-records.md) são um novo F# tipo apresentado em F# 4,6. Eles são agregações simples de valores nomeados que não precisam ser declarados antes do uso. Você pode declará-los como structs ou tipos de referência. Eles são tipos de referência por padrão.

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

Eles também podem ser declarados como structs para quando você deseja agrupar tipos de valor e estão operando em cenários sensíveis ao desempenho:

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    struct {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

Elas são muito poderosas e podem ser usadas em vários cenários. Saiba mais em [registros anônimos](../language-reference/anonymous-records.md).

## <a name="valueoption-functions"></a>Funções ValueOption

O tipo ValueOption adicionado em F# 4,5 agora tem "paridade de função associada a módulo" com o tipo de opção. Alguns dos exemplos mais comumente usados são os seguintes:

```fsharp
// Multiply a value option by 2 if it has  value
let xOpt = ValueSome 99
let result = xOpt |> ValueOption.map (fun v -> v * 2)

// Reverse a string if it exists
let strOpt = ValueSome "Mirror image"
let reverse (str: string) =
    match str with
    | null
    | "" -> None
    | s ->
        str.ToCharArray()
        |> Array.rev
        |> string
        |> Some

let reversedString = strOpt |> Option.bind reverse
```

Isso permite que o ValueOption seja usado exatamente como a opção em cenários em que um tipo de valor melhora o desempenho.
