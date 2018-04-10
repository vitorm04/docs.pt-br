---
title: Novidades no C# – Guia do C#
description: Como a linguagem C# está evoluindo
keywords: C#, recursos mais recentes, novidades, Roslyn
author: BillWagner
ms.author: wiwagn
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: 719fbe826b0b115b19067dbaf0d04f14e6534890
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="whats-new-in-c"></a><span data-ttu-id="0aebb-104">Novidades no C#</span><span class="sxs-lookup"><span data-stu-id="0aebb-104">What's new in C#</span></span> #

<span data-ttu-id="0aebb-105">Esta página fornece um roteiro de novos recursos em cada versão principal da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="0aebb-105">This page provides a roadmap of new features in each major release of the C# language.</span></span> <span data-ttu-id="0aebb-106">Os links a seguir fornecem informações detalhadas sobre os principais recursos adicionados a cada versão.</span><span class="sxs-lookup"><span data-stu-id="0aebb-106">The following links provide detailed information on the major features added in each release.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0aebb-107">A linguagem C# depende de tipos e métodos em uma *biblioteca padrão* para alguns dos recursos.</span><span class="sxs-lookup"><span data-stu-id="0aebb-107">The C# language relies on types and methods in a *standard library* for some of the features.</span></span> <span data-ttu-id="0aebb-108">Um exemplo é o processamento de exceção.</span><span class="sxs-lookup"><span data-stu-id="0aebb-108">One example is exception processing.</span></span> <span data-ttu-id="0aebb-109">Cada instrução ou expressão `throw` é verificada para garantir que o objeto que está sendo gerado é derivado de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="0aebb-109">Every `throw` statement or expression is checked to ensure the object being thrown is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="0aebb-110">Da mesma forma, cada `catch` é verificado para garantir que o tipo que está sendo capturado é derivado de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="0aebb-110">Similarly, every `catch` is checked to ensure that the type being caught is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="0aebb-111">Cada versão pode adicionar novos requisitos.</span><span class="sxs-lookup"><span data-stu-id="0aebb-111">Each version may add new requirements.</span></span> <span data-ttu-id="0aebb-112">Para usar os recursos de linguagem mais recentes em ambientes mais antigos, talvez seja necessário instalar bibliotecas específicas.</span><span class="sxs-lookup"><span data-stu-id="0aebb-112">To use the latest language features in older environments, you may need to install specific libraries.</span></span> <span data-ttu-id="0aebb-113">Essas dependências estão documentadas na página de cada versão específica.</span><span class="sxs-lookup"><span data-stu-id="0aebb-113">These dependencies are documented in the page for each specific version.</span></span> <span data-ttu-id="0aebb-114">Saiba mais sobre as [relações entre linguagem e biblioteca](relationships-between-language-and-library.md) para obter informações sobre essa dependência.</span><span class="sxs-lookup"><span data-stu-id="0aebb-114">You can learn more about the [relationships between language and library](relationships-between-language-and-library.md) for background on this dependency.</span></span> 


