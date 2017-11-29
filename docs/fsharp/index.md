---
title: Guia de F#
description: "Saiba mais sobre F # linguagem de programação, uma linguagem de código-fonte aberto para .NET que fornece suporte de primeira classe para programação funcional."
keywords: .NET, .NET Core
author: jackfoxy
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: 4ddd77cef6cf70a63f1af81359d82eda27a01593
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="f-guide"></a><span data-ttu-id="2145d-104">Guia de F#</span><span class="sxs-lookup"><span data-stu-id="2145d-104">F# Guide</span></span>

<span data-ttu-id="2145d-105">F# é uma linguagem de programação de plataforma cruzada e software livre para .NET que fornece suporte de primeiro nível para programação funcional, juntamente com o suporte à programação imperativa e orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="2145d-105">F# is a cross-platform, open source programming language for .NET which provides first-class support for functional programming, along with support of object-oriented and imperative programming.</span></span>  <span data-ttu-id="2145d-106">O compilador e as ferramentas para Visual F # são implementação e ferramentas da Microsoft para a linguagem de programação F#, tornando F# um membro de primeira classe do .NET.</span><span class="sxs-lookup"><span data-stu-id="2145d-106">The Visual F# compiler and tooling are Microsoft's implementation and tooling for the F# programming language, making F# a first-class member of .NET.</span></span>

## <a name="if-youre-new-to-f"></a><span data-ttu-id="2145d-107">Se você for novo no F #</span><span class="sxs-lookup"><span data-stu-id="2145d-107">If You're New to F#</span></span> #

<span data-ttu-id="2145d-108">Se você for novo no F #, comece com o [Tour do F #](tour.md) para obter uma visão geral do idioma.</span><span class="sxs-lookup"><span data-stu-id="2145d-108">If you're new to F#, begin with the [Tour of F#](tour.md) to get an overview of the language.</span></span>

<span data-ttu-id="2145d-109">Também é recomendável que você percorrer o [funciona como valores de primeira classe](introduction-to-functional-programming/functions-as-first-class-values.md) <!--[Introduction to Functional Progamming](introduction-to-functional-programming/index.md)--> para aprender os conceitos de programação funcional que são essenciais para trabalhar com F #.</span><span class="sxs-lookup"><span data-stu-id="2145d-109">It's also recommended that you go through the [Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Progamming](introduction-to-functional-programming/index.md)--> to learn Functional Programming concepts which are essential to working with F#.</span></span>

<span data-ttu-id="2145d-110">Os [Tutoriais](tutorials/getting-started/index.md) também contêm guias passo a passo para vários níveis de habilidade e recursos da linguagem.</span><span class="sxs-lookup"><span data-stu-id="2145d-110">The [Tutorials](tutorials/getting-started/index.md) also have step-by-step guides for various skill levels and features of the language.</span></span>

## <a name="if-youre-experienced-with-f"></a><span data-ttu-id="2145d-111">Se você tiver experiência com F #</span><span class="sxs-lookup"><span data-stu-id="2145d-111">If You're Experienced with F#</span></span> #

<span data-ttu-id="2145d-112">Se você conhecer o F#, a [Referência de linguagem](language-reference/index.md) será bastante útil, pois documenta completamente todos os aspectos da linguagem, complementados por inúmeros exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="2145d-112">If you know your way around F#, you'll find a lot of use in the [Language Reference](language-reference/index.md), which documents each aspect of the language thoroughly, supplemented by numerous code samples.</span></span>  <span data-ttu-id="2145d-113">A [Referência da biblioteca do F# Core](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) também será bastante útil.</span><span class="sxs-lookup"><span data-stu-id="2145d-113">You'll also find a lot of use in the [F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference).</span></span>  <span data-ttu-id="2145d-114">A referência da biblioteca principal F # eventualmente será movido para o MSDN e nesses documentos atuais.</span><span class="sxs-lookup"><span data-stu-id="2145d-114">The F# Core Library Reference will eventually move away from MSDN and into these current docs.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="2145d-115">O F# Software Foundation</span><span class="sxs-lookup"><span data-stu-id="2145d-115">The F# Software Foundation</span></span>

