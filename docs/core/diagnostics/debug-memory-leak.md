---
title: Depurar um tutorial de vazamento de memória
description: Saiba como depurar um vazamento de memória no .NET Core.
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: d47992bab9dab64cf7f88ff679eef407dd891b5a
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021364"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a><span data-ttu-id="4cf80-103">Tutorial: Depurar um vazamento de memória no .NET Core</span><span class="sxs-lookup"><span data-stu-id="4cf80-103">Tutorial: Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="4cf80-104">**Este artigo se aplica a:** ✔️ .NET Core 3.0 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="4cf80-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="4cf80-105">Este tutorial demonstra as ferramentas para analisar um vazamento de memória .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4cf80-105">This tutorial demonstrates the tools to analyze a .NET Core memory leak.</span></span>

<span data-ttu-id="4cf80-106">Este tutorial usa um aplicativo de exemplo, que foi projetado para vazar intencionalmente a memória.</span><span class="sxs-lookup"><span data-stu-id="4cf80-106">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="4cf80-107">A amostra é fornecida como um exercício.</span><span class="sxs-lookup"><span data-stu-id="4cf80-107">The sample is provided as an exercise.</span></span> <span data-ttu-id="4cf80-108">Você pode analisar um aplicativo que está vazando memória involuntariamente também.</span><span class="sxs-lookup"><span data-stu-id="4cf80-108">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="4cf80-109">Neste tutorial, você irá:</span><span class="sxs-lookup"><span data-stu-id="4cf80-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="4cf80-110">Examine o uso gerenciado da memória com [contadores de dotnet](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="4cf80-110">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="4cf80-111">Gerar um arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="4cf80-111">Generate a dump file.</span></span>
> - <span data-ttu-id="4cf80-112">Analise o uso da memória usando o arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="4cf80-112">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4cf80-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4cf80-113">Prerequisites</span></span>

<span data-ttu-id="4cf80-114">O tutorial usa:</span><span class="sxs-lookup"><span data-stu-id="4cf80-114">The tutorial uses:</span></span>

- <span data-ttu-id="4cf80-115">[SDK do .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core) ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="4cf80-115">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="4cf80-116">[dotnet-trace](dotnet-trace.md) para processos de lista.</span><span class="sxs-lookup"><span data-stu-id="4cf80-116">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
- <span data-ttu-id="4cf80-117">[contadores dotnet](dotnet-counters.md) para verificar o uso gerenciado da memória.</span><span class="sxs-lookup"><span data-stu-id="4cf80-117">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="4cf80-118">[dotnet-dump](dotnet-dump.md) para coletar e analisar um arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="4cf80-118">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="4cf80-119">Um aplicativo [de destino de depuração de amostra](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) para diagnosticar.</span><span class="sxs-lookup"><span data-stu-id="4cf80-119">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="4cf80-120">O tutorial pressupõe que a amostra e as ferramentas estão instaladas e prontas para uso.</span><span class="sxs-lookup"><span data-stu-id="4cf80-120">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="4cf80-121">Examine o uso gerenciado da memória</span><span class="sxs-lookup"><span data-stu-id="4cf80-121">Examine managed memory usage</span></span>

