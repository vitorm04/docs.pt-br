---
title: Depuração do deadlock-.NET Core
description: Um tutorial que orienta você pela depuração de um problema de bloqueio no .NET Core.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: d9a9328b376de5886d22ca7315f6d7d9d73fd2c2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538690"
---
# <a name="debug-a-deadlock-in-net-core"></a><span data-ttu-id="0f60c-103">Depurar um deadlock no .NET Core</span><span class="sxs-lookup"><span data-stu-id="0f60c-103">Debug a deadlock in .NET Core</span></span>

<span data-ttu-id="0f60c-104">**Este artigo aplica-se a: ✔️** SDK do .net Core 3,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="0f60c-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="0f60c-105">Neste tutorial, você aprenderá a depurar um cenário de deadlock.</span><span class="sxs-lookup"><span data-stu-id="0f60c-105">In this tutorial, you'll learn how to debug a deadlock scenario.</span></span> <span data-ttu-id="0f60c-106">Usando o exemplo fornecido ASP.NET Core repositório de código-fonte do [aplicativo Web](/samples/dotnet/samples/diagnostic-scenarios) , você pode causar um deadlock intencionalmente.</span><span class="sxs-lookup"><span data-stu-id="0f60c-106">Using the provided example [ASP.NET Core web app](/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="0f60c-107">O ponto de extremidade passará por uma falha e acumulação de threads.</span><span class="sxs-lookup"><span data-stu-id="0f60c-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="0f60c-108">Você aprenderá como é possível usar várias ferramentas para analisar o problema, como dumps principais, análise de despejo principal e rastreamento de processos.</span><span class="sxs-lookup"><span data-stu-id="0f60c-108">You'll learn how you can use various tools to analyze the problem, such as core dumps, core dump analysis, and process tracing.</span></span>

<span data-ttu-id="0f60c-109">Neste tutorial, você irá:</span><span class="sxs-lookup"><span data-stu-id="0f60c-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="0f60c-110">Investigar um aplicativo suspenso</span><span class="sxs-lookup"><span data-stu-id="0f60c-110">Investigate an app hang</span></span>
> - <span data-ttu-id="0f60c-111">Gerar um arquivo de despejo principal</span><span class="sxs-lookup"><span data-stu-id="0f60c-111">Generate a core dump file</span></span>
> - <span data-ttu-id="0f60c-112">Analisar threads de processo no arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="0f60c-112">Analyze process threads in the dump file</span></span>
> - <span data-ttu-id="0f60c-113">Analisar transchamadas e blocos de sincronização</span><span class="sxs-lookup"><span data-stu-id="0f60c-113">Analyze callstacks and sync blocks</span></span>
> - <span data-ttu-id="0f60c-114">Diagnosticar e resolver um deadlock</span><span class="sxs-lookup"><span data-stu-id="0f60c-114">Diagnose and solve a deadlock</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0f60c-115">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0f60c-115">Prerequisites</span></span>

<span data-ttu-id="0f60c-116">O tutorial usa:</span><span class="sxs-lookup"><span data-stu-id="0f60c-116">The tutorial uses:</span></span>

