---
title: Visão geral das ferramentas de diagnóstico – .NET Core
description: Uma visão geral das ferramentas e das técnicas disponíveis para diagnosticar aplicativos .NET Core.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: e97acccbe3bdd577ee600cefb9f1f0528d3c1ac0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538521"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="c7c71-103">Quais ferramentas de diagnóstico estão disponíveis no .NET Core?</span><span class="sxs-lookup"><span data-stu-id="c7c71-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="c7c71-104">O software nem sempre se comporta como esperado, mas o .NET Core tem ferramentas e APIs que ajudarão você a diagnosticar esses problemas de maneira rápida e eficaz.</span><span class="sxs-lookup"><span data-stu-id="c7c71-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="c7c71-105">Este artigo ajuda a identificar as diversas ferramentas de que você precisa.</span><span class="sxs-lookup"><span data-stu-id="c7c71-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="c7c71-106">Depuradores gerenciados</span><span class="sxs-lookup"><span data-stu-id="c7c71-106">Managed debuggers</span></span>

<span data-ttu-id="c7c71-107">Os [depuradores gerenciados](managed-debuggers.md) permitem que você interaja com seu programa.</span><span class="sxs-lookup"><span data-stu-id="c7c71-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="c7c71-108">Pausar, executar incrementalmente, examinar e retomar fornecem informações sobre o comportamento do seu código.</span><span class="sxs-lookup"><span data-stu-id="c7c71-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="c7c71-109">Um depurador é a primeira opção para diagnosticar problemas funcionais que podem ser facilmente reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="c7c71-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="c7c71-110">Registro em log e rastreamento</span><span class="sxs-lookup"><span data-stu-id="c7c71-110">Logging and tracing</span></span>

<span data-ttu-id="c7c71-111">O [registro em log e o rastreamento](logging-tracing.md) são técnicas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="c7c71-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="c7c71-112">Eles se referem ao código de instrumentação para criar arquivos de log.</span><span class="sxs-lookup"><span data-stu-id="c7c71-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="c7c71-113">Os arquivos registram os detalhes do que um programa faz.</span><span class="sxs-lookup"><span data-stu-id="c7c71-113">The files record the details of what a program does.</span></span> <span data-ttu-id="c7c71-114">Esses detalhes podem ser usados para diagnosticar os problemas mais complexos.</span><span class="sxs-lookup"><span data-stu-id="c7c71-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="c7c71-115">Quando aliados aos carimbos de data/hora, essas técnicas também são valiosas para as investigações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="c7c71-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="c7c71-116">Teste de unidade</span><span class="sxs-lookup"><span data-stu-id="c7c71-116">Unit testing</span></span>

<span data-ttu-id="c7c71-117">O [teste de unidade](../testing/index.md) é um componente fundamental da integração e da implantação contínuas de software de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="c7c71-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="c7c71-118">Os testes de unidade são projetados para fornecer um aviso antecipado quando você interrompe algo.</span><span class="sxs-lookup"><span data-stu-id="c7c71-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="debug-linux-dumps"></a><span data-ttu-id="c7c71-119">Depurar despejos do Linux</span><span class="sxs-lookup"><span data-stu-id="c7c71-119">Debug Linux dumps</span></span>

<span data-ttu-id="c7c71-120">[Depurar despejos do Linux](debug-linux-dumps.md) explica como coletar e analisar despejos no Linux.</span><span class="sxs-lookup"><span data-stu-id="c7c71-120">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="c7c71-121">Ferramentas globais de diagnóstico do .NET Core</span><span class="sxs-lookup"><span data-stu-id="c7c71-121">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="c7c71-122">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="c7c71-122">dotnet-counters</span></span>

<span data-ttu-id="c7c71-123">[dotnet-os contadores](dotnet-counters.md) são uma ferramenta de monitoramento de desempenho para a investigação de desempenho e monitoramento de integridade de primeiro nível.</span><span class="sxs-lookup"><span data-stu-id="c7c71-123">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="c7c71-124">Ele observa os valores do contador de desempenho publicados por meio da <xref:System.Diagnostics.Tracing.EventCounter> API.</span><span class="sxs-lookup"><span data-stu-id="c7c71-124">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="c7c71-125">Por exemplo, você pode monitorar rapidamente coisas como o uso da CPU ou a taxa de exceções que estão sendo geradas em seu aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7c71-125">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="c7c71-126">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="c7c71-126">dotnet-dump</span></span>

<span data-ttu-id="c7c71-127">A ferramenta [dotnet-dump](dotnet-dump.md) é uma maneira de coletar e analisar despejos do Windows e do Linux Core sem um depurador nativo.</span><span class="sxs-lookup"><span data-stu-id="c7c71-127">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="c7c71-128">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="c7c71-128">dotnet-gcdump</span></span>