<span data-ttu-id="4cf80-122">Antes de começar a coletar dados de diagnóstico para nos ajudar a criar esse cenário, você precisa ter certeza de que está realmente vendo um vazamento de memória (crescimento de memória).</span><span class="sxs-lookup"><span data-stu-id="4cf80-122">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="4cf80-123">Você pode usar a ferramenta [dotnet-counters](dotnet-counters.md) para confirmar isso.</span><span class="sxs-lookup"><span data-stu-id="4cf80-123">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="4cf80-124">Abra uma janela do console e navegue até o diretório onde você baixou e descompactou o [alvo de depuração de amostra](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span><span class="sxs-lookup"><span data-stu-id="4cf80-124">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="4cf80-125">Executar o alvo:</span><span class="sxs-lookup"><span data-stu-id="4cf80-125">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="4cf80-126">A partir de um console separado, encontre o ID do processo usando a ferramenta [dotnet-trace:](dotnet-trace.md)</span><span class="sxs-lookup"><span data-stu-id="4cf80-126">From a separate console, find the process ID using the [dotnet-trace](dotnet-trace.md) tool:</span></span>

```console
dotnet-trace ps
```

<span data-ttu-id="4cf80-127">A saída deve ser semelhante a:</span><span class="sxs-lookup"><span data-stu-id="4cf80-127">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="4cf80-128">Agora, verifique o uso gerenciado da memória com a ferramenta [dotnet-counters.](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="4cf80-128">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="4cf80-129">O `--refresh-interval` especifica o número de segundos entre as atualizações:</span><span class="sxs-lookup"><span data-stu-id="4cf80-129">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="4cf80-130">A saída ao vivo deve ser semelhante a:</span><span class="sxs-lookup"><span data-stu-id="4cf80-130">The live output should be similar to:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

<span data-ttu-id="4cf80-131">Focando nesta linha:</span><span class="sxs-lookup"><span data-stu-id="4cf80-131">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="4cf80-132">Você pode ver que a memória de pilha gerenciada é de 4 MB logo após a inicialização.</span><span class="sxs-lookup"><span data-stu-id="4cf80-132">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="4cf80-133">Agora, aperte `http://localhost:5000/api/diagscenario/memleak/20000`a URL .</span><span class="sxs-lookup"><span data-stu-id="4cf80-133">Now, hit the URL `http://localhost:5000/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="4cf80-134">Observe que o uso da memória cresceu para 30 MB.</span><span class="sxs-lookup"><span data-stu-id="4cf80-134">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="4cf80-135">Observando o uso da memória, você pode dizer com segurança que a memória está crescendo ou vazando.</span><span class="sxs-lookup"><span data-stu-id="4cf80-135">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="4cf80-136">O próximo passo é coletar os dados certos para análise de memória.</span><span class="sxs-lookup"><span data-stu-id="4cf80-136">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="4cf80-137">Gerar despejo de memória</span><span class="sxs-lookup"><span data-stu-id="4cf80-137">Generate memory dump</span></span>

<span data-ttu-id="4cf80-138">Ao analisar possíveis vazamentos de memória, você precisa acessar o monte de memória do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4cf80-138">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="4cf80-139">Então você pode analisar o conteúdo da memória.</span><span class="sxs-lookup"><span data-stu-id="4cf80-139">Then you can analyze the memory contents.</span></span> <span data-ttu-id="4cf80-140">Olhando para as relações entre objetos, você cria teorias sobre por que a memória não está sendo liberada.</span><span class="sxs-lookup"><span data-stu-id="4cf80-140">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="4cf80-141">Uma fonte de dados de diagnóstico comum é um despejo de memória no Windows ou o despejo de núcleo equivalente no Linux.</span><span class="sxs-lookup"><span data-stu-id="4cf80-141">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="4cf80-142">Para gerar um dump de um aplicativo .NET Core, você pode usar a ferramenta [dotnet-dump).](dotnet-dump.md)</span><span class="sxs-lookup"><span data-stu-id="4cf80-142">To generate a dump of a .NET Core application, you can use the [dotnet-dump)](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="4cf80-143">Usando o [destino de depuração de amostra](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) iniciado anteriormente, execute o seguinte comando para gerar um dump do núcleo do Linux:</span><span class="sxs-lookup"><span data-stu-id="4cf80-143">Using the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="4cf80-144">O resultado é um despejo de núcleo localizado na mesma pasta.</span><span class="sxs-lookup"><span data-stu-id="4cf80-144">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="4cf80-145">Reiniciar o processo de falha</span><span class="sxs-lookup"><span data-stu-id="4cf80-145">Restart the failed process</span></span>

<span data-ttu-id="4cf80-146">Uma vez que o despejo é coletado, você deve ter informações suficientes para diagnosticar o processo falho.</span><span class="sxs-lookup"><span data-stu-id="4cf80-146">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="4cf80-147">Se o processo de falha está sendo executado em um servidor de produção, agora é o momento ideal para remediação a curto prazo, reiniciando o processo.</span><span class="sxs-lookup"><span data-stu-id="4cf80-147">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="4cf80-148">Neste tutorial, você está pronto com o [destino de depuração Sample](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) e você pode fechá-lo.</span><span class="sxs-lookup"><span data-stu-id="4cf80-148">In this tutorial, you're now done with the [Sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="4cf80-149">Navegue até o terminal que `Control-C`iniciou o servidor e pressione .</span><span class="sxs-lookup"><span data-stu-id="4cf80-149">Navigate to the terminal that started the server and press `Control-C`.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="4cf80-150">Analisar o despejo do núcleo</span><span class="sxs-lookup"><span data-stu-id="4cf80-150">Analyze the core dump</span></span>

<span data-ttu-id="4cf80-151">Agora que você tem um dump de núcleo gerado, use a ferramenta [dotnet-dump](dotnet-dump.md) para analisar o dump:</span><span class="sxs-lookup"><span data-stu-id="4cf80-151">Now that you have a core dump generated, use the [dotnet-dump](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="4cf80-152">Onde `core_20190430_185145` está o nome do despejo do núcleo que você quer analisar.</span><span class="sxs-lookup"><span data-stu-id="4cf80-152">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="4cf80-153">Se você vir um erro reclamando que *libdl.so* não pode ser encontrado, você pode ter que instalar o pacote *libc6-dev.*</span><span class="sxs-lookup"><span data-stu-id="4cf80-153">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="4cf80-154">Para saber mais, confira [Pré-requisitos para o .NET Core no Linux](../install/dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="4cf80-154">For more information, see [Prerequisites for .NET Core on Linux](../install/dependencies.md?pivots=os-linux).</span></span>

<span data-ttu-id="4cf80-155">Você será apresentado com um prompt onde você pode inserir comandos SOS.</span><span class="sxs-lookup"><span data-stu-id="4cf80-155">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="4cf80-156">Geralmente, a primeira coisa que você quer olhar é o estado geral do monte gerenciado:</span><span class="sxs-lookup"><span data-stu-id="4cf80-156">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

<span data-ttu-id="4cf80-157">Aqui você pode ver que `String` `Customer` a maioria dos objetos são ou objetos.</span><span class="sxs-lookup"><span data-stu-id="4cf80-157">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="4cf80-158">Você pode `dumpheap` usar o comando novamente com a tabela de métodos (MT) para obter uma lista de todas as `String` instâncias:</span><span class="sxs-lookup"><span data-stu-id="4cf80-158">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

<span data-ttu-id="4cf80-159">Agora você pode `gcroot` usar `System.String` o comando em uma instância para ver como e por que o objeto está enraizado.</span><span class="sxs-lookup"><span data-stu-id="4cf80-159">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="4cf80-160">Seja paciente porque este comando leva vários minutos com um monte de 30 MB:</span><span class="sxs-lookup"><span data-stu-id="4cf80-160">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

<span data-ttu-id="4cf80-161">Você pode ver `String` que o `Customer` é diretamente mantido pelo `CustomerCache` objeto e indiretamente mantido por um objeto.</span><span class="sxs-lookup"><span data-stu-id="4cf80-161">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="4cf80-162">Você pode continuar despejando objetos para ver que a maioria dos `String` objetos segue um padrão semelhante.</span><span class="sxs-lookup"><span data-stu-id="4cf80-162">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="4cf80-163">Neste ponto, a investigação forneceu informações suficientes para identificar a causa raiz em seu código.</span><span class="sxs-lookup"><span data-stu-id="4cf80-163">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="4cf80-164">Este procedimento geral permite identificar a fonte de grandes vazamentos de memória.</span><span class="sxs-lookup"><span data-stu-id="4cf80-164">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="4cf80-165">Limpar os recursos</span><span class="sxs-lookup"><span data-stu-id="4cf80-165">Clean up resources</span></span>

<span data-ttu-id="4cf80-166">Neste tutorial, você começou um servidor web de exemplo.</span><span class="sxs-lookup"><span data-stu-id="4cf80-166">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="4cf80-167">Este servidor deveria ter sido desligado conforme explicado na seção Reiniciar a seção [de processo com falha.](#restart-the-failed-process)</span><span class="sxs-lookup"><span data-stu-id="4cf80-167">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="4cf80-168">Você também pode excluir o arquivo de despejo que foi criado.</span><span class="sxs-lookup"><span data-stu-id="4cf80-168">You can also delete the dump file that was created.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4cf80-169">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4cf80-169">Next steps</span></span>

<span data-ttu-id="4cf80-170">Parabéns por completar este tutorial.</span><span class="sxs-lookup"><span data-stu-id="4cf80-170">Congratulations on completing this tutorial.</span></span>

<span data-ttu-id="4cf80-171">Ainda estamos publicando mais tutoriais de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="4cf80-171">We're still publishing more diagnostic tutorials.</span></span> <span data-ttu-id="4cf80-172">Você pode ler as versões de rascunho no repositório [dotnet/diagnóstico.](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)</span><span class="sxs-lookup"><span data-stu-id="4cf80-172">You can read the draft versions on the [dotnet/diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) repository.</span></span>

<span data-ttu-id="4cf80-173">Este tutorial cobriu o básico das principais ferramentas de diagnóstico .NET.</span><span class="sxs-lookup"><span data-stu-id="4cf80-173">This tutorial covered the basics of key .NET diagnostic tools.</span></span> <span data-ttu-id="4cf80-174">Para uso avançado, consulte a seguinte documentação de referência:</span><span class="sxs-lookup"><span data-stu-id="4cf80-174">For advanced usage, see the following reference documentation:</span></span>

* <span data-ttu-id="4cf80-175">[dotnet-trace](dotnet-trace.md) para processos de lista.</span><span class="sxs-lookup"><span data-stu-id="4cf80-175">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
* <span data-ttu-id="4cf80-176">[contadores dotnet](dotnet-counters.md) para verificar o uso gerenciado da memória.</span><span class="sxs-lookup"><span data-stu-id="4cf80-176">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
* <span data-ttu-id="4cf80-177">[dotnet-dump](dotnet-dump.md) para coletar e analisar um arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="4cf80-177">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