- <span data-ttu-id="0f60c-117">[SDK do .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core) ou uma versão posterior</span><span class="sxs-lookup"><span data-stu-id="0f60c-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version</span></span>
- <span data-ttu-id="0f60c-118">[Exemplo de destino de depuração – aplicativo Web](/samples/dotnet/samples/diagnostic-scenarios) para disparar o cenário</span><span class="sxs-lookup"><span data-stu-id="0f60c-118">[Sample debug target - web app](/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario</span></span>
- <span data-ttu-id="0f60c-119">[dotnet-rastrear](dotnet-trace.md) para listar processos</span><span class="sxs-lookup"><span data-stu-id="0f60c-119">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="0f60c-120">[dotnet-despejo](dotnet-dump.md) para coletar e analisar um arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="0f60c-120">[dotnet-dump](dotnet-dump.md) to collect, and analyze a dump file</span></span>

## <a name="core-dump-generation"></a><span data-ttu-id="0f60c-121">Geração de despejo principal</span><span class="sxs-lookup"><span data-stu-id="0f60c-121">Core dump generation</span></span>

<span data-ttu-id="0f60c-122">Para investigar a falta de resposta do aplicativo, um despejo principal ou despejo de memória permite inspecionar o estado de seus threads e os possíveis bloqueios que podem ter problemas de contenção.</span><span class="sxs-lookup"><span data-stu-id="0f60c-122">To investigate application unresponsiveness, a core dump or memory dump allows you to inspect the state of its threads and any possible locks that may have contention issues.</span></span> <span data-ttu-id="0f60c-123">Execute o aplicativo de [depuração de exemplo](/samples/dotnet/samples/diagnostic-scenarios) usando o seguinte comando no diretório raiz de exemplo:</span><span class="sxs-lookup"><span data-stu-id="0f60c-123">Run the [sample debug](/samples/dotnet/samples/diagnostic-scenarios) application using the following command from the sample root directory:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="0f60c-124">Para localizar a ID do processo, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="0f60c-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="0f60c-125">Anote a ID do processo da saída do comando.</span><span class="sxs-lookup"><span data-stu-id="0f60c-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="0f60c-126">Nossa ID de processo era `4807` , mas a sua será diferente.</span><span class="sxs-lookup"><span data-stu-id="0f60c-126">Our process ID was `4807`, but yours will be different.</span></span> <span data-ttu-id="0f60c-127">Navegue até a URL a seguir, que é um ponto de extremidade de API no site de exemplo:</span><span class="sxs-lookup"><span data-stu-id="0f60c-127">Navigate to the following URL, which is an API endpoint on the sample site:</span></span>

`https://localhost:5001/api/diagscenario/deadlock`

<span data-ttu-id="0f60c-128">A solicitação de API para o site será travada e não responderá.</span><span class="sxs-lookup"><span data-stu-id="0f60c-128">The API request to the site will hang and not respond.</span></span> <span data-ttu-id="0f60c-129">Deixe a solicitação ser executada por cerca de 10-15 segundos.</span><span class="sxs-lookup"><span data-stu-id="0f60c-129">Let the request run for about 10-15 seconds.</span></span> <span data-ttu-id="0f60c-130">Em seguida, crie o dump principal usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="0f60c-130">Then create the core dump using the following command:</span></span>

### <a name="linux"></a>[<span data-ttu-id="0f60c-131">Linux</span><span class="sxs-lookup"><span data-stu-id="0f60c-131">Linux</span></span>](#tab/linux)

```bash
sudo dotnet-dump collect -p 4807
```

### <a name="windows"></a>[<span data-ttu-id="0f60c-132">Windows</span><span class="sxs-lookup"><span data-stu-id="0f60c-132">Windows</span></span>](#tab/windows)

```console
dotnet-dump collect -p 4807
```

---

## <a name="analyze-the-core-dump"></a><span data-ttu-id="0f60c-133">Analisar o dump principal</span><span class="sxs-lookup"><span data-stu-id="0f60c-133">Analyze the core dump</span></span>

<span data-ttu-id="0f60c-134">Para iniciar a análise de despejo principal, abra o dump principal usando o `dotnet-dump analyze` comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="0f60c-134">To start the core dump analysis, open the core dump using the following `dotnet-dump analyze` command.</span></span> <span data-ttu-id="0f60c-135">O argumento é o caminho para o arquivo de despejo principal que foi coletado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0f60c-135">The argument is the path to the core dump file that was collected earlier.</span></span>

```dotnetcli
dotnet-dump analyze  ~/.dotnet/tools/core_20190513_143916
```

<span data-ttu-id="0f60c-136">Como você está olhando para um potencial travamento, você deseja uma sensação geral para a atividade thread no processo.</span><span class="sxs-lookup"><span data-stu-id="0f60c-136">Since you're looking at a potential hang, you want an overall feel for the thread activity in the process.</span></span> <span data-ttu-id="0f60c-137">Você pode usar o `threads` comando conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="0f60c-137">You can use the `threads` command as shown below:</span></span>

```console
> threads
*0 0x1DBFF (121855)
 1 0x1DC01 (121857)
 2 0x1DC02 (121858)
 3 0x1DC03 (121859)
 4 0x1DC04 (121860)
 5 0x1DC05 (121861)
 6 0x1DC06 (121862)
 7 0x1DC07 (121863)
 8 0x1DC08 (121864)
 9 0x1DC09 (121865)
 10 0x1DC0A (121866)
 11 0x1DC0D (121869)
 12 0x1DC0E (121870)
 13 0x1DC10 (121872)
 14 0x1DC11 (121873)
 15 0x1DC12 (121874)
 16 0x1DC13 (121875)
 17 0x1DC14 (121876)
 18 0x1DC15 (121877)
 19 0x1DC1C (121884)
 20 0x1DC1D (121885)
 21 0x1DC1E (121886)
 22 0x1DC21 (121889)
 23 0x1DC22 (121890)
 24 0x1DC23 (121891)
 25 0x1DC24 (121892)
 26 0x1DC25 (121893)
...
...
 317 0x1DD48 (122184)
 318 0x1DD49 (122185)
 319 0x1DD4A (122186)
 320 0x1DD4B (122187)
 321 0x1DD4C (122188)
 ```

<span data-ttu-id="0f60c-138">A saída mostra todos os threads em execução no momento no processo com a ID do thread do depurador e a ID do thread do sistema operacional associados.</span><span class="sxs-lookup"><span data-stu-id="0f60c-138">The output shows all the threads currently running in the process with their associated debugger thread ID and operating system thread ID.</span></span> <span data-ttu-id="0f60c-139">Com base na saída, há mais de 300 threads.</span><span class="sxs-lookup"><span data-stu-id="0f60c-139">Based on the output, there are over 300 threads.</span></span>

<span data-ttu-id="0f60c-140">A próxima etapa é entender melhor o que os threads estão fazendo atualmente ao obter a pilha de chamadas de cada thread.</span><span class="sxs-lookup"><span data-stu-id="0f60c-140">The next step is to get a better understanding of what the threads are currently doing by getting each thread's callstack.</span></span> <span data-ttu-id="0f60c-141">O `clrstack` comando pode ser usado para gerar pilhas de chamadas.</span><span class="sxs-lookup"><span data-stu-id="0f60c-141">The `clrstack` command can be used to output callstacks.</span></span> <span data-ttu-id="0f60c-142">Ele pode gerar uma saída de uma única pilha de chamadas ou todas as chamadas.</span><span class="sxs-lookup"><span data-stu-id="0f60c-142">It can either output a single callstack or all the callstacks.</span></span> <span data-ttu-id="0f60c-143">Use o seguinte comando para gerar todas as chamadas para todos os threads no processo:</span><span class="sxs-lookup"><span data-stu-id="0f60c-143">Use the following command to output all the callstacks for all the threads in the process:</span></span>

```console
clrstack -all
```

<span data-ttu-id="0f60c-144">Uma parte representativa da saída é semelhante a:</span><span class="sxs-lookup"><span data-stu-id="0f60c-144">A representative portion of the output looks like:</span></span>

```console
  ...
  ...
  ...
        Child SP               IP Call Site
00007F2AE37B5680 00007f305abc6360 [GCFrame: 00007f2ae37b5680]
00007F2AE37B5770 00007f305abc6360 [GCFrame: 00007f2ae37b5770]
00007F2AE37B57D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae37b57d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE37B5920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE37B5950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE37B5CA0 00007f30593044af [GCFrame: 00007f2ae37b5ca0]
00007F2AE37B5D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae37b5d70]
OS Thread Id: 0x1dc82
        Child SP               IP Call Site
00007F2AE2FB4680 00007f305abc6360 [GCFrame: 00007f2ae2fb4680]
00007F2AE2FB4770 00007f305abc6360 [GCFrame: 00007f2ae2fb4770]
00007F2AE2FB47D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae2fb47d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE2FB4920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE2FB4950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE2FB4CA0 00007f30593044af [GCFrame: 00007f2ae2fb4ca0]
00007F2AE2FB4D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae2fb4d70]
OS Thread Id: 0x1dc83
        Child SP               IP Call Site
00007F2AE27B3680 00007f305abc6360 [GCFrame: 00007f2ae27b3680]
00007F2AE27B3770 00007f305abc6360 [GCFrame: 00007f2ae27b3770]
00007F2AE27B37D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae27b37d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE27B3920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE27B3950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE27B3CA0 00007f30593044af [GCFrame: 00007f2ae27b3ca0]
00007F2AE27B3D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae27b3d70]
OS Thread Id: 0x1dc84
        Child SP               IP Call Site
00007F2AE1FB2680 00007f305abc6360 [GCFrame: 00007f2ae1fb2680]
00007F2AE1FB2770 00007f305abc6360 [GCFrame: 00007f2ae1fb2770]
00007F2AE1FB27D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae1fb27d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE1FB2920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE1FB2950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE1FB2CA0 00007f30593044af [GCFrame: 00007f2ae1fb2ca0]
00007F2AE1FB2D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae1fb2d70]
OS Thread Id: 0x1dc85
        Child SP               IP Call Site
00007F2AE17B1680 00007f305abc6360 [GCFrame: 00007f2ae17b1680]
00007F2AE17B1770 00007f305abc6360 [GCFrame: 00007f2ae17b1770]
00007F2AE17B17D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae17b17d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE17B1920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE17B1950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE17B1CA0 00007f30593044af [GCFrame: 00007f2ae17b1ca0]
00007F2AE17B1D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae17b1d70]
OS Thread Id: 0x1dc86
        Child SP               IP Call Site
00007F2AE0FB0680 00007f305abc6360 [GCFrame: 00007f2ae0fb0680]
00007F2AE0FB0770 00007f305abc6360 [GCFrame: 00007f2ae0fb0770]
00007F2AE0FB07D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae0fb07d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE0FB0920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE0FB0950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE0FB0CA0 00007f30593044af [GCFrame: 00007f2ae0fb0ca0]
00007F2AE0FB0D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae0fb0d70]
OS Thread Id: 0x1dc87
        Child SP               IP Call Site
00007F2AE07AF680 00007f305abc6360 [GCFrame: 00007f2ae07af680]
00007F2AE07AF770 00007f305abc6360 [GCFrame: 00007f2ae07af770]
00007F2AE07AF7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae07af7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE07AF920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE07AF950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE07AFCA0 00007f30593044af [GCFrame: 00007f2ae07afca0]
00007F2AE07AFD70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae07afd70]
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
...
...
```

<span data-ttu-id="0f60c-145">Observar as chamadas de pilha para todos os mais de 300 threads mostra um padrão em que a maioria dos threads compartilha uma pilha de chamadas comum:</span><span class="sxs-lookup"><span data-stu-id="0f60c-145">Observing the callstacks for all 300+ threads shows a pattern where a majority of the threads share a common callstack:</span></span>

```console
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
```

<span data-ttu-id="0f60c-146">A pilha de chamadas parece mostrar que a solicitação chegou ao nosso método de deadlock que, por sua vez, faz uma chamada para `Monitor.ReliableEnter` .</span><span class="sxs-lookup"><span data-stu-id="0f60c-146">The callstack seems to show that the request arrived in our deadlock method that in turn makes a call to `Monitor.ReliableEnter`.</span></span> <span data-ttu-id="0f60c-147">Esse método indica que os threads estão tentando inserir um bloqueio de monitor.</span><span class="sxs-lookup"><span data-stu-id="0f60c-147">This method indicates that the threads are trying to enter a monitor lock.</span></span> <span data-ttu-id="0f60c-148">Eles estão aguardando a disponibilidade do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0f60c-148">They're waiting on the availability of the lock.</span></span> <span data-ttu-id="0f60c-149">Provavelmente, ele está bloqueado por um thread diferente.</span><span class="sxs-lookup"><span data-stu-id="0f60c-149">It's likely locked by a different thread.</span></span>

<span data-ttu-id="0f60c-150">A próxima etapa é descobrir qual thread está realmente mantendo o bloqueio de monitor.</span><span class="sxs-lookup"><span data-stu-id="0f60c-150">The next step then is to find out which thread is actually holding the monitor lock.</span></span> <span data-ttu-id="0f60c-151">Como os monitores normalmente armazenam informações de bloqueio na tabela de blocos de sincronização, podemos usar o `syncblk` comando para obter mais informações:</span><span class="sxs-lookup"><span data-stu-id="0f60c-151">Since monitors typically store lock information in the sync block table, we can use the `syncblk` command to get more information:</span></span>

```console
> syncblk
Index         SyncBlock MonitorHeld Recursion Owning Thread Info          SyncBlock Owner
   43 00000246E51268B8          603         1 0000024B713F4E30 5634  28   00000249654b14c0 System.Object
   44 00000246E5126908            3         1 0000024B713F47E0 51d4  29   00000249654b14d8 System.Object
-----------------------------
Total           344
CCW             1
RCW             2
ComClassFactory 0
Free            0
```

<span data-ttu-id="0f60c-152">As duas colunas interessantes são **MonitorHeld** e **informações de thread de propriedade**.</span><span class="sxs-lookup"><span data-stu-id="0f60c-152">The two interesting columns are **MonitorHeld** and **Owning Thread Info**.</span></span> <span data-ttu-id="0f60c-153">A coluna **MonitorHeld** mostra se um bloqueio de monitor é adquirido por um thread e o número de threads em espera.</span><span class="sxs-lookup"><span data-stu-id="0f60c-153">The **MonitorHeld** column shows whether a monitor lock is acquired by a thread and the number of waiting threads.</span></span> <span data-ttu-id="0f60c-154">A coluna **informações de thread de propriedade** mostra qual thread possui atualmente o bloqueio de monitor.</span><span class="sxs-lookup"><span data-stu-id="0f60c-154">The **Owning Thread Info** column shows which thread currently owns the monitor lock.</span></span> <span data-ttu-id="0f60c-155">As informações de thread têm três Subcolunas diferentes.</span><span class="sxs-lookup"><span data-stu-id="0f60c-155">The thread info has three different subcolumns.</span></span> <span data-ttu-id="0f60c-156">A segunda subcoluna mostra a ID do thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="0f60c-156">The second subcolumn shows operating system thread ID.</span></span>

<span data-ttu-id="0f60c-157">Neste ponto, sabemos que dois threads diferentes (0x5634 e 0x51d4) mantêm um bloqueio de monitor.</span><span class="sxs-lookup"><span data-stu-id="0f60c-157">At this point, we know two different threads (0x5634 and 0x51d4) hold a monitor lock.</span></span> <span data-ttu-id="0f60c-158">A próxima etapa é dar uma olhada no que esses threads estão fazendo.</span><span class="sxs-lookup"><span data-stu-id="0f60c-158">The next step is to take a look at what those threads are doing.</span></span> <span data-ttu-id="0f60c-159">Precisamos verificar se eles estão presos indefinidamente mantendo o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0f60c-159">We need to check if they're stuck indefinitely holding the lock.</span></span> <span data-ttu-id="0f60c-160">Vamos usar os `setthread` comandos e `clrstack` para alternar para cada um dos threads e exibir as pilhas de chamadas.</span><span class="sxs-lookup"><span data-stu-id="0f60c-160">Let's use the `setthread` and `clrstack` commands to switch to each of the threads and display the callstacks.</span></span>

<span data-ttu-id="0f60c-161">Para examinar o primeiro thread, execute o `setthread` comando e localize o índice do thread 0x5634 (nosso índice foi 28).</span><span class="sxs-lookup"><span data-stu-id="0f60c-161">To look at the first thread, run the `setthread` command, and find the index of the 0x5634 thread (our index was 28).</span></span> <span data-ttu-id="0f60c-162">A função de deadlock está aguardando para adquirir um bloqueio, mas ele já possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0f60c-162">The deadlock function is waiting to acquire a lock, but it already owns the lock.</span></span> <span data-ttu-id="0f60c-163">Ele está em deadlock aguardando o bloqueio que ele já contém.</span><span class="sxs-lookup"><span data-stu-id="0f60c-163">It's in deadlock waiting for the lock it already holds.</span></span>

```console
> setthread 28
> clrstack
OS Thread Id: 0x5634 (28)
        Child SP               IP Call Site
0000004E46AFEAA8 00007fff43a5cbc4 [GCFrame: 0000004e46afeaa8]
0000004E46AFEC18 00007fff43a5cbc4 [GCFrame: 0000004e46afec18]
0000004E46AFEC68 00007fff43a5cbc4 [HelperMethodFrame_1OBJ: 0000004e46afec68] System.Threading.Monitor.Enter(System.Object)
0000004E46AFEDC0 00007FFE5EAF9C80 testwebapi.Controllers.DiagScenarioController.DeadlockFunc() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 58]
0000004E46AFEE30 00007FFE5EAF9B8C testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_0() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 26]
0000004E46AFEE80 00007FFEBB251A5B System.Threading.ThreadHelper.ThreadStart_Context(System.Object) [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 44]
0000004E46AFEEB0 00007FFE5EAEEEEC System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/_/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
0000004E46AFEF20 00007FFEBB234EAB System.Threading.ThreadHelper.ThreadStart() [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 93]
0000004E46AFF138 00007ffebdcc6b63 [GCFrame: 0000004e46aff138]
0000004E46AFF3A0 00007ffebdcc6b63 [DebuggerU2MCatchHandlerFrame: 0000004e46aff3a0]
```

<span data-ttu-id="0f60c-164">O segundo thread é semelhante.</span><span class="sxs-lookup"><span data-stu-id="0f60c-164">The second thread is similar.</span></span> <span data-ttu-id="0f60c-165">Também está tentando adquirir um bloqueio que já possui.</span><span class="sxs-lookup"><span data-stu-id="0f60c-165">It's also trying to acquire a lock that it already owns.</span></span> <span data-ttu-id="0f60c-166">Os mais de 300 threads que estão aguardando provavelmente também aguardam um dos bloqueios que causaram o deadlock.</span><span class="sxs-lookup"><span data-stu-id="0f60c-166">The remaining 300+ threads that are all waiting are most likely also waiting on one of the locks that caused the deadlock.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f60c-167">Confira também</span><span class="sxs-lookup"><span data-stu-id="0f60c-167">See also</span></span>

- <span data-ttu-id="0f60c-168">[dotnet-rastrear](dotnet-trace.md) para listar processos</span><span class="sxs-lookup"><span data-stu-id="0f60c-168">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="0f60c-169">[dotnet-contadores](dotnet-counters.md) para verificar o uso de memória gerenciada</span><span class="sxs-lookup"><span data-stu-id="0f60c-169">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="0f60c-170">[dotnet-despejo](dotnet-dump.md) para coletar e analisar um arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="0f60c-170">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="0f60c-171">dotnet/diagnóstico</span><span class="sxs-lookup"><span data-stu-id="0f60c-171">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="0f60c-172">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="0f60c-172">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0f60c-173">Quais ferramentas de diagnóstico estão disponíveis no .NET Core</span><span class="sxs-lookup"><span data-stu-id="0f60c-173">What diagnostic tools are available in .NET Core</span></span>](index.md)