<span data-ttu-id="c7c71-129">A ferramenta [dotnet-gcdump](dotnet-gcdump.md) é uma maneira de coletar despejos de GC (coletor de lixo) de processos do .net em tempo real.</span><span class="sxs-lookup"><span data-stu-id="c7c71-129">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="c7c71-130">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="c7c71-130">dotnet-trace</span></span>

<span data-ttu-id="c7c71-131">O .NET Core inclui o que é chamado de `EventPipe` por meio do qual os dados de diagnóstico são expostos.</span><span class="sxs-lookup"><span data-stu-id="c7c71-131">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="c7c71-132">A ferramenta [dotnet-Trace](dotnet-trace.md) permite que você consuma dados de criação de perfil interessantes de seu aplicativo que podem ajudar em cenários em que você precisa ter a causa raiz dos aplicativos em execução lenta.</span><span class="sxs-lookup"><span data-stu-id="c7c71-132">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="c7c71-133">dotnet-symbol</span><span class="sxs-lookup"><span data-stu-id="c7c71-133">dotnet-symbol</span></span>

<span data-ttu-id="c7c71-134">[dotnet-Symbol](dotnet-symbol.md) baixa arquivos (símbolos, DAC/DBI, arquivos de host, etc.) necessários para abrir um dump principal ou minidespejo.</span><span class="sxs-lookup"><span data-stu-id="c7c71-134">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="c7c71-135">Use essa ferramenta se precisar de símbolos e módulos para depurar um arquivo de despejo capturado em um computador diferente.</span><span class="sxs-lookup"><span data-stu-id="c7c71-135">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="c7c71-136">dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="c7c71-136">dotnet-sos</span></span>

<span data-ttu-id="c7c71-137">[dotnet-SOS](dotnet-sos.md) é usado para instalar a [extensão de depuração SOS](../../framework/tools/sos-dll-sos-debugging-extension.md) no Linux ou MacOS (ou no Windows, se estiver usando ferramentas de depuração mais antigas).</span><span class="sxs-lookup"><span data-stu-id="c7c71-137">[dotnet-sos](dotnet-sos.md) is used to install the [SOS debugging extension](../../framework/tools/sos-dll-sos-debugging-extension.md) on Linux or MacOS (or on Windows if using older debugging tools).</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="c7c71-138">Tutoriais de diagnóstico do .NET Core</span><span class="sxs-lookup"><span data-stu-id="c7c71-138">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="c7c71-139">Depurar um vazamento de memória</span><span class="sxs-lookup"><span data-stu-id="c7c71-139">Debug a memory leak</span></span>

<span data-ttu-id="c7c71-140">[Tutorial: Depurar um vazamento de memória](debug-memory-leak.md) percorre a localização de um vazamento de memória.</span><span class="sxs-lookup"><span data-stu-id="c7c71-140">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="c7c71-141">A ferramenta [dotnet-Counters](dotnet-counters.md) é usada para confirmar o vazamento e a ferramenta [dotnet-dump](dotnet-dump.md) é usada para diagnosticar o vazamento.</span><span class="sxs-lookup"><span data-stu-id="c7c71-141">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="c7c71-142">Depurar alto uso da CPU</span><span class="sxs-lookup"><span data-stu-id="c7c71-142">Debug high CPU usage</span></span>

<span data-ttu-id="c7c71-143">[Tutorial: Depurar alto uso da CPU](debug-highcpu.md) orienta você na investigação de alto uso da CPU.</span><span class="sxs-lookup"><span data-stu-id="c7c71-143">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="c7c71-144">Ele usa a ferramenta [dotnet-Counters](dotnet-counters.md) para confirmar o alto uso da CPU.</span><span class="sxs-lookup"><span data-stu-id="c7c71-144">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="c7c71-145">Em seguida, ele orienta você pelo uso [do trace for performance Analysis Utility ( `dotnet-trace` ) ou do](dotnet-trace.md) Linux `perf` para coletar e exibir o perfil de uso da CPU.</span><span class="sxs-lookup"><span data-stu-id="c7c71-145">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="c7c71-146">Depurar deadlock</span><span class="sxs-lookup"><span data-stu-id="c7c71-146">Debug deadlock</span></span>

<span data-ttu-id="c7c71-147">[Tutorial: debug deadlock](debug-deadlock.md) mostra como usar a ferramenta [dotnet-dump](dotnet-dump.md) para investigar threads e bloqueios.</span><span class="sxs-lookup"><span data-stu-id="c7c71-147">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>
