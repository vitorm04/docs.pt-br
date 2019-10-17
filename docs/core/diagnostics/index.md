---
title: Visão geral das ferramentas de diagnóstico – .NET Core
description: Uma visão geral das ferramentas e das técnicas disponíveis para diagnosticar aplicativos .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.topic: overview
ms.openlocfilehash: c0a45a1bfe866ad42890db576b5dd5098b1dbc3d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318340"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="aecda-103">Quais ferramentas de diagnóstico estão disponíveis no .NET Core?</span><span class="sxs-lookup"><span data-stu-id="aecda-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="aecda-104">O software nem sempre se comporta como esperado, mas o .NET Core tem ferramentas e APIs que ajudarão você a diagnosticar esses problemas de maneira rápida e eficaz.</span><span class="sxs-lookup"><span data-stu-id="aecda-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="aecda-105">Este artigo ajuda a identificar as diversas ferramentas de que você precisa.</span><span class="sxs-lookup"><span data-stu-id="aecda-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="aecda-106">Depuradores gerenciados</span><span class="sxs-lookup"><span data-stu-id="aecda-106">Managed debuggers</span></span>

<span data-ttu-id="aecda-107">Os [depuradores gerenciados](managed-debuggers.md) permitem que você interaja com seu programa.</span><span class="sxs-lookup"><span data-stu-id="aecda-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="aecda-108">Pausar, executar incrementalmente, examinar e retomar fornecem informações sobre o comportamento do seu código.</span><span class="sxs-lookup"><span data-stu-id="aecda-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="aecda-109">Um depurador é a primeira opção para diagnosticar problemas funcionais que podem ser facilmente reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="aecda-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="aecda-110">Registro em log e rastreamento</span><span class="sxs-lookup"><span data-stu-id="aecda-110">Logging and tracing</span></span>

<span data-ttu-id="aecda-111">O [registro em log e o rastreamento](logging-tracing.md) são técnicas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="aecda-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="aecda-112">Eles se referem ao código de instrumentação para criar arquivos de log.</span><span class="sxs-lookup"><span data-stu-id="aecda-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="aecda-113">Os arquivos registram os detalhes do que um programa faz.</span><span class="sxs-lookup"><span data-stu-id="aecda-113">The files record the details of what a program does.</span></span> <span data-ttu-id="aecda-114">Esses detalhes podem ser usados para diagnosticar os problemas mais complexos.</span><span class="sxs-lookup"><span data-stu-id="aecda-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="aecda-115">Quando aliados aos carimbos de data/hora, essas técnicas também são valiosas para as investigações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="aecda-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="aecda-116">Teste de unidade</span><span class="sxs-lookup"><span data-stu-id="aecda-116">Unit testing</span></span>

<span data-ttu-id="aecda-117">O [teste de unidade](../testing/index.md) é um componente fundamental da integração e da implantação contínuas de software de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="aecda-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="aecda-118">Os testes de unidade são projetados para fornecer um aviso antecipado quando você interrompe algo.</span><span class="sxs-lookup"><span data-stu-id="aecda-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="net-core-dotnet-diagnostic-global-tools"></a><span data-ttu-id="aecda-119">Ferramentas globais de diagnóstico dotnet do .NET Core</span><span class="sxs-lookup"><span data-stu-id="aecda-119">.NET Core dotnet diagnostic Global Tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="aecda-120">dotnet-contadores</span><span class="sxs-lookup"><span data-stu-id="aecda-120">dotnet-counters</span></span>

<span data-ttu-id="aecda-121">[dotnet-os contadores](dotnet-counters.md) são uma ferramenta de monitoramento de desempenho para a investigação de desempenho e monitoramento de integridade de primeiro nível.</span><span class="sxs-lookup"><span data-stu-id="aecda-121">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="aecda-122">Ele observa os valores do contador de desempenho publicados por meio da API <xref:System.Diagnostics.Tracing.EventCounter>.</span><span class="sxs-lookup"><span data-stu-id="aecda-122">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="aecda-123">Por exemplo, você pode monitorar rapidamente coisas como o uso da CPU ou a taxa de exceções que estão sendo geradas em seu aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aecda-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="aecda-124">dotnet-despejo</span><span class="sxs-lookup"><span data-stu-id="aecda-124">dotnet-dump</span></span>

<span data-ttu-id="aecda-125">A ferramenta [dotnet-dump](dotnet-dump.md) é uma maneira de coletar e analisar despejos do Windows e do Linux Core sem um depurador nativo.</span><span class="sxs-lookup"><span data-stu-id="aecda-125">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="aecda-126">dotnet-rastreamento</span><span class="sxs-lookup"><span data-stu-id="aecda-126">dotnet-trace</span></span>

<span data-ttu-id="aecda-127">O .NET Core inclui o que é chamado de `EventPipe` por meio do qual os dados de diagnóstico são expostos.</span><span class="sxs-lookup"><span data-stu-id="aecda-127">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="aecda-128">A ferramenta [dotnet-Trace](dotnet-trace.md) permite que você consuma dados de criação de perfil interessantes de seu aplicativo que podem ajudar em cenários em que você precisa ter a causa raiz dos aplicativos em execução lenta.</span><span class="sxs-lookup"><span data-stu-id="aecda-128">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>
