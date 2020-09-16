---
title: Depurar alto uso da CPU-.NET Core
description: Um tutorial que orienta você pela depuração de alto uso da CPU no .NET Core.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 71e0b98f7ad38836c6a20c3e0e75a878fb6525c7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538703"
---
# <a name="debug-high-cpu-usage-in-net-core"></a><span data-ttu-id="49dca-103">Depurar alto uso da CPU no .NET Core</span><span class="sxs-lookup"><span data-stu-id="49dca-103">Debug high CPU usage in .NET Core</span></span>

<span data-ttu-id="49dca-104">**Este artigo aplica-se a: ✔️** SDK do .net Core 3,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="49dca-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="49dca-105">Neste tutorial, você aprenderá a depurar um cenário de uso excessivo da CPU.</span><span class="sxs-lookup"><span data-stu-id="49dca-105">In this tutorial, you'll learn how to debug an excessive CPU usage scenario.</span></span> <span data-ttu-id="49dca-106">Usando o exemplo fornecido ASP.NET Core repositório de código-fonte do [aplicativo Web](/samples/dotnet/samples/diagnostic-scenarios) , você pode causar um deadlock intencionalmente.</span><span class="sxs-lookup"><span data-stu-id="49dca-106">Using the provided example [ASP.NET Core web app](/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="49dca-107">O ponto de extremidade passará por uma falha e acumulação de threads.</span><span class="sxs-lookup"><span data-stu-id="49dca-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="49dca-108">Você aprenderá como é possível usar várias ferramentas para diagnosticar esse cenário com várias partes importantes dos dados de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="49dca-108">You'll learn how you can use various tools to diagnose this scenario with several key pieces of diagnostics data.</span></span>

