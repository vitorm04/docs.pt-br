---
title: dotnet-contadores-.NET Core
description: Saiba como instalar e usar a ferramenta de linha de comando dotnet-Counter.
ms.date: 02/26/2020
ms.openlocfilehash: 7ff29ad91ad271afd35e3d38a4d748bc79ad6c03
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507248"
---
# <a name="dotnet-counters"></a><span data-ttu-id="604bc-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="604bc-103">dotnet-counters</span></span>

<span data-ttu-id="604bc-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 3,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="604bc-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="604bc-105">Instalar dotnet-contadores</span><span class="sxs-lookup"><span data-stu-id="604bc-105">Install dotnet-counters</span></span>

<span data-ttu-id="604bc-106">Para instalar a versão de lançamento mais recente do `dotnet-counters` [pacote NuGet](https://www.nuget.org/packages/dotnet-counters), use o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="604bc-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="604bc-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="604bc-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="604bc-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="604bc-108">Description</span></span>

<span data-ttu-id="604bc-109">`dotnet-counters` é uma ferramenta de monitoramento de desempenho para monitoramento de integridade ad hoc e investigação de desempenho de primeiro nível.</span><span class="sxs-lookup"><span data-stu-id="604bc-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="604bc-110">Ele pode observar os valores do contador de desempenho que são publicados por meio da <xref:System.Diagnostics.Tracing.EventCounter> API.</span><span class="sxs-lookup"><span data-stu-id="604bc-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="604bc-111">Por exemplo, você pode monitorar rapidamente coisas como o uso da CPU ou a taxa de exceções que estão sendo geradas em seu aplicativo .NET Core para ver se há algo suspeito antes de mergulhar em uma investigação de desempenho mais séria usando o `PerfView` ou o `dotnet-trace` .</span><span class="sxs-lookup"><span data-stu-id="604bc-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="604bc-112">Opções</span><span class="sxs-lookup"><span data-stu-id="604bc-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="604bc-113">Exibe a versão do utilitário dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="604bc-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="604bc-114">Mostra a ajuda da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="604bc-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="604bc-115">Comandos</span><span class="sxs-lookup"><span data-stu-id="604bc-115">Commands</span></span>

| <span data-ttu-id="604bc-116">Comando</span><span class="sxs-lookup"><span data-stu-id="604bc-116">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="604bc-117">dotnet – coleta de contadores</span><span class="sxs-lookup"><span data-stu-id="604bc-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="604bc-118">dotnet – lista de contadores</span><span class="sxs-lookup"><span data-stu-id="604bc-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="604bc-119">dotnet – monitor de contadores</span><span class="sxs-lookup"><span data-stu-id="604bc-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="604bc-120">dotnet-contadores PS</span><span class="sxs-lookup"><span data-stu-id="604bc-120">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="604bc-121">dotnet – coleta de contadores</span><span class="sxs-lookup"><span data-stu-id="604bc-121">dotnet-counters collect</span></span>

<span data-ttu-id="604bc-122">Coletar periodicamente os valores de contador selecionados e exportá-los para um formato de arquivo especificado para o pós-processamento.</span><span class="sxs-lookup"><span data-stu-id="604bc-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="604bc-123">Sinopse</span><span class="sxs-lookup"><span data-stu-id="604bc-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="604bc-124">Opções</span><span class="sxs-lookup"><span data-stu-id="604bc-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="604bc-125">A ID do processo a ser monitorado.</span><span class="sxs-lookup"><span data-stu-id="604bc-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="604bc-126">O número de segundos de atraso entre a atualização dos contadores exibidos</span><span class="sxs-lookup"><span data-stu-id="604bc-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="604bc-127">Uma lista separada por vírgulas de contadores.</span><span class="sxs-lookup"><span data-stu-id="604bc-127">A comma-separated list of counters.</span></span> <span data-ttu-id="604bc-128">Os contadores podem ser especificados `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="604bc-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="604bc-129">Se o `provider_name` for usado sem uma lista de contadores de qualificação, todos os contadores do provedor serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="604bc-129">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="604bc-130">Para descobrir os nomes de provedor e contador, use o comando [dotnet-Counters List](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="604bc-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="604bc-131">O formato a ser exportado.</span><span class="sxs-lookup"><span data-stu-id="604bc-131">The format to be exported.</span></span> <span data-ttu-id="604bc-132">Atualmente disponível: CSV, JSON.</span><span class="sxs-lookup"><span data-stu-id="604bc-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="604bc-133">O nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="604bc-133">The name of the output file.</span></span>

- <span data-ttu-id="604bc-134">**`-- <command>` (para aplicativos de destino que executam o .NET 5,0 ou posterior somente)**</span><span class="sxs-lookup"><span data-stu-id="604bc-134">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="604bc-135">Após os parâmetros de configuração da coleção, o usuário pode acrescentar `--` seguido por um comando para iniciar um aplicativo .NET com pelo menos um tempo de execução de 5,0.</span><span class="sxs-lookup"><span data-stu-id="604bc-135">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="604bc-136">`dotnet-counters` o iniciará um processo com o comando fornecido e coletará as métricas solicitadas.</span><span class="sxs-lookup"><span data-stu-id="604bc-136">`dotnet-counters` will launch a process with the provided command and collect the requested metrics.</span></span> <span data-ttu-id="604bc-137">Isso geralmente é útil para coletar métricas para o caminho de inicialização do aplicativo e pode ser usado para diagnosticar ou monitorar problemas que ocorrem antes ou logo após o ponto de entrada principal.</span><span class="sxs-lookup"><span data-stu-id="604bc-137">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

> [!NOTE]
> <span data-ttu-id="604bc-138">O uso dessa opção monitora o primeiro processo do .NET 5,0 que se comunica de volta à ferramenta, o que significa que, se o comando iniciar vários aplicativos .NET, ele só coletará o primeiro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="604bc-138">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="604bc-139">Portanto, é recomendável usar essa opção em aplicativos independentes ou usando a `dotnet exec <app.dll>` opção.</span><span class="sxs-lookup"><span data-stu-id="604bc-139">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

### <a name="examples"></a><span data-ttu-id="604bc-140">Exemplos</span><span class="sxs-lookup"><span data-stu-id="604bc-140">Examples</span></span>

- <span data-ttu-id="604bc-141">Colete todos os contadores em um intervalo de atualização de 3 segundos e gere um CSV como saída:</span><span class="sxs-lookup"><span data-stu-id="604bc-141">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- <span data-ttu-id="604bc-142">Inicie `dotnet mvc.dll` o como um processo filho e comece a coletar contadores de tempo de execução e ASP.NET Core contadores de hospedagem da inicialização e salve-os como uma saída JSON:</span><span class="sxs-lookup"><span data-stu-id="604bc-142">Start `dotnet mvc.dll` as a child process and start collecting runtime counters and ASP.NET Core Hosting counters from startup and save it as a JSON output:</span></span>

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="604bc-143">dotnet – lista de contadores</span><span class="sxs-lookup"><span data-stu-id="604bc-143">dotnet-counters list</span></span>

<span data-ttu-id="604bc-144">Exibe uma lista de nomes e descrições de contadores, agrupados por provedor.</span><span class="sxs-lookup"><span data-stu-id="604bc-144">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="604bc-145">Sinopse</span><span class="sxs-lookup"><span data-stu-id="604bc-145">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="604bc-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="604bc-146">Example</span></span>

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs / min
    gen-1-gc-count                               Number of Gen 1 GCs / min
    gen-2-gc-count                               Number of Gen 2 GCs / min
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions / sec
    threadpool-thread-count                      Number of ThreadPool Threads
    monitor-lock-contention-count                Monitor Lock Contention Count
    threadpool-queue-length                      ThreadPool Work Items Queue Length
    threadpool-completed-items-count             ThreadPool Completed Work Items Count
    active-timer-count                           Active Timers Count

Microsoft.AspNetCore.Hosting
    requests-per-second                  Request rate
    total-requests                       Total number of requests
    current-requests                     Current number of requests
    failed-requests                      Failed number of requests
```

> [!NOTE]
> <span data-ttu-id="604bc-147">Os `Microsoft.AspNetCore.Hosting` contadores são exibidos quando há processos identificados que dão suporte a esses contadores, por exemplo, quando um aplicativo ASP.NET Core está em execução no computador host.</span><span class="sxs-lookup"><span data-stu-id="604bc-147">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="604bc-148">dotnet – monitor de contadores</span><span class="sxs-lookup"><span data-stu-id="604bc-148">dotnet-counters monitor</span></span>

<span data-ttu-id="604bc-149">Exibe a atualização periódica de valores dos contadores selecionados.</span><span class="sxs-lookup"><span data-stu-id="604bc-149">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="604bc-150">Sinopse</span><span class="sxs-lookup"><span data-stu-id="604bc-150">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [--counters] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="604bc-151">Opções</span><span class="sxs-lookup"><span data-stu-id="604bc-151">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="604bc-152">A ID do processo a ser monitorado.</span><span class="sxs-lookup"><span data-stu-id="604bc-152">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="604bc-153">O número de segundos de atraso entre a atualização dos contadores exibidos</span><span class="sxs-lookup"><span data-stu-id="604bc-153">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="604bc-154">Uma lista separada por vírgulas de contadores.</span><span class="sxs-lookup"><span data-stu-id="604bc-154">A comma-separated list of counters.</span></span> <span data-ttu-id="604bc-155">Os contadores podem ser especificados `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="604bc-155">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="604bc-156">Se o `provider_name` for usado sem uma lista de contadores de qualificação, todos os contadores do provedor serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="604bc-156">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="604bc-157">Para descobrir os nomes de provedor e contador, use o comando [dotnet-Counters List](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="604bc-157">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

 <span data-ttu-id="604bc-158">**`-- <command>` (para aplicativos de destino que executam o .NET 5,0 ou posterior somente)**</span><span class="sxs-lookup"><span data-stu-id="604bc-158">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="604bc-159">Após os parâmetros de configuração da coleção, o usuário pode acrescentar `--` seguido por um comando para iniciar um aplicativo .NET com pelo menos um tempo de execução de 5,0.</span><span class="sxs-lookup"><span data-stu-id="604bc-159">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="604bc-160">`dotnet-counters` o iniciará um processo com o comando fornecido e monitorará as métricas solicitadas.</span><span class="sxs-lookup"><span data-stu-id="604bc-160">`dotnet-counters` will launch a process with the provided command and monitor the requested metrics.</span></span> <span data-ttu-id="604bc-161">Isso geralmente é útil para coletar métricas para o caminho de inicialização do aplicativo e pode ser usado para diagnosticar ou monitorar problemas que ocorrem antes ou logo após o ponto de entrada principal.</span><span class="sxs-lookup"><span data-stu-id="604bc-161">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="604bc-162">O uso dessa opção monitora o primeiro processo do .NET 5,0 que se comunica de volta à ferramenta, o que significa que, se o comando iniciar vários aplicativos .NET, ele só coletará o primeiro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="604bc-162">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="604bc-163">Portanto, é recomendável usar essa opção em aplicativos independentes ou usando a `dotnet exec <app.dll>` opção.</span><span class="sxs-lookup"><span data-stu-id="604bc-163">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

### <a name="examples"></a><span data-ttu-id="604bc-164">Exemplos</span><span class="sxs-lookup"><span data-stu-id="604bc-164">Examples</span></span>

- <span data-ttu-id="604bc-165">Monitorar todos os contadores de `System.Runtime` em um intervalo de atualização de 3 segundos:</span><span class="sxs-lookup"><span data-stu-id="604bc-165">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 --counters System.Runtime
  Press p to pause, r to resume, q to quit.
      Status: Running

  [System.Runtime]
      % Time in GC since last GC (%)                                 0
      Allocation Rate (B / 1 sec)                                5,376
      CPU Usage (%)                                                  0
      Exception Count (Count / 1 sec)                                0
      GC Fragmentation (%)                                          48.467
      GC Heap Size (MB)                                              0
      Gen 0 GC Count (Count / 1 sec)                                 1
      Gen 0 Size (B)                                                24
      Gen 1 GC Count (Count / 1 sec)                                 1
      Gen 1 Size (B)                                                24
      Gen 2 GC Count (Count / 1 sec)                                 1
      Gen 2 Size (B)                                           272,000
      IL Bytes Jitted (B)                                       19,449
      LOH Size (B)                                              19,640
      Monitor Lock Contention Count (Count / 1 sec)                  0
      Number of Active Timers                                        0
      Number of Assemblies Loaded                                    7
      Number of Methods Jitted                                     166
      POH (Pinned Object Heap) Size (B)                             24
      ThreadPool Completed Work Item Count (Count / 1 sec)           0
      ThreadPool Queue Length                                        0
      ThreadPool Thread Count                                        2
      Working Set (MB)                                              19
  ```

- <span data-ttu-id="604bc-166">Monitorar apenas o uso da CPU e o tamanho do heap do GC de `System.Runtime` :</span><span class="sxs-lookup"><span data-stu-id="604bc-166">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="604bc-167">Monitorar `EventCounter` valores de definidos pelo usuário `EventSource` .</span><span class="sxs-lookup"><span data-stu-id="604bc-167">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="604bc-168">Para obter mais informações, consulte [tutorial: medir o desempenho usando o EventCounters no .NET Core](event-counter-perf.md).</span><span class="sxs-lookup"><span data-stu-id="604bc-168">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- <span data-ttu-id="604bc-169">Inicie `my-aspnet-server.exe` e monitore o número de assemblies carregados a partir de sua inicialização (somente .net 5,0 ou posterior):</span><span class="sxs-lookup"><span data-stu-id="604bc-169">Launch `my-aspnet-server.exe` and monitor the # of assemblies loaded from its startup (.NET 5.0 or later only):</span></span>

  <span data-ttu-id="604bc-170">Observação: isso funciona somente para aplicativos que executam o .NET 5,0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="604bc-170">NOTE: This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- <span data-ttu-id="604bc-171">Inicie `my-aspnet-server.exe` com `arg1` e `arg2` como argumentos de linha de comando e monitore seu conjunto de trabalho e o tamanho do heap de GC de sua inicialização (somente .NET 5,0 ou posterior):</span><span class="sxs-lookup"><span data-stu-id="604bc-171">Launch `my-aspnet-server.exe` with `arg1` and `arg2` as command-line arguments and monitor its working set and GC heap size from its startup (.NET 5.0 or later only):</span></span>

  <span data-ttu-id="604bc-172">Observação: isso funciona somente para aplicativos que executam o .NET 5,0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="604bc-172">NOTE: This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[working-set,gc-heap-size] -- my-aspnet-server.exe arg1 arg2
  ```

  ```console
  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      GC Heap Size (MB)                                 39
      Working Set (MB)                                  59
  ```

## <a name="dotnet-counters-ps"></a><span data-ttu-id="604bc-173">dotnet-contadores PS</span><span class="sxs-lookup"><span data-stu-id="604bc-173">dotnet-counters ps</span></span>

<span data-ttu-id="604bc-174">Exibe uma lista de processos dotnet que podem ser monitorados.</span><span class="sxs-lookup"><span data-stu-id="604bc-174">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="604bc-175">Sinopse</span><span class="sxs-lookup"><span data-stu-id="604bc-175">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="604bc-176">Exemplo</span><span class="sxs-lookup"><span data-stu-id="604bc-176">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
