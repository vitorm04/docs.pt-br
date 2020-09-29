---
title: Visão geral das ferramentas de diagnóstico – .NET Core
description: Uma visão geral das ferramentas e das técnicas disponíveis para diagnosticar aplicativos .NET Core.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: d78b73e53637927ecb877dd69054f75a1f5ac91f
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91437997"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="8133c-103">Quais ferramentas de diagnóstico estão disponíveis no .NET Core?</span><span class="sxs-lookup"><span data-stu-id="8133c-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="8133c-104">O software nem sempre se comporta como esperado, mas o .NET Core tem ferramentas e APIs que ajudarão você a diagnosticar esses problemas de maneira rápida e eficaz.</span><span class="sxs-lookup"><span data-stu-id="8133c-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="8133c-105">Este artigo ajuda a identificar as diversas ferramentas de que você precisa.</span><span class="sxs-lookup"><span data-stu-id="8133c-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="8133c-106">Depuradores gerenciados</span><span class="sxs-lookup"><span data-stu-id="8133c-106">Managed debuggers</span></span>

<span data-ttu-id="8133c-107">Os [depuradores gerenciados](managed-debuggers.md) permitem que você interaja com seu programa.</span><span class="sxs-lookup"><span data-stu-id="8133c-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="8133c-108">Pausar, executar incrementalmente, examinar e retomar fornecem informações sobre o comportamento do seu código.</span><span class="sxs-lookup"><span data-stu-id="8133c-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="8133c-109">Um depurador é a primeira opção para diagnosticar problemas funcionais que podem ser facilmente reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="8133c-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="8133c-110">Registro em log e rastreamento</span><span class="sxs-lookup"><span data-stu-id="8133c-110">Logging and tracing</span></span>

<span data-ttu-id="8133c-111">O [registro em log e o rastreamento](logging-tracing.md) são técnicas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="8133c-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="8133c-112">Eles se referem ao código de instrumentação para criar arquivos de log.</span><span class="sxs-lookup"><span data-stu-id="8133c-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="8133c-113">Os arquivos registram os detalhes do que um programa faz.</span><span class="sxs-lookup"><span data-stu-id="8133c-113">The files record the details of what a program does.</span></span> <span data-ttu-id="8133c-114">Esses detalhes podem ser usados para diagnosticar os problemas mais complexos.</span><span class="sxs-lookup"><span data-stu-id="8133c-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="8133c-115">Quando aliados aos carimbos de data/hora, essas técnicas também são valiosas para as investigações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="8133c-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="8133c-116">Teste de unidade</span><span class="sxs-lookup"><span data-stu-id="8133c-116">Unit testing</span></span>

<span data-ttu-id="8133c-117">O [teste de unidade](../testing/index.md) é um componente fundamental da integração e da implantação contínuas de software de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="8133c-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="8133c-118">Os testes de unidade são projetados para fornecer um aviso antecipado quando você interrompe algo.</span><span class="sxs-lookup"><span data-stu-id="8133c-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="collect-diagnostics-in-containers"></a><span data-ttu-id="8133c-119">Coletar diagnósticos em contêineres</span><span class="sxs-lookup"><span data-stu-id="8133c-119">Collect diagnostics in containers</span></span>

<span data-ttu-id="8133c-120">As mesmas ferramentas de diagnóstico usadas em ambientes Linux não-contêineres também podem ser usadas para [coletar diagnósticos em contêineres](diagnostics-in-containers.md).</span><span class="sxs-lookup"><span data-stu-id="8133c-120">The same diagnostics tools that are used in non-containerized Linux environments can also be used to [collect diagnostics in containers](diagnostics-in-containers.md).</span></span> <span data-ttu-id="8133c-121">Há apenas algumas alterações de uso necessárias para garantir que as ferramentas funcionem em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="8133c-121">There are just a few usage changes needed to make sure the tools work in a Docker container.</span></span>

## <a name="debug-linux-dumps"></a><span data-ttu-id="8133c-122">Depurar despejos do Linux</span><span class="sxs-lookup"><span data-stu-id="8133c-122">Debug Linux dumps</span></span>

<span data-ttu-id="8133c-123">[Depurar despejos do Linux](debug-linux-dumps.md) explica como coletar e analisar despejos no Linux.</span><span class="sxs-lookup"><span data-stu-id="8133c-123">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="8133c-124">Ferramentas globais de diagnóstico do .NET Core</span><span class="sxs-lookup"><span data-stu-id="8133c-124">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="8133c-125">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="8133c-125">dotnet-counters</span></span>

<span data-ttu-id="8133c-126">[dotnet-os contadores](dotnet-counters.md) são uma ferramenta de monitoramento de desempenho para a investigação de desempenho e monitoramento de integridade de primeiro nível.</span><span class="sxs-lookup"><span data-stu-id="8133c-126">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="8133c-127">Ele observa os valores do contador de desempenho publicados por meio da <xref:System.Diagnostics.Tracing.EventCounter> API.</span><span class="sxs-lookup"><span data-stu-id="8133c-127">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="8133c-128">Por exemplo, você pode monitorar rapidamente coisas como o uso da CPU ou a taxa de exceções que estão sendo geradas em seu aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8133c-128">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="8133c-129">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="8133c-129">dotnet-dump</span></span>

