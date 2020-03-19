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
# <a name="whats-new-in-f-47"></a>O que há de novo em F# 4.7

F# 4.7 adiciona várias melhorias ao idioma F#.

## <a name="get-started"></a>Introdução

F# 4.7 está disponível em todas as distribuições .NET Core e ferramentas do Visual Studio. [Comece com F#](../get-started/index.md) para aprender mais.

## <a name="language-version"></a>Versão da linguagem

O compilador F# 4.7 introduz a capacidade de definir sua versão de idioma eficaz através de uma propriedade no arquivo do projeto:

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Você pode defini-lo `4.6` `4.7`para `latest`os `preview`valores, e . O padrão é `latest`.

Se você configurá-lo para `preview`, seu compilador ativará todos os recursos de visualização F# que são implementados em seu compilador.

## <a name="implicit-yields"></a>Rendimentos implícitos

Você não precisa mais `yield` aplicar a palavra-chave em matrizes, listas, seqüências ou expressões de computação onde o tipo pode ser inferido. No exemplo a seguir, ambas `yield` as expressões exigiram a declaração para cada entrada antes do F# 4.7:

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

Se você introduzir `yield` uma única palavra-chave, `yield` todos os outros itens também devem ter aplicado a ela.

Os rendimentos implícitos não são ativados quando usados em uma expressão que também usa `yield!` para fazer algo como achatar uma seqüência. Você deve continuar `yield` a usar hoje nestes casos.

## <a name="wildcard-identifiers"></a>Identificadores curinga

No código F# envolvendo classes, o auto-identificador precisa ser sempre explícito nas declarações dos membros. Mas nos casos em que o auto-identificador nunca é usado, tradicionalmente tem sido convenção usar um sublinhado duplo para indicar um auto-identificador sem nome. Agora você pode usar um único sublinhado:

```fsharp
type C() =
    member _.M() = ()
```

Isso também se `for` aplica a loops:

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a>Relaxamentos de recuo

Antes do F# 4.7, os requisitos de recuo para argumentos de membros primários e estáticos exigiam recuo excessivo. Eles agora exigem apenas um único escopo de recuo:

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
