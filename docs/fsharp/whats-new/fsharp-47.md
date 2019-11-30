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
# <a name="whats-new-in-f-47"></a>O que há de F# novo no 4,7

F#4,7 adiciona várias melhorias ao F# idioma.

## <a name="get-started"></a>Introdução

F#o 4,7 está disponível em todas as distribuições do .NET Core e ferramentas do Visual Studio. [Introdução F# ](../get-started/index.md) ao para saber mais.

## <a name="language-version"></a>Versão da linguagem

O F# compilador 4,7 apresenta a capacidade de definir sua versão de linguagem em vigor por meio de uma propriedade no arquivo de projeto:

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Você pode defini-lo com os valores `4.6`, `4.7`, `latest`e `preview`. O padrão é `latest`.

Se você defini-lo como `preview`, o compilador ativará F# todos os recursos de visualização implementados em seu compilador.

## <a name="implicit-yields"></a>Rendimento implícito

Você não precisa mais aplicar a palavra-chave `yield` em matrizes, listas, sequências ou expressões de computação em que o tipo pode ser inferido. No exemplo a seguir, as duas expressões exigiam a instrução `yield` para cada entrada F# antes de 4,7:

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

Se você introduzir uma única palavra-chave `yield`, todos os outros itens também deverão ter `yield` aplicado a ela.

Os resultados implícitos não são ativados quando usados em uma expressão que também usa `yield!` para fazer algo como nivelar uma sequência. Você deve continuar a usar o `yield` hoje nesses casos.

## <a name="wildcard-identifiers"></a>Identificadores curinga

No F# código que envolve classes, o autoidentifier precisa sempre ser explícito em declarações de membro. Mas, nos casos em que o autoidentificador nunca é usado, tradicionalmente, ele tem uma Convenção para usar um caractere de sublinhado duplo para indicar um autoidentificador sem nome. Agora você pode usar um sublinhado simples:

```fsharp
type C() =
    member _.M() = ()
```

Isso também se aplica a loops de `for`:

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a>Reduções de recuo

Antes de F# 4,7, os requisitos de recuo para o construtor primário e os argumentos de membro estáticos exigiam recuo excessivo. Agora, eles só exigem um único escopo de recuo:

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