<span data-ttu-id="8133c-130">A ferramenta [dotnet-dump](dotnet-dump.md) é uma maneira de coletar e analisar despejos do Windows e do Linux Core sem um depurador nativo.</span><span class="sxs-lookup"><span data-stu-id="8133c-130">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="8133c-131">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="8133c-131">dotnet-gcdump</span></span>

<span data-ttu-id="8133c-132">A ferramenta [dotnet-gcdump](dotnet-gcdump.md) é uma maneira de coletar despejos de GC (coletor de lixo) de processos do .net em tempo real.</span><span class="sxs-lookup"><span data-stu-id="8133c-132">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="8133c-133">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="8133c-133">dotnet-trace</span></span>

<span data-ttu-id="8133c-134">O .NET Core inclui o que é chamado de `EventPipe` por meio do qual os dados de diagnóstico são expostos.</span><span class="sxs-lookup"><span data-stu-id="8133c-134">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="8133c-135">A ferramenta [dotnet-Trace](dotnet-trace.md) permite que você consuma dados de criação de perfil interessantes de seu aplicativo que podem ajudar em cenários em que você precisa ter a causa raiz dos aplicativos em execução lenta.</span><span class="sxs-lookup"><span data-stu-id="8133c-135">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="8133c-136">dotnet-symbol</span><span class="sxs-lookup"><span data-stu-id="8133c-136">dotnet-symbol</span></span>

<span data-ttu-id="8133c-137">[dotnet-Symbol](dotnet-symbol.md) baixa arquivos (símbolos, DAC/DBI, arquivos de host, etc.) necessários para abrir um dump principal ou minidespejo.</span><span class="sxs-lookup"><span data-stu-id="8133c-137">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="8133c-138">Use essa ferramenta se precisar de símbolos e módulos para depurar um arquivo de despejo capturado em um computador diferente.</span><span class="sxs-lookup"><span data-stu-id="8133c-138">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="8133c-139">dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="8133c-139">dotnet-sos</span></span>

<span data-ttu-id="8133c-140">[dotnet-SOS](dotnet-sos.md) é usado para instalar a [extensão de depuração SOS](../../framework/tools/sos-dll-sos-debugging-extension.md) no Linux ou MacOS (ou no Windows, se estiver usando ferramentas de depuração mais antigas).</span><span class="sxs-lookup"><span data-stu-id="8133c-140">[dotnet-sos](dotnet-sos.md) is used to install the [SOS debugging extension](../../framework/tools/sos-dll-sos-debugging-extension.md) on Linux or MacOS (or on Windows if using older debugging tools).</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="8133c-141">Tutoriais de diagnóstico do .NET Core</span><span class="sxs-lookup"><span data-stu-id="8133c-141">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="8133c-142">Depurar um vazamento de memória</span><span class="sxs-lookup"><span data-stu-id="8133c-142">Debug a memory leak</span></span>

<span data-ttu-id="8133c-143">[Tutorial: Depurar um vazamento de memória](debug-memory-leak.md) percorre a localização de um vazamento de memória.</span><span class="sxs-lookup"><span data-stu-id="8133c-143">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="8133c-144">A ferramenta [dotnet-Counters](dotnet-counters.md) é usada para confirmar o vazamento e a ferramenta [dotnet-dump](dotnet-dump.md) é usada para diagnosticar o vazamento.</span><span class="sxs-lookup"><span data-stu-id="8133c-144">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="8133c-145">Depurar alto uso da CPU</span><span class="sxs-lookup"><span data-stu-id="8133c-145">Debug high CPU usage</span></span>

<span data-ttu-id="8133c-146">[Tutorial: Depurar alto uso da CPU](debug-highcpu.md) orienta você na investigação de alto uso da CPU.</span><span class="sxs-lookup"><span data-stu-id="8133c-146">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="8133c-147">Ele usa a ferramenta [dotnet-Counters](dotnet-counters.md) para confirmar o alto uso da CPU.</span><span class="sxs-lookup"><span data-stu-id="8133c-147">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="8133c-148">Em seguida, ele orienta você pelo uso [do trace for performance Analysis Utility ( `dotnet-trace` ) ou do](dotnet-trace.md) Linux `perf` para coletar e exibir o perfil de uso da CPU.</span><span class="sxs-lookup"><span data-stu-id="8133c-148">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="8133c-149">Depurar deadlock</span><span class="sxs-lookup"><span data-stu-id="8133c-149">Debug deadlock</span></span>

<span data-ttu-id="8133c-150">[Tutorial: debug deadlock](debug-deadlock.md) mostra como usar a ferramenta [dotnet-dump](dotnet-dump.md) para investigar threads e bloqueios.</span><span class="sxs-lookup"><span data-stu-id="8133c-150">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>
