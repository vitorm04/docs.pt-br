---
title: Visão geral das ferramentas de diagnóstico – .NET Core
description: Uma visão geral das ferramentas e das técnicas disponíveis para diagnosticar aplicativos .NET Core.
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 0a78ec6c88f5323104277cddea4480a5e13b4e41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399045"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="ec5b7-103">Quais ferramentas de diagnóstico estão disponíveis no .NET Core?</span><span class="sxs-lookup"><span data-stu-id="ec5b7-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="ec5b7-104">O software nem sempre se comporta como esperado, mas o .NET Core tem ferramentas e APIs que ajudarão você a diagnosticar esses problemas de maneira rápida e eficaz.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="ec5b7-105">Este artigo ajuda a identificar as diversas ferramentas de que você precisa.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="ec5b7-106">Depuradores gerenciados</span><span class="sxs-lookup"><span data-stu-id="ec5b7-106">Managed debuggers</span></span>

<span data-ttu-id="ec5b7-107">[Os depuradores gerenciados](managed-debuggers.md) permitem que você interaja com seu programa.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="ec5b7-108">Pausar, executar incrementalmente, examinar e retomar fornecem informações sobre o comportamento do seu código.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="ec5b7-109">Um depurador é a primeira opção para diagnosticar problemas funcionais que podem ser facilmente reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="ec5b7-110">Log e rastreamento</span><span class="sxs-lookup"><span data-stu-id="ec5b7-110">Logging and tracing</span></span>

<span data-ttu-id="ec5b7-111">[Registro e rastreamento](logging-tracing.md) são técnicas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="ec5b7-112">Eles se referem ao código de instrumentação para criar arquivos de log.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="ec5b7-113">Os arquivos registram os detalhes do que um programa faz.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-113">The files record the details of what a program does.</span></span> <span data-ttu-id="ec5b7-114">Esses detalhes podem ser usados para diagnosticar os problemas mais complexos.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="ec5b7-115">Quando aliados aos carimbos de data/hora, essas técnicas também são valiosas para as investigações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="ec5b7-116">Teste de unidade</span><span class="sxs-lookup"><span data-stu-id="ec5b7-116">Unit testing</span></span>

<span data-ttu-id="ec5b7-117">[O teste unitário](../testing/index.md) é um componente-chave da integração contínua e implantação de software de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="ec5b7-118">Os testes de unidade são projetados para fornecer um aviso antecipado quando você interrompe algo.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="net-core-dotnet-diagnostic-global-tools"></a><span data-ttu-id="ec5b7-119">.NET Core dotnet diagnóstico Global Tools</span><span class="sxs-lookup"><span data-stu-id="ec5b7-119">.NET Core dotnet diagnostic Global Tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="ec5b7-120">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="ec5b7-120">dotnet-counters</span></span>

<span data-ttu-id="ec5b7-121">[dotnet-counters](dotnet-counters.md) é uma ferramenta de monitoramento de desempenho para monitoramento de saúde de primeiro nível e investigação de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-121">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="ec5b7-122">Observa valores de contador <xref:System.Diagnostics.Tracing.EventCounter> de desempenho publicados através da API.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-122">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="ec5b7-123">Por exemplo, você pode monitorar rapidamente coisas como o uso da CPU ou a taxa de exceções que estão sendo lançadas no seu aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="ec5b7-124">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="ec5b7-124">dotnet-dump</span></span>

<span data-ttu-id="ec5b7-125">A ferramenta [dotnet-dump](dotnet-dump.md) é uma maneira de coletar e analisar dumps centrais do Windows e Linux sem um depurador nativo.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-125">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="ec5b7-126">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="ec5b7-126">dotnet-trace</span></span>

<span data-ttu-id="ec5b7-127">O Núcleo .NET inclui `EventPipe` o que é chamado de através do qual os dados de diagnóstico são expostos.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-127">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="ec5b7-128">A ferramenta [dotnet-trace](dotnet-trace.md) permite que você consuma dados interessantes de criação de perfil do seu aplicativo que podem ajudar em cenários onde você precisa criar aplicativos de causa em execução lenta.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-128">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="ec5b7-129">Tutoriais de diagnóstico do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ec5b7-129">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="ec5b7-130">Depurar um vazamento de memória</span><span class="sxs-lookup"><span data-stu-id="ec5b7-130">Debug a memory leak</span></span>

<span data-ttu-id="ec5b7-131">[Tutorial: Depurar um vazamento de memória](debug-memory-leak.md) passa por encontrar um vazamento de memória.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-131">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="ec5b7-132">A ferramenta [dotnet-counters](dotnet-counters.md) é usada para confirmar o vazamento e a ferramenta [dotnet-dump](dotnet-dump.md) é usada para diagnosticar o vazamento.</span><span class="sxs-lookup"><span data-stu-id="ec5b7-132">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>