<span data-ttu-id="49dca-109">Neste tutorial, você irá:</span><span class="sxs-lookup"><span data-stu-id="49dca-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="49dca-110">Investigar o alto uso da CPU</span><span class="sxs-lookup"><span data-stu-id="49dca-110">Investigate high CPU usage</span></span>
> - <span data-ttu-id="49dca-111">Determinar o uso da CPU com [dotnet-contadores](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="49dca-111">Determine CPU usage with [dotnet-counters](dotnet-counters.md)</span></span>
> - <span data-ttu-id="49dca-112">Usar [dotnet-rastreamento](dotnet-trace.md) para geração de rastreamento</span><span class="sxs-lookup"><span data-stu-id="49dca-112">Use [dotnet-trace](dotnet-trace.md) for trace generation</span></span>
> - <span data-ttu-id="49dca-113">Desempenho do perfil no PerfView</span><span class="sxs-lookup"><span data-stu-id="49dca-113">Profile performance in PerfView</span></span>
> - <span data-ttu-id="49dca-114">Diagnosticar e resolver o uso excessivo da CPU</span><span class="sxs-lookup"><span data-stu-id="49dca-114">Diagnose and solve excessive CPU usage</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49dca-115">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="49dca-115">Prerequisites</span></span>

<span data-ttu-id="49dca-116">O tutorial usa:</span><span class="sxs-lookup"><span data-stu-id="49dca-116">The tutorial uses:</span></span>

- <span data-ttu-id="49dca-117">[SDK do .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core) ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="49dca-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="49dca-118">[Exemplo de destino de depuração](/samples/dotnet/samples/diagnostic-scenarios) para disparar o cenário.</span><span class="sxs-lookup"><span data-stu-id="49dca-118">[Sample debug target](/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario.</span></span>
- <span data-ttu-id="49dca-119">[dotnet – rastreamento](dotnet-trace.md) para listar processos e gerar um perfil.</span><span class="sxs-lookup"><span data-stu-id="49dca-119">[dotnet-trace](dotnet-trace.md) to list processes and generate a profile.</span></span>
- <span data-ttu-id="49dca-120">[dotnet-contadores](dotnet-counters.md) para monitorar o uso da CPU.</span><span class="sxs-lookup"><span data-stu-id="49dca-120">[dotnet-counters](dotnet-counters.md) to monitor cpu usage.</span></span>

## <a name="cpu-counters"></a><span data-ttu-id="49dca-121">Contadores de CPU</span><span class="sxs-lookup"><span data-stu-id="49dca-121">CPU counters</span></span>

<span data-ttu-id="49dca-122">Antes de tentar coletar dados de diagnóstico, você precisa observar uma alta condição de CPU.</span><span class="sxs-lookup"><span data-stu-id="49dca-122">Before attempting to collect diagnostics data, you need to observe a high CPU condition.</span></span> <span data-ttu-id="49dca-123">Execute o [aplicativo de exemplo](/samples/dotnet/samples/diagnostic-scenarios) usando o comando a seguir no diretório raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="49dca-123">Run the [sample application](/samples/dotnet/samples/diagnostic-scenarios) using the following command from the project root directory.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="49dca-124">Para localizar a ID do processo, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="49dca-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="49dca-125">Anote a ID do processo da saída do comando.</span><span class="sxs-lookup"><span data-stu-id="49dca-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="49dca-126">Nossa ID de processo era `22884` , mas a sua será diferente.</span><span class="sxs-lookup"><span data-stu-id="49dca-126">Our process ID was `22884`, but yours will be different.</span></span> <span data-ttu-id="49dca-127">Para verificar o uso atual da CPU, use o comando de ferramenta [dotnet-Counters](dotnet-counters.md) :</span><span class="sxs-lookup"><span data-stu-id="49dca-127">To check the current CPU usage, use the [dotnet-counters](dotnet-counters.md) tool command:</span></span>

```dotnetcli
dotnet-counters monitor --refresh-interval 1 -p 22884
```

<span data-ttu-id="49dca-128">O `refresh-interval` é o número de segundos entre o contador sondando valores de CPU.</span><span class="sxs-lookup"><span data-stu-id="49dca-128">The `refresh-interval` is the number of seconds between the counter polling CPU values.</span></span> <span data-ttu-id="49dca-129">A saída deve ser semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="49dca-129">The output should be similar to the following:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    % Time in GC since last GC (%)                         0
    Allocation Rate / 1 sec (B)                            0
    CPU Usage (%)                                          0
    Exception Count / 1 sec                                0
    GC Heap Size (MB)                                      4
    Gen 0 GC Count / 60 sec                                0
    Gen 0 Size (B)                                         0
    Gen 1 GC Count / 60 sec                                0
    Gen 1 Size (B)                                         0
    Gen 2 GC Count / 60 sec                                0
    Gen 2 Size (B)                                         0
    LOH Size (B)                                           0
    Monitor Lock Contention Count / 1 sec                  0
    Number of Active Timers                                1
    Number of Assemblies Loaded                          140
    ThreadPool Completed Work Item Count / 1 sec           3
    ThreadPool Queue Length                                0
    ThreadPool Thread Count                                7
    Working Set (MB)                                      63
```

<span data-ttu-id="49dca-130">Com o aplicativo Web em execução, imediatamente após a inicialização, a CPU não está sendo consumida e é relatada em `0%` .</span><span class="sxs-lookup"><span data-stu-id="49dca-130">With the web app running, immediately after startup, the CPU isn't being consumed at all and is reported at `0%`.</span></span> <span data-ttu-id="49dca-131">Navegue até a `api/diagscenario/highcpu` rota com `60000` como o parâmetro de rota:</span><span class="sxs-lookup"><span data-stu-id="49dca-131">Navigate to the `api/diagscenario/highcpu` route with `60000` as the route parameter:</span></span>

`https://localhost:5001/api/diagscenario/highcpu/60000`

<span data-ttu-id="49dca-132">Agora, execute novamente o comando [dotnet-Counters](dotnet-counters.md) .</span><span class="sxs-lookup"><span data-stu-id="49dca-132">Now, rerun the [dotnet-counters](dotnet-counters.md) command.</span></span> <span data-ttu-id="49dca-133">Para monitorar apenas o `cpu-usage` , especifique `System.Runtime[cpu-usage]` como parte do comando.</span><span class="sxs-lookup"><span data-stu-id="49dca-133">To monitor just the `cpu-usage`, specify `System.Runtime[cpu-usage]` as part of the command.</span></span>

```dotnetcli
dotnet-counters monitor System.Runtime[cpu-usage] -p 22884 --refresh-interval 1
```

<span data-ttu-id="49dca-134">Você deve ver um aumento no uso da CPU, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="49dca-134">You should see an increase in CPU usage as shown below:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    CPU Usage (%)                                         25
```

<span data-ttu-id="49dca-135">Ao longo da duração da solicitação, o uso da CPU focaliza 25%.</span><span class="sxs-lookup"><span data-stu-id="49dca-135">Throughout the duration of the request, the CPU usage will hover around 25% .</span></span> <span data-ttu-id="49dca-136">Dependendo do computador host, espere o uso de CPU variável.</span><span class="sxs-lookup"><span data-stu-id="49dca-136">Depending on the host machine, expect varying CPU usage.</span></span>

> [!TIP]
> <span data-ttu-id="49dca-137">Para visualizar um uso de CPU ainda maior, você pode exercitar esse ponto de extremidade em várias guias do navegador simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="49dca-137">To visualize an even higher CPU usage, you can exercise this endpoint in multiple browser tabs simultaneously.</span></span>

<span data-ttu-id="49dca-138">Neste ponto, você pode dizer com segurança que a CPU está em execução mais alta do que o esperado.</span><span class="sxs-lookup"><span data-stu-id="49dca-138">At this point, you can safely say the CPU is running higher than you expect.</span></span>

## <a name="trace-generation"></a><span data-ttu-id="49dca-139">Geração de rastreamento</span><span class="sxs-lookup"><span data-stu-id="49dca-139">Trace generation</span></span>

<span data-ttu-id="49dca-140">Ao analisar uma solicitação lenta, você precisa de uma ferramenta de diagnóstico que possa fornecer informações sobre o que o código está fazendo.</span><span class="sxs-lookup"><span data-stu-id="49dca-140">When analyzing a slow request, you need a diagnostics tool that can provide insights into what the code is doing.</span></span> <span data-ttu-id="49dca-141">A opção usual é um criador de perfil, e há diferentes opções de criador de perfil a serem escolhidas.</span><span class="sxs-lookup"><span data-stu-id="49dca-141">The usual choice is a profiler, and there are different profiler options to choose from.</span></span>

### <a name="linux"></a>[<span data-ttu-id="49dca-142">Linux</span><span class="sxs-lookup"><span data-stu-id="49dca-142">Linux</span></span>](#tab/linux)

<span data-ttu-id="49dca-143">A `perf` ferramenta pode ser usada para gerar perfis de aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49dca-143">The `perf` tool can be used to generate .NET Core app profiles.</span></span> <span data-ttu-id="49dca-144">Saia da instância anterior do [destino de depuração de exemplo](/samples/dotnet/samples/diagnostic-scenarios).</span><span class="sxs-lookup"><span data-stu-id="49dca-144">Exit the previous instance of the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios).</span></span>

<span data-ttu-id="49dca-145">Defina a `COMPlus_PerfMapEnabled` variável de ambiente para fazer com que o aplicativo .NET Core crie um `map` arquivo no `/tmp` diretório.</span><span class="sxs-lookup"><span data-stu-id="49dca-145">Set the `COMPlus_PerfMapEnabled` environment variable to cause the .NET Core app to create a `map` file in the `/tmp` directory.</span></span> <span data-ttu-id="49dca-146">Esse `map` arquivo é usado pelo `perf` para mapear o endereço de CPU para funções geradas por JIT por nome.</span><span class="sxs-lookup"><span data-stu-id="49dca-146">This `map` file is used by `perf` to map CPU address to JIT-generated functions by name.</span></span> <span data-ttu-id="49dca-147">Para obter mais informações, consulte [Write perf MAP](../run-time-config/debugging-profiling.md#write-perf-map).</span><span class="sxs-lookup"><span data-stu-id="49dca-147">For more information, see [Write perf map](../run-time-config/debugging-profiling.md#write-perf-map).</span></span>

<span data-ttu-id="49dca-148">Execute o [destino de depuração de exemplo](/samples/dotnet/samples/diagnostic-scenarios) na mesma sessão de terminal.</span><span class="sxs-lookup"><span data-stu-id="49dca-148">Run the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios) in the same terminal session.</span></span>

```dotnetcli
export COMPlus_PerfMapEnabled=1
dotnet run
```

<span data-ttu-id="49dca-149">Exerça o ponto de extremidade de API de CPU alta ( `https://localhost:5001/api/diagscenario/highcpu/60000` ) novamente.</span><span class="sxs-lookup"><span data-stu-id="49dca-149">Exercise the high CPU API endpoint (`https://localhost:5001/api/diagscenario/highcpu/60000`) again.</span></span> <span data-ttu-id="49dca-150">Enquanto estiver em execução dentro da solicitação de 1 minuto, execute o `perf` comando com a ID do processo:</span><span class="sxs-lookup"><span data-stu-id="49dca-150">While it's running within the 1-minute request, run the `perf` command with your process ID:</span></span>

```bash
sudo perf record -p 2266 -g
```

<span data-ttu-id="49dca-151">O `perf` comando inicia o processo de coleta de desempenho.</span><span class="sxs-lookup"><span data-stu-id="49dca-151">The `perf` command starts the performance collection process.</span></span> <span data-ttu-id="49dca-152">Deixe que ele seja executado por cerca de 20-30 segundos e pressione <kbd>Ctrl + C</kbd> para sair do processo de coleta.</span><span class="sxs-lookup"><span data-stu-id="49dca-152">Let it run for about 20-30 seconds, then press <kbd>Ctrl+C</kbd> to exit the collection process.</span></span> <span data-ttu-id="49dca-153">Você pode usar o mesmo `perf` comando para ver a saída do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="49dca-153">You can use the same `perf` command to see the output of the trace.</span></span>

```bash
sudo perf report -f
```

<span data-ttu-id="49dca-154">Você também pode gerar um _elemento chama-grafo_ usando os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="49dca-154">You can also generate a _flame-graph_ by using the following commands:</span></span>

```bash
git clone --depth=1 https://github.com/BrendanGregg/FlameGraph
sudo perf script | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
```

<span data-ttu-id="49dca-155">Esse comando gera um `flamegraph.svg` que você pode exibir no navegador para investigar o problema de desempenho:</span><span class="sxs-lookup"><span data-stu-id="49dca-155">This command generates a `flamegraph.svg` that you can view in the browser to investigate the performance problem:</span></span>

<span data-ttu-id="49dca-156">[![Imagem SVG do grafo chama](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="49dca-156">[![Flame graph SVG image](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span></span>

### <a name="windows"></a>[<span data-ttu-id="49dca-157">Windows</span><span class="sxs-lookup"><span data-stu-id="49dca-157">Windows</span></span>](#tab/windows)

<span data-ttu-id="49dca-158">No Windows, você pode usar a ferramenta [dotnet-Trace](dotnet-trace.md) como um criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="49dca-158">On Windows, you can use the [dotnet-trace](dotnet-trace.md) tool as a profiler.</span></span> <span data-ttu-id="49dca-159">Usando o [destino de depuração de exemplo](/samples/dotnet/samples/diagnostic-scenarios)anterior, exerça novamente o ponto de extremidade de CPU alta ( `https://localhost:5001/api/diagscenario/highcpu/60000` ).</span><span class="sxs-lookup"><span data-stu-id="49dca-159">Using the previous [sample debug target](/samples/dotnet/samples/diagnostic-scenarios), exercise the high CPU endpoint (`https://localhost:5001/api/diagscenario/highcpu/60000`) again.</span></span> <span data-ttu-id="49dca-160">Enquanto estiver em execução dentro da solicitação de 1 minuto, use o `collect` comando da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="49dca-160">While it's running within the 1-minute request, use the `collect` command as follows:</span></span>

```dotnetcli
dotnet-trace collect -p 22884 --providers Microsoft-DotNETCore-SampleProfiler
```

<span data-ttu-id="49dca-161">Deixe que o [rastreamento dotnet](dotnet-trace.md) seja executado por cerca de 20-30 segundos e, em seguida, pressione <kbd>Enter</kbd> para sair da coleção.</span><span class="sxs-lookup"><span data-stu-id="49dca-161">Let [dotnet-trace](dotnet-trace.md) run for about 20-30 seconds, and then press the <kbd>Enter</kbd> to exit the collection.</span></span> <span data-ttu-id="49dca-162">O resultado é um `nettrace` arquivo localizado na mesma pasta.</span><span class="sxs-lookup"><span data-stu-id="49dca-162">The result is a `nettrace` file located in the same folder.</span></span> <span data-ttu-id="49dca-163">Os `nettrace` arquivos são uma ótima maneira de usar as ferramentas de análise existentes no Windows.</span><span class="sxs-lookup"><span data-stu-id="49dca-163">The `nettrace` files are a great way to use existing analysis tools on Windows.</span></span>

<span data-ttu-id="49dca-164">Abra o `nettrace` com [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="49dca-164">Open the `nettrace` with [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) as shown below.</span></span>

<span data-ttu-id="49dca-165">[![Imagem PerfView](media/perfview.jpg)](media/perfview.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="49dca-165">[![PerfView image](media/perfview.jpg)](media/perfview.jpg#lightbox)</span></span>

---

## <a name="see-also"></a><span data-ttu-id="49dca-166">Confira também</span><span class="sxs-lookup"><span data-stu-id="49dca-166">See also</span></span>

- <span data-ttu-id="49dca-167">[dotnet-rastrear](dotnet-trace.md) para listar processos</span><span class="sxs-lookup"><span data-stu-id="49dca-167">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="49dca-168">[dotnet-contadores](dotnet-counters.md) para verificar o uso de memória gerenciada</span><span class="sxs-lookup"><span data-stu-id="49dca-168">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="49dca-169">[dotnet-despejo](dotnet-dump.md) para coletar e analisar um arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="49dca-169">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="49dca-170">dotnet/diagnóstico</span><span class="sxs-lookup"><span data-stu-id="49dca-170">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="49dca-171">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="49dca-171">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="49dca-172">Depurar um deadlock no .NET Core</span><span class="sxs-lookup"><span data-stu-id="49dca-172">Debug a deadlock in .NET Core</span></span>](debug-deadlock.md)