<span data-ttu-id="2145d-116">Embora a Microsoft seja o desenvolvedor principal da linguagem F# e das ferramentas Visual F#, F# também recebe suporte de uma base independente, a F# Software Foundation (FSSF).</span><span class="sxs-lookup"><span data-stu-id="2145d-116">Although Microsoft is the primary developer of the F# language and Visual F# Tooling, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="2145d-117">A missão do F# Software Foundation é promover, proteger e evoluir a linguagem de programação F#, além de dar suporte e facilitar o crescimento de uma comunidade internacional e diversa de programadores em F#.</span><span class="sxs-lookup"><span data-stu-id="2145d-117">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="2145d-118">Para saber mais e se envolver, confira [fsharp.org](http://fsharp.org).</span><span class="sxs-lookup"><span data-stu-id="2145d-118">To learn more and get involved, check out [fsharp.org](http://fsharp.org).</span></span>

## <a name="documentation"></a><span data-ttu-id="2145d-119">Documentação</span><span class="sxs-lookup"><span data-stu-id="2145d-119">Documentation</span></span>

* [<span data-ttu-id="2145d-120">Tutoriais</span><span class="sxs-lookup"><span data-stu-id="2145d-120">Tutorials</span></span>](tutorials/getting-started/index.md)
* <span data-ttu-id="2145d-121">[Funções como valores de primeira classe](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span><span class="sxs-lookup"><span data-stu-id="2145d-121">[Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span></span>
* [<span data-ttu-id="2145d-122">Referência de Linguagem</span><span class="sxs-lookup"><span data-stu-id="2145d-122">Language Reference</span></span>](language-reference/index.md)
* [<span data-ttu-id="2145d-123">Referência da biblioteca de F# Core</span><span class="sxs-lookup"><span data-stu-id="2145d-123">F# Core Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)

## <a name="online-reading-resources"></a><span data-ttu-id="2145d-124">Recursos online para leitura</span><span class="sxs-lookup"><span data-stu-id="2145d-124">Online Reading Resources</span></span>

* [<span data-ttu-id="2145d-125">F# for Fun and Profit Gitbook (Gitbook: F# por diversão e lucro)</span><span class="sxs-lookup"><span data-stu-id="2145d-125">F# for Fun and Profit Gitbook</span></span>](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) 
* [<span data-ttu-id="2145d-126">Wikibook sobre programação em F#</span><span class="sxs-lookup"><span data-stu-id="2145d-126">F# Programming Wikibook</span></span>](https://en.wikibooks.org/wiki/F_Sharp_Programming)

## <a name="video-learning-resources"></a><span data-ttu-id="2145d-127">Recursos de aprendizagem em vídeo</span><span class="sxs-lookup"><span data-stu-id="2145d-127">Video Learning Resources</span></span>

* [<span data-ttu-id="2145d-128">Série de Introdução à programação em F# no YouTube</span><span class="sxs-lookup"><span data-stu-id="2145d-128">Introduction to Programming with F# series on YouTube</span></span>](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)
* [<span data-ttu-id="2145d-129">Introduction to F# series on FSharpTV (Série Introdução ao F# na FSharpTV) </span><span class="sxs-lookup"><span data-stu-id="2145d-129">Introduction to F# series on FSharpTV</span></span>](https://fsharp.tv/courses/fsharp-programming-intro/)

## <a name="further-resources"></a><span data-ttu-id="2145d-130">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="2145d-130">Further Resources</span></span>

* [<span data-ttu-id="2145d-131">Recursos de aprendizado em F# do fsharp.org</span><span class="sxs-lookup"><span data-stu-id="2145d-131">F# Learning Resources on fsharp.org</span></span>](http://fsharp.org/learn.html)
* [<span data-ttu-id="2145d-132">Site de trechos de código F#</span><span class="sxs-lookup"><span data-stu-id="2145d-132">F# Snippets Website</span></span>](http://www.fssnip.net)
* [<span data-ttu-id="2145d-133">F# Software Foundation</span><span class="sxs-lookup"><span data-stu-id="2145d-133">F# Software Foundation</span></span>](http://fsharp.org)