* <span data-ttu-id="0aebb-115">[C# 7.2](csharp-7-2.md):</span><span class="sxs-lookup"><span data-stu-id="0aebb-115">[C# 7.2](csharp-7-2.md):</span></span>
    - <span data-ttu-id="0aebb-116">Esta página descreve os recursos mais recentes na linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="0aebb-116">This page describes the latest features in the C# language.</span></span> <span data-ttu-id="0aebb-117">O C#7.2 está disponível atualmente no [Visual Studio 2017 versão 15.5](https://www.visualstudio.com/vs/whatsnew/) e no [SDK do .NET Core 2.0](../../core/whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="0aebb-117">C# 7.2 is currently available in [Visual Studio 2017 version 15.5](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="0aebb-118">[C# 7.1](csharp-7-1.md):</span><span class="sxs-lookup"><span data-stu-id="0aebb-118">[C# 7.1](csharp-7-1.md):</span></span>
    - <span data-ttu-id="0aebb-119">Esta página descreve os recursos no C# 7.1.</span><span class="sxs-lookup"><span data-stu-id="0aebb-119">This page describes the features in C# 7.1.</span></span> <span data-ttu-id="0aebb-120">Esses recursos foram adicionados no [Visual Studio 2017 versão 15.3](https://www.visualstudio.com/vs/whatsnew/) e no [SDK do .NET Core 2.0](../../core/whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="0aebb-120">These features were added in [Visual Studio 2017 version 15.3](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="0aebb-121">[C# 7](csharp-7.md):</span><span class="sxs-lookup"><span data-stu-id="0aebb-121">[C# 7](csharp-7.md):</span></span>
    - <span data-ttu-id="0aebb-122">Esta página descreve os recursos adicionados ao C# 7.</span><span class="sxs-lookup"><span data-stu-id="0aebb-122">This page describes the features added in C# 7.</span></span> <span data-ttu-id="0aebb-123">Esses recursos foram adicionados ao [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) e ao [.NET Core 1.0](../../core/whats-new/index.md) e posterior</span><span class="sxs-lookup"><span data-stu-id="0aebb-123">These features were added in [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) and [.NET Core 1.0](../../core/whats-new/index.md) and later</span></span>
     
* <span data-ttu-id="0aebb-124">[C# 6](csharp-6.md):</span><span class="sxs-lookup"><span data-stu-id="0aebb-124">[C# 6](csharp-6.md):</span></span>
    - <span data-ttu-id="0aebb-125">Esta página descreve os recursos que foram adicionados no C# 6.</span><span class="sxs-lookup"><span data-stu-id="0aebb-125">This page describes the features that were added in C# 6.</span></span> <span data-ttu-id="0aebb-126">Esses recursos estão disponíveis no Visual Studio 2015 para desenvolvedores do Windows e no .NET Core 1.0 para desenvolvedores explorando o C# no macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="0aebb-126">These features are available in Visual Studio 2015 for Windows developers, and on .NET Core 1.0 for developers exploring C# on macOS and Linux.</span></span>

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* <span data-ttu-id="0aebb-127">[Suporte de plataforma cruzada](../../core/index.md):</span><span class="sxs-lookup"><span data-stu-id="0aebb-127">[Cross Platform Support](../../core/index.md):</span></span>
    - <span data-ttu-id="0aebb-128">O C#, por meio do suporte do .NET Core, é executado em várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="0aebb-128">C#, through .NET Core support, runs on multiple platforms.</span></span> <span data-ttu-id="0aebb-129">Se estiver interessado em testar o C# no macOS ou em uma das várias distribuições do Linux com suporte, saiba mais sobre o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0aebb-129">If you are interested in trying C# on macOS, or on one of the many supported Linux distributions, learn more about .NET Core.</span></span>

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a><span data-ttu-id="0aebb-130">Versões anteriores</span><span class="sxs-lookup"><span data-stu-id="0aebb-130">Previous Versions</span></span>
<span data-ttu-id="0aebb-131">A seguir estão listados as principais funcionalidades que foram introduzidas em versões anteriores da linguagem C# e Visual Studio .NET.</span><span class="sxs-lookup"><span data-stu-id="0aebb-131">The following lists key features that were introduced in previous versions of the C# language and Visual Studio .NET.</span></span>  
  
 * <span data-ttu-id="0aebb-132">Visual Studio .NET 2013:</span><span class="sxs-lookup"><span data-stu-id="0aebb-132">Visual Studio .NET 2013:</span></span> 
     - <span data-ttu-id="0aebb-133">Esta versão do Visual Studio incluiu correções de bug, aprimoramentos de desempenho e visualizações de tecnologia da Plataforma do Compilador .NET ("Roslyn"), que se tornou o SDK de Plataforma do Compilador .NET<!--Link to ../roslyn/index.md-->.</span><span class="sxs-lookup"><span data-stu-id="0aebb-133">This version of Visual Studio included bug fixes, performance improvements, and technology previews of .NET Compiler Platform ("Roslyn") which became the .NET Compiler Platform SDK<!--Link to ../roslyn/index.md-->.</span></span>

 * <span data-ttu-id="0aebb-134">C# 5, Visual Studio .NET 2012:</span><span class="sxs-lookup"><span data-stu-id="0aebb-134">C# 5, Visual Studio .NET 2012:</span></span> 
     - <span data-ttu-id="0aebb-135">`Async` / `await`, atributos de [informações do chamador](../programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="0aebb-135">`Async` / `await`, and [caller information](../programming-guide/concepts/caller-information.md) attributes.</span></span>

 * <span data-ttu-id="0aebb-136">C# 4, Visual Studio .NET 2010:</span><span class="sxs-lookup"><span data-stu-id="0aebb-136">C# 4, Visual Studio .NET 2010:</span></span> 
     - <span data-ttu-id="0aebb-137">`Dynamic`, [argumentos nomeados](../programming-guide/classes-and-structs/named-and-optional-arguments.md), parâmetros opcionais e [covariância e contravariância](../programming-guide/concepts/covariance-contravariance/index.md) genéricas.</span><span class="sxs-lookup"><span data-stu-id="0aebb-137">`Dynamic`, [named arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md), optional parameters, and generic [covariance and contra variance](../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

 * <span data-ttu-id="0aebb-138">C# 3, Visual Studio .NET 2008:</span><span class="sxs-lookup"><span data-stu-id="0aebb-138">C# 3, Visual Studio .NET 2008:</span></span> 
     - <span data-ttu-id="0aebb-139">Inicializadores de objeto e coleção, expressões lambda, métodos de extensão, tipos anônimos, propriedades automáticas, inferência de tipos `var` local e [LINQ (Consulta Integrada à Linguagem)](../programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="0aebb-139">Object and collection initializers, lambda expressions, extension methods, anonymous types, automatic properties, local `var` type inference, and [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).</span></span>

 * <span data-ttu-id="0aebb-140">C# 2, Visual Studio .NET 2005:</span><span class="sxs-lookup"><span data-stu-id="0aebb-140">C# 2, Visual Studio .NET 2005:</span></span> 
     - <span data-ttu-id="0aebb-141">Métodos anônimos, genéricos, tipos anuláveis, iteradores/suspensão, classes `static`, covariância e contravariância para delegados.</span><span class="sxs-lookup"><span data-stu-id="0aebb-141">Anonymous methods, generics, nullable types, iterators/yield, `static` classes, and covariance and contra variance for delegates.</span></span>

 * <span data-ttu-id="0aebb-142">C# 1.1, Visual Studio .NET 2003:</span><span class="sxs-lookup"><span data-stu-id="0aebb-142">C# 1.1, Visual Studio .NET 2003:</span></span> 
     - <span data-ttu-id="0aebb-143">Comentários da documentação XML e pragma `#line`.</span><span class="sxs-lookup"><span data-stu-id="0aebb-143">`#line` pragma and xml doc comments.</span></span>

 * <span data-ttu-id="0aebb-144">C# 1, Visual Studio .NET 2002:</span><span class="sxs-lookup"><span data-stu-id="0aebb-144">C# 1, Visual Studio .NET 2002:</span></span> 
     - <span data-ttu-id="0aebb-145">A primeira versão do [C#](../csharp.md).</span><span class="sxs-lookup"><span data-stu-id="0aebb-145">The first release of [C#](../csharp.md).</span></span>   
