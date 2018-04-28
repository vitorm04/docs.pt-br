---
title: Guia de F#
description: 'Este guia fornece uma visão geral de vários materiais de aprendizagem para F #, uma linguagem de programação funcional que é executado no .NET.'
author: jackfoxy
ms.author: phcart
ms.date: 03/19/2018
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 9c03148d42f3cf8731580e36990aa21c68f705f6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="f-guide"></a><span data-ttu-id="64452-103">Guia de F#</span><span class="sxs-lookup"><span data-stu-id="64452-103">F# Guide</span></span>

<span data-ttu-id="64452-104">F # é uma linguagem de programação funcional que é executado no .NET.</span><span class="sxs-lookup"><span data-stu-id="64452-104">F# is a functional programming language that runs on .NET.</span></span> <span data-ttu-id="64452-105">Ele também tem suporte completo para objetos, permitindo que você blend funcional e programação de objeto para soluções pragmáticas para qualquer problema.</span><span class="sxs-lookup"><span data-stu-id="64452-105">It also has full support for objects, letting you blend functional and object programming for pragmatic solutions to any problem.</span></span>

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

<span data-ttu-id="64452-106">F # é sobre a produtividade em seu núcleo.</span><span class="sxs-lookup"><span data-stu-id="64452-106">F# is about productivity at its heart.</span></span> <span data-ttu-id="64452-107">O suporte de ferramentas para F # é onipresente e completo de recursos avançados.</span><span class="sxs-lookup"><span data-stu-id="64452-107">The tooling support for F# is ubiquitous and full of advanced features.</span></span>

## <a name="learning-f"></a><span data-ttu-id="64452-108">Aprender a F #</span><span class="sxs-lookup"><span data-stu-id="64452-108">Learning F#</span></span> #

