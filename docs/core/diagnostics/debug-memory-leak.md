---
title: Tutorial de depuração de perda de memória
description: Saiba como depurar um vazamento de memória no .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.topic: tutorial
ms.date: 12/17/2019
ms.openlocfilehash: def848b5fe6f08cf32067b833bbf6a97a56edda1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443508"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a><span data-ttu-id="5ba8d-103">Tutorial: Depurar um vazamento de memória no .NET Core</span><span class="sxs-lookup"><span data-stu-id="5ba8d-103">Tutorial: Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="5ba8d-104">**Este artigo aplica-se a: ✓ o** SDK do .net Core 3,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="5ba8d-104">**This article applies to: ✓** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="5ba8d-105">Este tutorial demonstra as ferramentas para analisar um vazamento de memória do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-105">This tutorial demonstrates the tools to analyze a .NET Core memory leak.</span></span>

<span data-ttu-id="5ba8d-106">Este tutorial usa um aplicativo de exemplo, que é projetado para vazar a memória intencionalmente.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-106">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="5ba8d-107">O exemplo é fornecido como um exercício.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-107">The sample is provided as an exercise.</span></span> <span data-ttu-id="5ba8d-108">Você pode analisar um aplicativo que está vazando involuntariamente a memória também.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-108">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="5ba8d-109">Neste tutorial, você irá:</span><span class="sxs-lookup"><span data-stu-id="5ba8d-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="5ba8d-110">Examine o uso de memória gerenciada com os [contadores dotnet](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="5ba8d-110">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="5ba8d-111">Gerar um arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-111">Generate a dump file.</span></span>
> - <span data-ttu-id="5ba8d-112">Analise o uso de memória usando o arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-112">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5ba8d-113">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5ba8d-113">Prerequisites</span></span>

<span data-ttu-id="5ba8d-114">O tutorial usa:</span><span class="sxs-lookup"><span data-stu-id="5ba8d-114">The tutorial uses:</span></span>

- <span data-ttu-id="5ba8d-115">[SDK do .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core) ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-115">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="5ba8d-116">[dotnet – rastreamento](dotnet-trace.md) para listar processos.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-116">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
- <span data-ttu-id="5ba8d-117">[dotnet-contadores](dotnet-counters.md) para verificar o uso de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-117">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="5ba8d-118">[dotnet-despejo](dotnet-dump.md) para coletar e analisar um arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-118">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="5ba8d-119">Um aplicativo de [destino de depuração de exemplo](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) para diagnosticar.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-119">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="5ba8d-120">O tutorial pressupõe que o exemplo e as ferramentas estejam instalados e prontos para uso.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-120">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="5ba8d-121">Examinar o uso de memória gerenciada</span><span class="sxs-lookup"><span data-stu-id="5ba8d-121">Examine managed memory usage</span></span>

<span data-ttu-id="5ba8d-122">Antes de começar a coletar dados de diagnóstico para ajudar a raiz a causar esse cenário, você precisa certificar-se de que está realmente vendo um vazamento de memória (aumento de memória).</span><span class="sxs-lookup"><span data-stu-id="5ba8d-122">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="5ba8d-123">Você pode usar a ferramenta [dotnet-Counters](dotnet-counters.md) para confirmar isso.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-123">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="5ba8d-124">Abra uma janela de console e navegue até o diretório em que você baixou e descompactou o [destino de depuração de exemplo](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span><span class="sxs-lookup"><span data-stu-id="5ba8d-124">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="5ba8d-125">Execute o destino:</span><span class="sxs-lookup"><span data-stu-id="5ba8d-125">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="5ba8d-126">Em um console separado, localize a ID do processo usando a ferramenta [dotnet-Trace](dotnet-trace.md) :</span><span class="sxs-lookup"><span data-stu-id="5ba8d-126">From a separate console, find the process ID using the [dotnet-trace](dotnet-trace.md) tool:</span></span>

```console
dotnet-trace ps
```

<span data-ttu-id="5ba8d-127">A saída deve ser semelhante a:</span><span class="sxs-lookup"><span data-stu-id="5ba8d-127">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="5ba8d-128">Agora, verifique o uso de memória gerenciada com a ferramenta [dotnet-Counters](dotnet-counters.md) .</span><span class="sxs-lookup"><span data-stu-id="5ba8d-128">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="5ba8d-129">O `--refresh-interval` especifica o número de segundos entre as atualizações:</span><span class="sxs-lookup"><span data-stu-id="5ba8d-129">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="5ba8d-130">A saída ao vivo deve ser semelhante a:</span><span class="sxs-lookup"><span data-stu-id="5ba8d-130">The live output should be similar to:</span></span>

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

<span data-ttu-id="5ba8d-131">Concentrando-se nesta linha:</span><span class="sxs-lookup"><span data-stu-id="5ba8d-131">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="5ba8d-132">Você pode ver que a memória de heap gerenciada é de 4 MB logo após a inicialização.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-132">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="5ba8d-133">Agora, pressione a URL `http://localhost:5000/api/diagscenario/memleak/20000`.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-133">Now, hit the URL `http://localhost:5000/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="5ba8d-134">Observe que o uso de memória cresceu para 30 MB.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-134">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="5ba8d-135">Ao assistir ao uso de memória, você pode dizer com segurança que a memória está crescendo ou vazando.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-135">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="5ba8d-136">A próxima etapa é coletar os dados certos para análise de memória.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-136">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="5ba8d-137">Gerar despejo de memória</span><span class="sxs-lookup"><span data-stu-id="5ba8d-137">Generate memory dump</span></span>

<span data-ttu-id="5ba8d-138">Ao analisar possíveis vazamentos de memória, você precisa ter acesso ao heap de memória do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-138">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="5ba8d-139">Em seguida, você pode analisar o conteúdo da memória.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-139">Then you can analyze the memory contents.</span></span> <span data-ttu-id="5ba8d-140">Examinando relações entre objetos, você cria teorias sobre o motivo pelo qual a memória não está sendo liberada.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-140">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="5ba8d-141">Uma fonte de dados de diagnóstico comum é um despejo de memória no Windows ou o dump de núcleo equivalente no Linux.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-141">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="5ba8d-142">Para gerar um despejo de um aplicativo .NET Core, você pode usar a ferramenta [dotnet-dump)](dotnet-dump.md) .</span><span class="sxs-lookup"><span data-stu-id="5ba8d-142">To generate a dump of a .NET Core application, you can use the [dotnet-dump)](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="5ba8d-143">Usando o [destino de depuração de exemplo](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) iniciado anteriormente, execute o seguinte comando para gerar um despejo de núcleo do Linux:</span><span class="sxs-lookup"><span data-stu-id="5ba8d-143">Using the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="5ba8d-144">O resultado é um dump principal localizado na mesma pasta.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-144">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="5ba8d-145">Reiniciar o processo com falha</span><span class="sxs-lookup"><span data-stu-id="5ba8d-145">Restart the failed process</span></span>

<span data-ttu-id="5ba8d-146">Depois que o despejo for coletado, você deverá ter informações suficientes para diagnosticar o processo com falha.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-146">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="5ba8d-147">Se o processo com falha estiver em execução em um servidor de produção, agora é o momento ideal para a remediação de curto prazo reiniciando o processo.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-147">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="5ba8d-148">Neste tutorial, você está pronto para o destino de [depuração de exemplo](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) e pode fechá-lo.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-148">In this tutorial, you're now done with the [Sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="5ba8d-149">Navegue até o terminal que iniciou o servidor e pressione `Control-C`.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-149">Navigate to the terminal that started the server and press `Control-C`.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="5ba8d-150">Analisar o dump principal</span><span class="sxs-lookup"><span data-stu-id="5ba8d-150">Analyze the core dump</span></span>

<span data-ttu-id="5ba8d-151">Agora que você tem um dump principal gerado, use a ferramenta [dotnet-dump)](dotnet-dump.md) para analisar o despejo:</span><span class="sxs-lookup"><span data-stu-id="5ba8d-151">Now that you have a core dump generated, use the [dotnet-dump)](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="5ba8d-152">Em que `core_20190430_185145` é o nome do dump principal que você deseja analisar.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-152">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="5ba8d-153">Se você vir um erro reclamando que *libdl.so* não pode ser encontrado, talvez seja necessário instalar o pacote *libc6-dev* .</span><span class="sxs-lookup"><span data-stu-id="5ba8d-153">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="5ba8d-154">Para saber mais, confira [Pré-requisitos para o .NET Core no Linux](../linux-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="5ba8d-154">For more information, see [Prerequisites for .NET Core on Linux](../linux-prerequisites.md).</span></span>

<span data-ttu-id="5ba8d-155">Você verá um prompt onde pode inserir comandos SOS.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-155">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="5ba8d-156">Normalmente, a primeira coisa que você deseja examinar é o estado geral do heap gerenciado:</span><span class="sxs-lookup"><span data-stu-id="5ba8d-156">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

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

<span data-ttu-id="5ba8d-157">Aqui você pode ver que a maioria dos objetos são `String` ou `Customer` objetos.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-157">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="5ba8d-158">Você pode usar o comando `dumpheap` novamente com a tabela de métodos (MT) para obter uma lista de todas as instâncias de `String`:</span><span class="sxs-lookup"><span data-stu-id="5ba8d-158">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

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

<span data-ttu-id="5ba8d-159">Agora você pode usar o comando `gcroot` em uma instância `System.String` para ver como e por que o objeto tem raiz.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-159">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="5ba8d-160">Seja paciente porque esse comando leva vários minutos com um heap de 30 MB:</span><span class="sxs-lookup"><span data-stu-id="5ba8d-160">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

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

<span data-ttu-id="5ba8d-161">Você pode ver que o `String` é mantido diretamente pelo objeto `Customer` e é indiretamente mantido por um objeto `CustomerCache`.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-161">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="5ba8d-162">Você pode continuar despejando objetos para ver que a maioria dos objetos `String` seguem um padrão semelhante.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-162">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="5ba8d-163">Neste ponto, a investigação forneceu informações suficientes para identificar a causa raiz em seu código.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-163">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="5ba8d-164">Esse procedimento geral permite que você identifique a origem dos principais vazamentos de memória.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-164">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="5ba8d-165">Limpar recursos</span><span class="sxs-lookup"><span data-stu-id="5ba8d-165">Clean up resources</span></span>

<span data-ttu-id="5ba8d-166">Neste tutorial, você iniciou um servidor Web de exemplo.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-166">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="5ba8d-167">Esse servidor deve ter sido desligado, conforme explicado na seção [reiniciar o processo com falha](#restart-the-failed-process) .</span><span class="sxs-lookup"><span data-stu-id="5ba8d-167">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="5ba8d-168">Você também pode excluir o arquivo de despejo que foi criado.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-168">You can also delete the dump file that was created.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5ba8d-169">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5ba8d-169">Next steps</span></span>

<span data-ttu-id="5ba8d-170">Parabéns por concluir este tutorial.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-170">Congratulations on completing this tutorial.</span></span>

<span data-ttu-id="5ba8d-171">Ainda estamos publicando mais tutoriais de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-171">We're still publishing more diagnostic tutorials.</span></span> <span data-ttu-id="5ba8d-172">Você pode ler as versões de rascunho no repositório [dotnet/diagnóstico](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) .</span><span class="sxs-lookup"><span data-stu-id="5ba8d-172">You can read the draft versions on the [dotnet/diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) repository.</span></span>

<span data-ttu-id="5ba8d-173">Este tutorial abordou as noções básicas sobre as principais ferramentas de diagnóstico do .NET.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-173">This tutorial covered the basics of key .NET diagnostic tools.</span></span> <span data-ttu-id="5ba8d-174">Para uso avançado, consulte a seguinte documentação de referência:</span><span class="sxs-lookup"><span data-stu-id="5ba8d-174">For advanced usage, see the following reference documentation:</span></span>

* <span data-ttu-id="5ba8d-175">[dotnet – rastreamento](dotnet-trace.md) para listar processos.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-175">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
* <span data-ttu-id="5ba8d-176">[dotnet-contadores](dotnet-counters.md) para verificar o uso de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-176">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
* <span data-ttu-id="5ba8d-177">[dotnet-despejo](dotnet-dump.md) para coletar e analisar um arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="5ba8d-177">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
