---
title: Guia de F#
description: 'Este guia fornece uma visão geral de vários materiais de aprendizagem para F #, uma linguagem de programação funcional que é executado no .NET.'
author: jackfoxy
ms.date: 03/19/2018
ms.openlocfilehash: cb829e904c006467e1470752b4fe8757ca694b05
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2018
ms.locfileid: "34311995"
---
# <a name="f-guide"></a>Guia de F#

F # é uma linguagem de programação funcional que é executado no .NET. Ele também tem suporte completo para objetos, permitindo que você blend funcional e programação de objeto para soluções pragmáticas para qualquer problema.

```fsharp
open System // Get access to functionality in System namespace.

// Function: takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

// Use the EntryPoint attribute to run the program.
[<EntryPoint>]
let main args =
    // Define a list of names
    let names = [| "Don"; "Julia"; "Xi" |]
    
    // Print a fun greeting for each name!
    names
    |> Array.map getGreeting
    |> Array.iter (fun greeting -> printfn "%s" greeting)

    0
```

F # é sobre a produtividade em seu núcleo. O suporte de ferramentas para F # é onipresente e completo de recursos avançados.

## <a name="learning-f"></a>Aprender a F # #

[Tour do F #](tour.md) fornece uma visão geral dos recursos de idioma principal com muitos exemplos de código. Isso é recomendado se você for novo para F # e deseja ter uma ideia de como funciona a linguagem.

[Introdução à linguagem F # no Visual Studio](get-started/get-started-visual-studio.md) se você estiver no Windows e quiser que a experiência completa do Visual Studio IDE (ambiente de desenvolvimento Integraded).

[Introdução ao F # no Visual Studio para Mac](get-started/get-started-with-visual-studio-for-mac.md) se você estiver em macOS e deseja usar um Visual Studio IDE.

[Introdução à linguagem F # em código do Visual Studio](get-started/get-started-vscode.md) se você deseja uma leve, entre plataformas e experiência de IDE repleto de recursos.

[Introdução à linguagem F # com o .NET Core CLI](get-started/get-started-command-line.md) se você quiser usar as ferramentas de linha de comando.

[Introdução à linguagem F # e Xamarin](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/) para programação móvel com F #.

[F # para blocos de anotações do Azure](https://notebooks.azure.com/Microsoft/libraries/samples/html/FSharp%20for%20Azure%20Notebooks.ipynb) é um tutorial para aprender a F # em um Jupyter Notebook livre, hospedado.

## <a name="references"></a>Referências

[Referência da linguagem F #](language-reference/index.md) é a referência oficial e abrangente para todos os recursos da linguagem F #. Cada artigo explica a sintaxe e mostra exemplos de código. Você pode usar a barra de filtro na tabela de conteúdo para localizar artigos específicos.

[Referência da biblioteca principal F #](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) é a referência de API para a biblioteca principal F #.


## <a name="additional-guides"></a>Guias adicionais

[F # para diversão e lucro](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) é um catálogo abrangente e muito detalhado no aprendizado do F #. Seu conteúdo e autor são queridos pela comunidade do F #. O público-alvo é principalmente os desenvolvedores com um plano de fundo de programação orientada a objeto.

[Wikibook programação F #](https://en.wikibooks.org/wiki/F_Sharp_Programming) é um wikibook sobre como aprender F #. Também é um produto da comunidade do F #. O público-alvo são pessoas que são novas para F #, com um pouco de programação orientada a objeto de plano de fundo.

## <a name="learn-f-through-videos"></a>Aprender a F # por meio de vídeos

[F # tutorial no YouTube](https://www.youtube.com/watch?v=c7eNDJN758U) é uma ótima introdução para F # usando o Visual Studio, mostrando vários exemplos grandes durante o curso de 1,5 horas. O público-alvo é que os desenvolvedores do Visual Studio que são novos para F #.

[Introdução à programação com F #](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) é uma série de vídeo grande que usa o código do Visual Studio como o editor principal. A série de vídeo começa em nada e termina com a criação de um jogo de vídeo de RPG baseado em texto. O público-alvo é que os desenvolvedores que preferem código do Visual Studio (ou um IDE leve) e são novos para F #.

[O que há de novo no Visual Studio de 2017 para F # para desenvolvedores](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) um curso de vídeo que mostra alguns dos recursos mais recentes para F # em 2017 do Visual Studio. O público-alvo é que os desenvolvedores do Visual Studio que são novos para F #.

## <a name="other-useful-resources"></a>Outros recursos úteis

O [site de trechos de código F #](http://www.fssnip.net) contém um conjunto grande de trechos de código mostrando como fazer qualquer coisa no F #, variando de iniciantes a trechos de código altamente avançados.

O [F # Software Foundation atraso](http://fsharp.org/guides/slack/) é um ótimo lugar para iniciantes e especialistas da mesma forma, é altamente ativos, e tem algumas melhores F # programadores do mundo disponíveis para um bate-papo. É altamente recomendável ingressar.

## <a name="the-f-software-foundation"></a>O F# Software Foundation

Embora a Microsoft é o principal do desenvolvedor da linguagem F # e suas ferramentas no Visual Studio, F # é também o apoio de uma base independente, o F # Software Foundation (FSSF).

A missão do F# Software Foundation é promover, proteger e evoluir a linguagem de programação F#, além de dar suporte e facilitar o crescimento de uma comunidade internacional e diversa de programadores em F#.

Para saber mais e se envolver, confira [fsharp.org](http://fsharp.org). A junção é gratuita e a rede de desenvolvedores do F # no foundation é algo que você não deseja perder!
