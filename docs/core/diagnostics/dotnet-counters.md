---
title: contadores dotnet - .NET Core
description: Saiba como instalar e usar a ferramenta de linha de comando dotnet-counter.
ms.date: 02/26/2020
ms.openlocfilehash: dc95297478784ca06fe442a939f8489a40b29da7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147172"
---
# <a name="dotnet-counters"></a><span data-ttu-id="1883f-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="1883f-103">dotnet-counters</span></span>

<span data-ttu-id="1883f-104">**Este artigo se aplica a:** ✔️ .NET Core 3.0 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="1883f-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="1883f-105">Instale contadores de dotnet</span><span class="sxs-lookup"><span data-stu-id="1883f-105">Install dotnet-counters</span></span>

<span data-ttu-id="1883f-106">Para instalar a versão `dotnet-counters` de versão mais recente do [pacote NuGet,](https://www.nuget.org/packages/dotnet-counters)use o comando [dotnet tool install:](../tools/dotnet-tool-install.md)</span><span class="sxs-lookup"><span data-stu-id="1883f-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="1883f-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="1883f-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="1883f-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="1883f-108">Description</span></span>

<span data-ttu-id="1883f-109">`dotnet-counters`é uma ferramenta de monitoramento de desempenho para monitoramento de saúde ad-hoc e investigação de desempenho de primeiro nível.</span><span class="sxs-lookup"><span data-stu-id="1883f-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="1883f-110">Ele pode observar valores de <xref:System.Diagnostics.Tracing.EventCounter> contador de desempenho que são publicados através da API.</span><span class="sxs-lookup"><span data-stu-id="1883f-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="1883f-111">Por exemplo, você pode monitorar rapidamente coisas como o uso da CPU ou a taxa de exceções que estão sendo `PerfView` lançadas em seu aplicativo .NET Core para ver se há algo suspeito antes de mergulhar em uma investigação de desempenho mais séria usando ou `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="1883f-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="1883f-112">Opções</span><span class="sxs-lookup"><span data-stu-id="1883f-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="1883f-113">Exibe a versão do utilitário dotnet-counters.</span><span class="sxs-lookup"><span data-stu-id="1883f-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="1883f-114">Mostra ajuda na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="1883f-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="1883f-115">Comandos</span><span class="sxs-lookup"><span data-stu-id="1883f-115">Commands</span></span>

| <span data-ttu-id="1883f-116">Comando</span><span class="sxs-lookup"><span data-stu-id="1883f-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="1883f-117">dotnet-contadores coletar</span><span class="sxs-lookup"><span data-stu-id="1883f-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="1883f-118">lista dotnet-contadores</span><span class="sxs-lookup"><span data-stu-id="1883f-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="1883f-119">monitor dotnet-contadores</span><span class="sxs-lookup"><span data-stu-id="1883f-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="1883f-120">dotnet-counters ps</span><span class="sxs-lookup"><span data-stu-id="1883f-120">dotnet-counters ps</span></span>](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="1883f-121">dotnet-contadores coletar</span><span class="sxs-lookup"><span data-stu-id="1883f-121">dotnet-counters collect</span></span>

<span data-ttu-id="1883f-122">Coletar periodicamente os valores do contador selecionados e exportá-los para um formato de arquivo especificado para pós-processamento.</span><span class="sxs-lookup"><span data-stu-id="1883f-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="1883f-123">Sinopse</span><span class="sxs-lookup"><span data-stu-id="1883f-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a><span data-ttu-id="1883f-124">Opções</span><span class="sxs-lookup"><span data-stu-id="1883f-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="1883f-125">A id do processo a ser monitorada.</span><span class="sxs-lookup"><span data-stu-id="1883f-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="1883f-126">O número de segundos para atrasar entre a atualização dos contadores exibidos</span><span class="sxs-lookup"><span data-stu-id="1883f-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="1883f-127">Uma lista de contadores separados no espaço.</span><span class="sxs-lookup"><span data-stu-id="1883f-127">A space separated list of counters.</span></span> <span data-ttu-id="1883f-128">Os contadores podem `provider_name[:counter_name]`ser especificados .</span><span class="sxs-lookup"><span data-stu-id="1883f-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="1883f-129">Se `provider_name` o for usado `counter_name`sem uma qualificação, todos os contadores serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="1883f-129">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="1883f-130">Para descobrir nomes de provedores e contadores, use o comando [dotnet-counters list.](#dotnet-counters-list)</span><span class="sxs-lookup"><span data-stu-id="1883f-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="1883f-131">TO formato a ser exportado.</span><span class="sxs-lookup"><span data-stu-id="1883f-131">TThe format to be exported.</span></span> <span data-ttu-id="1883f-132">Atualmente disponível: csv, json.</span><span class="sxs-lookup"><span data-stu-id="1883f-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="1883f-133">O nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="1883f-133">The name of the output file.</span></span>

### <a name="examples"></a><span data-ttu-id="1883f-134">Exemplos</span><span class="sxs-lookup"><span data-stu-id="1883f-134">Examples</span></span>

- <span data-ttu-id="1883f-135">Coletar todos os contadores em um intervalo de atualização de 3 segundos e gerar um csv como saída:</span><span class="sxs-lookup"><span data-stu-id="1883f-135">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="1883f-136">lista dotnet-contadores</span><span class="sxs-lookup"><span data-stu-id="1883f-136">dotnet-counters list</span></span>

<span data-ttu-id="1883f-137">Exibe uma lista de nomes e descrições de contadores, agrupados por provedor.</span><span class="sxs-lookup"><span data-stu-id="1883f-137">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="1883f-138">Sinopse</span><span class="sxs-lookup"><span data-stu-id="1883f-138">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="1883f-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1883f-139">Example</span></span>

```console
> dotnet-counters list

    Showing well-known counters only. Specific processes may support additional counters.
    System.Runtime
        cpu-usage                    Amount of time the process has utilized the CPU (ms)
        working-set                  Amount of working set used by the process (MB)
        gc-heap-size                 Total heap size reported by the GC (MB)
        gen-0-gc-count               Number of Gen 0 GCs / sec
        gen-1-gc-count               Number of Gen 1 GCs / sec
        gen-2-gc-count               Number of Gen 2 GCs / sec
        exception-count              Number of Exceptions / sec
```

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="1883f-140">monitor dotnet-contadores</span><span class="sxs-lookup"><span data-stu-id="1883f-140">dotnet-counters monitor</span></span>

<span data-ttu-id="1883f-141">Exibe valores de atualização periódica dos contadores selecionados.</span><span class="sxs-lookup"><span data-stu-id="1883f-141">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="1883f-142">Sinopse</span><span class="sxs-lookup"><span data-stu-id="1883f-142">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="1883f-143">Opções</span><span class="sxs-lookup"><span data-stu-id="1883f-143">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="1883f-144">A id do processo a ser monitorada.</span><span class="sxs-lookup"><span data-stu-id="1883f-144">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="1883f-145">O número de segundos para atrasar entre a atualização dos contadores exibidos</span><span class="sxs-lookup"><span data-stu-id="1883f-145">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="1883f-146">Uma lista de contadores separados no espaço.</span><span class="sxs-lookup"><span data-stu-id="1883f-146">A space separated list of counters.</span></span> <span data-ttu-id="1883f-147">Os contadores podem `provider_name[:counter_name]`ser especificados .</span><span class="sxs-lookup"><span data-stu-id="1883f-147">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="1883f-148">Se `provider_name` o for usado `counter_name`sem uma qualificação, todos os contadores serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="1883f-148">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="1883f-149">Para descobrir nomes de provedores e contadores, use o comando [dotnet-counters list.](#dotnet-counters-list)</span><span class="sxs-lookup"><span data-stu-id="1883f-149">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="1883f-150">Exemplos</span><span class="sxs-lookup"><span data-stu-id="1883f-150">Examples</span></span>

- <span data-ttu-id="1883f-151">Monitore todos `System.Runtime` os contadores a partir de um intervalo de atualização de 3 segundos:</span><span class="sxs-lookup"><span data-stu-id="1883f-151">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 System.Runtime

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      Working Set (MB)                            1982
      GC Heap Size (MB)                            811
      Gen 0 GC / second                             20
      Gen 1 GC / second                              4
      Gen 2 GC / second                              1
      Number of Exceptions / sec                     4
  ```

- <span data-ttu-id="1883f-152">Monitore apenas o uso `System.Runtime`da CPU e o tamanho do heap GC de:</span><span class="sxs-lookup"><span data-stu-id="1883f-152">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="1883f-153">Monitore `EventCounter` os valores a partir de definidos pelo `EventSource`usuário .</span><span class="sxs-lookup"><span data-stu-id="1883f-153">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="1883f-154">Para obter mais informações, consulte [Tutorial: Como medir o desempenho para eventos muito frequentes usando EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span><span class="sxs-lookup"><span data-stu-id="1883f-154">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a><span data-ttu-id="1883f-155">dotnet-counters ps</span><span class="sxs-lookup"><span data-stu-id="1883f-155">dotnet-counters ps</span></span>

<span data-ttu-id="1883f-156">Exibir uma lista de processos dotnet que podem ser monitorados.</span><span class="sxs-lookup"><span data-stu-id="1883f-156">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="1883f-157">Sinopse</span><span class="sxs-lookup"><span data-stu-id="1883f-157">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="1883f-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1883f-158">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
