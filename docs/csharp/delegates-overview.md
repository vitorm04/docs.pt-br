---
title: "Introdução a Delegados"
description: "Saiba mais sobre delegados neste tópico de visão geral que apresenta os conceitos básicos e discute as metas de design da linguagem para delegados."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: dd4c68fb4f960d0c2d5cbdc9e699650070cacaf1
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="introduction-to-delegates"></a><span data-ttu-id="97869-104">Introdução a Delegados</span><span class="sxs-lookup"><span data-stu-id="97869-104">Introduction to Delegates</span></span>

[<span data-ttu-id="97869-105">Anterior</span><span class="sxs-lookup"><span data-stu-id="97869-105">Previous</span></span>](delegates-events.md)

<span data-ttu-id="97869-106">Os delegados fornecem um mecanismo de *associação tardia* no .NET.</span><span class="sxs-lookup"><span data-stu-id="97869-106">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="97869-107">Associação tardia significa que você cria um algoritmo em que o chamador também fornece pelo menos um método que implementa a parte do algoritmo.</span><span class="sxs-lookup"><span data-stu-id="97869-107">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="97869-108">Por exemplo, considere classificar uma lista de estrelas em um aplicativo de astronomia.</span><span class="sxs-lookup"><span data-stu-id="97869-108">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="97869-109">Você pode optar por classificar as estrelas por sua distância da terra ou a magnitude da estrela ou seu brilho percebido.</span><span class="sxs-lookup"><span data-stu-id="97869-109">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="97869-110">Em todos esses casos, o método Sort() faz essencialmente a mesma coisa: organiza os itens na lista com base em alguma comparação.</span><span class="sxs-lookup"><span data-stu-id="97869-110">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="97869-111">O código que compara duas estrelas é diferente para cada uma das ordenações de classificação.</span><span class="sxs-lookup"><span data-stu-id="97869-111">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="97869-112">Esses tipos de soluções foram usados no software por meio século.</span><span class="sxs-lookup"><span data-stu-id="97869-112">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="97869-113">O conceito de delegado de linguagem C# fornece suporte de linguagem de primeira classe e segurança de tipos em torno do conceito.</span><span class="sxs-lookup"><span data-stu-id="97869-113">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="97869-114">Como você verá posteriormente nesta série, o código C# que você escreve para algoritmos como esse é seguro quanto ao tipo e aproveita a linguagem e o compilador para garantir que os tipos correspondem aos argumentos e tipos de retorno.</span><span class="sxs-lookup"><span data-stu-id="97869-114">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="97869-115">Metas de design da linguagem para delegados</span><span class="sxs-lookup"><span data-stu-id="97869-115">Language Design Goals for Delegates</span></span>

<span data-ttu-id="97869-116">Os designers de linguagem enumeraram várias metas para o recurso que eventualmente se tornaram delegados.</span><span class="sxs-lookup"><span data-stu-id="97869-116">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="97869-117">A equipe queria um constructo de linguagem comum que pudesse ser usada qualquer algoritmo de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="97869-117">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="97869-118">Isso permite aos desenvolvedores aprender um conceito e usar esse conceito entre muitos problemas de software diferentes.</span><span class="sxs-lookup"><span data-stu-id="97869-118">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="97869-119">Em segundo lugar, a equipe queria dar suporte a chamadas de método single ou multicast.</span><span class="sxs-lookup"><span data-stu-id="97869-119">Second, the team wanted to support both single and multi-cast method calls.</span></span> <span data-ttu-id="97869-120">(Delegados multicast são delegados em que vários métodos foram encadeados.</span><span class="sxs-lookup"><span data-stu-id="97869-120">(Multicast delegates are delegates where multiple methods have been chained together.</span></span> <span data-ttu-id="97869-121">Você verá exemplos [posteriormente nesta série](delegate-class.md).</span><span class="sxs-lookup"><span data-stu-id="97869-121">You'll see examples [later in this series](delegate-class.md).</span></span> 

<span data-ttu-id="97869-122">A equipe queria delegados para dar suporte à mesma segurança de tipos que os desenvolvedores esperam de todos os constructos de C#.</span><span class="sxs-lookup"><span data-stu-id="97869-122">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span> 

<span data-ttu-id="97869-123">Por fim, a equipe reconheceu que um padrão de eventos é um padrão específico em que delegados ou qualquer algoritmo de associação tardia é muito útil.</span><span class="sxs-lookup"><span data-stu-id="97869-123">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm) is very useful.</span></span> <span data-ttu-id="97869-124">A equipe quis garantir que o código para delegados pudesse fornecer a base para o padrão de evento .NET.</span><span class="sxs-lookup"><span data-stu-id="97869-124">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="97869-125">O resultado de todo esse trabalho era o suporte do delegado e do evento no C# e .NET.</span><span class="sxs-lookup"><span data-stu-id="97869-125">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="97869-126">Os demais artigos nessa seção abordarão os recursos da linguagem, o suporte da biblioteca e as expressões comuns que são usadas ao trabalhar com delegados.</span><span class="sxs-lookup"><span data-stu-id="97869-126">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="97869-127">Você aprenderá sobre a palavra-chave `delegate` e qual código ela gera.</span><span class="sxs-lookup"><span data-stu-id="97869-127">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="97869-128">Você aprenderá sobre os recursos na classe `System.Delegate` e como esses recursos são usados.</span><span class="sxs-lookup"><span data-stu-id="97869-128">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="97869-129">Você aprenderá como criar delegados de segurança de tipos e como criar métodos que podem ser invocados por meio de delegados.</span><span class="sxs-lookup"><span data-stu-id="97869-129">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="97869-130">Você também aprenderá a trabalhar com eventos e delegados usando expressões Lambda.</span><span class="sxs-lookup"><span data-stu-id="97869-130">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="97869-131">Você verá onde delegados se tornam um dos blocos de construção para LINQ.</span><span class="sxs-lookup"><span data-stu-id="97869-131">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="97869-132">Você aprenderá como os delegados são a base para o padrão de evento do .NET e como eles são diferentes.</span><span class="sxs-lookup"><span data-stu-id="97869-132">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="97869-133">Em geral, você verá como os delegados são parte integrante de programação em .NET e no trabalho com as APIs de estrutura.</span><span class="sxs-lookup"><span data-stu-id="97869-133">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="97869-134">Vamos começar.</span><span class="sxs-lookup"><span data-stu-id="97869-134">Let's get started.</span></span>

[<span data-ttu-id="97869-135">Avançar</span><span class="sxs-lookup"><span data-stu-id="97869-135">Next</span></span>](delegate-class.md)

