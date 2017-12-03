---
title: Guia de F#
description: "Saiba mais sobre F #, uma linguagem de programação funcional que é executado no .NET."
keywords: .NET, .NET Core
author: jackfoxy
ms.author: phcart
ms.date: 12/01/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: 45f5d2ca794ccea7a35cf6c0bf9d58a3e6500453
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="f-guide"></a><span data-ttu-id="f797a-104">Guia de F#</span><span class="sxs-lookup"><span data-stu-id="f797a-104">F# Guide</span></span>

<span data-ttu-id="f797a-105">F # é uma linguagem de programação funcional que é executado no .NET.</span><span class="sxs-lookup"><span data-stu-id="f797a-105">F# is a functional programming language which runs on .NET.</span></span>  <span data-ttu-id="f797a-106">Além de suporte construções de programação funcionais, ele também tem recursos de programação do objeto.</span><span class="sxs-lookup"><span data-stu-id="f797a-106">In addition to supporting functional programming constructs, it also has object programming capabilities.</span></span>  <span data-ttu-id="f797a-107">Torna essa híbrida de programação funcional com recursos orientados a objeto F # um idioma pragmático para realizar qualquer tarefa.</span><span class="sxs-lookup"><span data-stu-id="f797a-107">This hybrid of functional programming with object-oriented capabilities makes F# a pragmatic language for accomplishing any task.</span></span>

## <a name="if-youre-new-to-f"></a><span data-ttu-id="f797a-108">Se você for novo no F #</span><span class="sxs-lookup"><span data-stu-id="f797a-108">If You're New to F#</span></span> #

<span data-ttu-id="f797a-109">Se você for novo no F #, comece com o [Tour do F #](tour.md) para obter uma visão geral da linguagem e alguns dos seus conceitos de programação.</span><span class="sxs-lookup"><span data-stu-id="f797a-109">If you're new to F#, begin with the [Tour of F#](tour.md) to get an overview of the language and some of its programming concepts.</span></span>  <span data-ttu-id="f797a-110">Se você estiver usando o Visual Studio, o modelo de projeto do Tutorial contém o mesmo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f797a-110">If you're using Visual Studio, the Tutorial project template contains the same content.</span></span>

## <a name="if-youre-experienced-with-f"></a><span data-ttu-id="f797a-111">Se você tiver experiência com F #</span><span class="sxs-lookup"><span data-stu-id="f797a-111">If You're Experienced with F#</span></span> #

<span data-ttu-id="f797a-112">Se você souber o caminho para F #, ou saber mais sobre a construção de um idioma específico, consulte o [referência de linguagem](language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="f797a-112">If you know your way around F#, or want to learn more about a specific language construct, see the [Language Reference](language-reference/index.md).</span></span>  <span data-ttu-id="f797a-113">É um guia completo de todos os recursos de linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="f797a-113">It's a thorough guide of all F# language capabilities.</span></span>

<span data-ttu-id="f797a-114">Além disso, o [referência da biblioteca principal F #](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) é um ótimo recurso para aprender sobre FSharp. Core, a biblioteca principal que faz parte da linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="f797a-114">Additionally, the [F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) is a great resource for learning about FSharp.Core, the core library which is a part of F#.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="f797a-115">O F# Software Foundation</span><span class="sxs-lookup"><span data-stu-id="f797a-115">The F# Software Foundation</span></span>

<span data-ttu-id="f797a-116">Embora a Microsoft é o principal do desenvolvedor da linguagem F # e suas ferramentas, F # é também o apoio de uma base independente, o F # Software Foundation (FSSF).</span><span class="sxs-lookup"><span data-stu-id="f797a-116">Although Microsoft is the primary developer of the F# language and its tooling, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="f797a-117">A missão do F# Software Foundation é promover, proteger e evoluir a linguagem de programação F#, além de dar suporte e facilitar o crescimento de uma comunidade internacional e diversa de programadores em F#.</span><span class="sxs-lookup"><span data-stu-id="f797a-117">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="f797a-118">Para saber mais e se envolver, confira [fsharp.org](http://fsharp.org).</span><span class="sxs-lookup"><span data-stu-id="f797a-118">To learn more and get involved, check out [fsharp.org](http://fsharp.org).</span></span>

## <a name="documentation"></a><span data-ttu-id="f797a-119">Documentação</span><span class="sxs-lookup"><span data-stu-id="f797a-119">Documentation</span></span>

* [<span data-ttu-id="f797a-120">Tutoriais</span><span class="sxs-lookup"><span data-stu-id="f797a-120">Tutorials</span></span>](tutorials/getting-started/index.md)
* <span data-ttu-id="f797a-121">[Funções como valores de primeira classe](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span><span class="sxs-lookup"><span data-stu-id="f797a-121">[Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span></span>
* [<span data-ttu-id="f797a-122">Referência de Linguagem</span><span class="sxs-lookup"><span data-stu-id="f797a-122">Language Reference</span></span>](language-reference/index.md)
* [<span data-ttu-id="f797a-123">Referência da biblioteca de F# Core</span><span class="sxs-lookup"><span data-stu-id="f797a-123">F# Core Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)

## <a name="online-reading-resources"></a><span data-ttu-id="f797a-124">Recursos online para leitura</span><span class="sxs-lookup"><span data-stu-id="f797a-124">Online Reading Resources</span></span>

* [<span data-ttu-id="f797a-125">F# for Fun and Profit Gitbook (Gitbook: F# por diversão e lucro)</span><span class="sxs-lookup"><span data-stu-id="f797a-125">F# for Fun and Profit Gitbook</span></span>](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) 
* [<span data-ttu-id="f797a-126">Wikibook sobre programação em F#</span><span class="sxs-lookup"><span data-stu-id="f797a-126">F# Programming Wikibook</span></span>](https://en.wikibooks.org/wiki/F_Sharp_Programming)

## <a name="video-learning-resources"></a><span data-ttu-id="f797a-127">Recursos de aprendizagem em vídeo</span><span class="sxs-lookup"><span data-stu-id="f797a-127">Video Learning Resources</span></span>

* [<span data-ttu-id="f797a-128">Série de Introdução à programação em F# no YouTube</span><span class="sxs-lookup"><span data-stu-id="f797a-128">Introduction to Programming with F# series on YouTube</span></span>](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)
* [<span data-ttu-id="f797a-129">Introduction to F# series on FSharpTV (Série Introdução ao F# na FSharpTV) </span><span class="sxs-lookup"><span data-stu-id="f797a-129">Introduction to F# series on FSharpTV</span></span>](https://fsharp.tv/courses/fsharp-programming-intro/)

## <a name="further-resources"></a><span data-ttu-id="f797a-130">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="f797a-130">Further Resources</span></span>

* [<span data-ttu-id="f797a-131">Recursos de aprendizado em F# do fsharp.org</span><span class="sxs-lookup"><span data-stu-id="f797a-131">F# Learning Resources on fsharp.org</span></span>](http://fsharp.org/learn.html)
* [<span data-ttu-id="f797a-132">Site de trechos de código F#</span><span class="sxs-lookup"><span data-stu-id="f797a-132">F# Snippets Website</span></span>](http://www.fssnip.net)
* [<span data-ttu-id="f797a-133">F# Software Foundation</span><span class="sxs-lookup"><span data-stu-id="f797a-133">F# Software Foundation</span></span>](http://fsharp.org)