<span data-ttu-id="64452-109">[Tour do F #](tour.md) fornece uma visão geral dos recursos de idioma principal com muitos exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="64452-109">[Tour of F#](tour.md) gives an overview of major language features with lots of code samples.</span></span> <span data-ttu-id="64452-110">Isso é recomendado se você for novo para F # e deseja ter uma ideia de como funciona a linguagem.</span><span class="sxs-lookup"><span data-stu-id="64452-110">This is recommended if you are new to F# and want to get a feel for how the language works.</span></span>

<span data-ttu-id="64452-111">[Introdução à linguagem F # no Visual Studio](get-started/get-started-visual-studio.md) se você estiver no Windows e quiser que a experiência completa do Visual Studio IDE (ambiente de desenvolvimento Integraded).</span><span class="sxs-lookup"><span data-stu-id="64452-111">[Get started with F# in Visual Studio](get-started/get-started-visual-studio.md) if you're on Windows and want the full Visual Studio IDE (Integraded Development Environment) experience.</span></span>

<span data-ttu-id="64452-112">[Introdução ao F # no Visual Studio para Mac](get-started/get-started-with-visual-studio-for-mac.md) se você estiver em macOS e deseja usar um Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="64452-112">[Get started with F# in Visual Studio for Mac](get-started/get-started-with-visual-studio-for-mac.md) if you're on macOS and want to use a Visual Studio IDE.</span></span>

<span data-ttu-id="64452-113">[Introdução à linguagem F # em código do Visual Studio](get-started/get-started-vscode.md) se você deseja uma leve, entre plataformas e experiência de IDE repleto de recursos.</span><span class="sxs-lookup"><span data-stu-id="64452-113">[Get Started with F# in Visual Studio Code](get-started/get-started-vscode.md) if you want a lightweight, cross-platform, and feature-packed IDE experience.</span></span>

<span data-ttu-id="64452-114">[Introdução à linguagem F # com o .NET Core CLI](get-started/get-started-command-line.md) se você quiser usar as ferramentas de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="64452-114">[Get started with F# with the .NET Core CLI](get-started/get-started-command-line.md) if you want to use command-line tools.</span></span>

<span data-ttu-id="64452-115">[Introdução à linguagem F # e Xamarin](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/) para programação móvel com F #.</span><span class="sxs-lookup"><span data-stu-id="64452-115">[Get started with F# and Xamarin](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/) for mobile programming with F#.</span></span>

## <a name="references"></a><span data-ttu-id="64452-116">Referências</span><span class="sxs-lookup"><span data-stu-id="64452-116">References</span></span>

<span data-ttu-id="64452-117">[Referência da linguagem F #](language-reference/index.md) é a referência oficial e abrangente para todos os recursos da linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="64452-117">[F# Language Reference](language-reference/index.md) is the official, comprehensive reference for all F# language features.</span></span> <span data-ttu-id="64452-118">Cada artigo explica a sintaxe e mostra exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="64452-118">Each article explains the syntax and shows code samples.</span></span> <span data-ttu-id="64452-119">Você pode usar a barra de filtro na tabela de conteúdo para localizar artigos específicos.</span><span class="sxs-lookup"><span data-stu-id="64452-119">You can use the filter bar in the table of contents to find specific articles.</span></span>

<span data-ttu-id="64452-120">[Referência da biblioteca principal F #](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) é a referência de API para a biblioteca principal F #.</span><span class="sxs-lookup"><span data-stu-id="64452-120">[F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) is the API reference for the F# Core Library.</span></span>


## <a name="additional-guides"></a><span data-ttu-id="64452-121">Guias adicionais</span><span class="sxs-lookup"><span data-stu-id="64452-121">Additional guides</span></span>

<span data-ttu-id="64452-122">[F # para diversão e lucro](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) é um catálogo abrangente e muito detalhado no aprendizado do F #.</span><span class="sxs-lookup"><span data-stu-id="64452-122">[F# for Fun and Profit](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) is a comprehensive and very detailed book on learning F#.</span></span> <span data-ttu-id="64452-123">Seu conteúdo e autor são queridos pela comunidade do F #.</span><span class="sxs-lookup"><span data-stu-id="64452-123">Its contents and author are beloved by the F# community.</span></span> <span data-ttu-id="64452-124">O público-alvo é principalmente os desenvolvedores com um plano de fundo de programação orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="64452-124">The target audience is primarily developers with an object oriented programming background.</span></span>

<span data-ttu-id="64452-125">[Wikibook programação F #](https://en.wikibooks.org/wiki/F_Sharp_Programming) é um wikibook sobre como aprender F #.</span><span class="sxs-lookup"><span data-stu-id="64452-125">[F# Programming Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming) is a wikibook about learning F#.</span></span> <span data-ttu-id="64452-126">Também é um produto da comunidade do F #.</span><span class="sxs-lookup"><span data-stu-id="64452-126">It is also a product of the F# community.</span></span> <span data-ttu-id="64452-127">O público-alvo são pessoas que são novas para F #, com um pouco de programação orientada a objeto de plano de fundo.</span><span class="sxs-lookup"><span data-stu-id="64452-127">The target audience is people who are new to F#, with a little bit of object oriented programming background.</span></span>

## <a name="learn-f-through-videos"></a><span data-ttu-id="64452-128">Aprender a F # por meio de vídeos</span><span class="sxs-lookup"><span data-stu-id="64452-128">Learn F# through videos</span></span>

<span data-ttu-id="64452-129">[F # tutorial no YouTube](https://www.youtube.com/watch?v=c7eNDJN758U) é uma ótima introdução para F # usando o Visual Studio, mostrando vários exemplos grandes durante o curso de 1,5 horas.</span><span class="sxs-lookup"><span data-stu-id="64452-129">[F# tutorial on YouTube](https://www.youtube.com/watch?v=c7eNDJN758U) is a great introduction to F# using Visual Studio, showing lots of great examples over the course of 1.5 hours.</span></span> <span data-ttu-id="64452-130">O público-alvo é que os desenvolvedores do Visual Studio que são novos para F #.</span><span class="sxs-lookup"><span data-stu-id="64452-130">The target audience is Visual Studio developers who are new to F#.</span></span>

<span data-ttu-id="64452-131">[Introdução à programação com F #](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) é uma série de vídeo grande que usa o código do Visual Studio como o editor principal.</span><span class="sxs-lookup"><span data-stu-id="64452-131">[Introduction to Programming with F#](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) is a great video series that uses Visual Studio Code as the main editor.</span></span> <span data-ttu-id="64452-132">A série de vídeo começa em nada e termina com a criação de um jogo de vídeo de RPG baseado em texto.</span><span class="sxs-lookup"><span data-stu-id="64452-132">The video series starts from nothing and ends with building a text-based RPG video game.</span></span> <span data-ttu-id="64452-133">O público-alvo é que os desenvolvedores que preferem código do Visual Studio (ou um IDE leve) e são novos para F #.</span><span class="sxs-lookup"><span data-stu-id="64452-133">The target audience is developers who prefer Visual Studio Code (or a lightweight IDE) and are new to F#.</span></span>

<span data-ttu-id="64452-134">[O que há de novo no Visual Studio de 2017 para F # para desenvolvedores](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) um curso de vídeo que mostra alguns dos recursos mais recentes para F # em 2017 do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="64452-134">[What's New in Visual Studio 2017 for F# For Developers](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) is a video course that shows some of the newer features for F# in Visual Studio 2017.</span></span> <span data-ttu-id="64452-135">O público-alvo é que os desenvolvedores do Visual Studio que são novos para F #.</span><span class="sxs-lookup"><span data-stu-id="64452-135">The target audience is Visual Studio developers who are new to F#.</span></span>

## <a name="other-useful-resources"></a><span data-ttu-id="64452-136">Outros recursos úteis</span><span class="sxs-lookup"><span data-stu-id="64452-136">Other useful resources</span></span>

<span data-ttu-id="64452-137">O [site de trechos de código F #](http://www.fssnip.net) contém um conjunto grande de trechos de código mostrando como fazer qualquer coisa no F #, variando de iniciantes a trechos de código altamente avançados.</span><span class="sxs-lookup"><span data-stu-id="64452-137">The [F# Snippets Website](http://www.fssnip.net) contains a massive set of code snippets showing how to do just about anything in F#, ranging from absolute beginner to highly advanced snippets.</span></span>

<span data-ttu-id="64452-138">O [F # Software Foundation atraso](http://fsharp.org/guides/slack/) é um ótimo lugar para iniciantes e especialistas da mesma forma, é altamente ativos, e tem algumas melhores F # programadores do mundo disponíveis para um bate-papo.</span><span class="sxs-lookup"><span data-stu-id="64452-138">The [F# Software Foundation Slack](http://fsharp.org/guides/slack/) is a great place for beginners and experts alike, is highly active, and has some of world's best F# programmers available for a chat.</span></span> <span data-ttu-id="64452-139">É altamente recomendável ingressar.</span><span class="sxs-lookup"><span data-stu-id="64452-139">We highly recommend joining.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="64452-140">O F# Software Foundation</span><span class="sxs-lookup"><span data-stu-id="64452-140">The F# Software Foundation</span></span>

<span data-ttu-id="64452-141">Embora a Microsoft é o principal do desenvolvedor da linguagem F # e suas ferramentas no Visual Studio, F # é também o apoio de uma base independente, o F # Software Foundation (FSSF).</span><span class="sxs-lookup"><span data-stu-id="64452-141">Although Microsoft is the primary developer of the F# language and its tools in Visual Studio, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="64452-142">A missão do F# Software Foundation é promover, proteger e evoluir a linguagem de programação F#, além de dar suporte e facilitar o crescimento de uma comunidade internacional e diversa de programadores em F#.</span><span class="sxs-lookup"><span data-stu-id="64452-142">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="64452-143">Para saber mais e se envolver, confira [fsharp.org](http://fsharp.org). A junção é gratuita e a rede de desenvolvedores do F # no foundation é algo que você não deseja perder!</span><span class="sxs-lookup"><span data-stu-id="64452-143">To learn more and get involved, check out [fsharp.org](http://fsharp.org). It's free to join, and the network of F# developers in the foundation is something you don't want to miss out on!</span></span>
