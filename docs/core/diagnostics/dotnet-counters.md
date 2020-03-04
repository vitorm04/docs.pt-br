---
title: dotnet-contadores-.NET Core
description: Saiba como instalar e usar a ferramenta de linha de comando dotnet-Counter.
ms.date: 02/26/2020
ms.openlocfilehash: 88f701a60d0ee03dd0236ae54c57679943e14939
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157876"
---
# <a name="dotnet-counters"></a><span data-ttu-id="06b86-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="06b86-103">dotnet-counters</span></span>

<span data-ttu-id="06b86-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 3,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="06b86-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="06b86-105">Instalar dotnet-contadores</span><span class="sxs-lookup"><span data-stu-id="06b86-105">Install dotnet-counters</span></span>

<span data-ttu-id="06b86-106">Para instalar a versão de lançamento mais recente do [pacote NuGet](https://www.nuget.org/packages/dotnet-counters)`dotnet-counters`, use o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="06b86-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="06b86-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="06b86-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="06b86-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="06b86-108">Description</span></span>

<span data-ttu-id="06b86-109">`dotnet-counters` é uma ferramenta de monitoramento de desempenho para monitoramento de integridade ad hoc e investigação de desempenho de primeiro nível.</span><span class="sxs-lookup"><span data-stu-id="06b86-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="06b86-110">Ele pode observar os valores do contador de desempenho que são publicados por meio da API <xref:System.Diagnostics.Tracing.EventCounter>.</span><span class="sxs-lookup"><span data-stu-id="06b86-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="06b86-111">Por exemplo, você pode monitorar rapidamente coisas como o uso da CPU ou a taxa de exceções sendo geradas em seu aplicativo .NET Core para ver se há algo suspeito antes de mergulhar em uma investigação de desempenho mais séria usando `PerfView` ou `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="06b86-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="06b86-112">Opções</span><span class="sxs-lookup"><span data-stu-id="06b86-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="06b86-113">Exibe a versão do utilitário dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="06b86-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="06b86-114">Mostra a ajuda da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="06b86-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="06b86-115">Comandos</span><span class="sxs-lookup"><span data-stu-id="06b86-115">Commands</span></span>

| <span data-ttu-id="06b86-116">Comando</span><span class="sxs-lookup"><span data-stu-id="06b86-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="06b86-117">dotnet – coleta de contadores</span><span class="sxs-lookup"><span data-stu-id="06b86-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="06b86-118">dotnet – lista de contadores</span><span class="sxs-lookup"><span data-stu-id="06b86-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="06b86-119">dotnet – monitor de contadores</span><span class="sxs-lookup"><span data-stu-id="06b86-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="06b86-120">dotnet-contadores PS</span><span class="sxs-lookup"><span data-stu-id="06b86-120">dotnet-counters ps</span></span>](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="06b86-121">dotnet – coleta de contadores</span><span class="sxs-lookup"><span data-stu-id="06b86-121">dotnet-counters collect</span></span>

<span data-ttu-id="06b86-122">Coletar periodicamente os valores de contador selecionados e exportá-los para um formato de arquivo especificado para o pós-processamento.</span><span class="sxs-lookup"><span data-stu-id="06b86-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="06b86-123">Sinopse</span><span class="sxs-lookup"><span data-stu-id="06b86-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a><span data-ttu-id="06b86-124">Opções</span><span class="sxs-lookup"><span data-stu-id="06b86-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="06b86-125">A ID do processo a ser monitorado.</span><span class="sxs-lookup"><span data-stu-id="06b86-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="06b86-126">O número de segundos de atraso entre a atualização dos contadores exibidos</span><span class="sxs-lookup"><span data-stu-id="06b86-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="06b86-127">Uma lista de contadores separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="06b86-127">A space separated list of counters.</span></span> <span data-ttu-id="06b86-128">Os contadores podem ser especificados `provider_name[:counter_name]`.</span><span class="sxs-lookup"><span data-stu-id="06b86-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="06b86-129">Se o `provider_name` for usado sem uma `counter_name`de qualificação, todos os contadores serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="06b86-129">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="06b86-130">Para descobrir os nomes de provedor e contador, use o comando [dotnet-Counters List](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="06b86-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="06b86-131">Formato Tnão a ser exportado.</span><span class="sxs-lookup"><span data-stu-id="06b86-131">TThe format to be exported.</span></span> <span data-ttu-id="06b86-132">Atualmente disponível: CSV, JSON.</span><span class="sxs-lookup"><span data-stu-id="06b86-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="06b86-133">O nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="06b86-133">The name of the output file.</span></span>

### <a name="examples"></a><span data-ttu-id="06b86-134">Exemplos</span><span class="sxs-lookup"><span data-stu-id="06b86-134">Examples</span></span>

- <span data-ttu-id="06b86-135">Colete todos os contadores em um intervalo de atualização de 3 segundos e gere um CSV como saída:</span><span class="sxs-lookup"><span data-stu-id="06b86-135">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="06b86-136">dotnet – lista de contadores</span><span class="sxs-lookup"><span data-stu-id="06b86-136">dotnet-counters list</span></span>

<span data-ttu-id="06b86-137">Exibe uma lista de nomes e descrições de contadores, agrupados por provedor.</span><span class="sxs-lookup"><span data-stu-id="06b86-137">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="06b86-138">Sinopse</span><span class="sxs-lookup"><span data-stu-id="06b86-138">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="06b86-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06b86-139">Example</span></span>

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

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="06b86-140">dotnet – monitor de contadores</span><span class="sxs-lookup"><span data-stu-id="06b86-140">dotnet-counters monitor</span></span>

<span data-ttu-id="06b86-141">Exibe a atualização periódica de valores dos contadores selecionados.</span><span class="sxs-lookup"><span data-stu-id="06b86-141">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="06b86-142">Sinopse</span><span class="sxs-lookup"><span data-stu-id="06b86-142">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="06b86-143">Opções</span><span class="sxs-lookup"><span data-stu-id="06b86-143">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="06b86-144">A ID do processo a ser monitorado.</span><span class="sxs-lookup"><span data-stu-id="06b86-144">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="06b86-145">O número de segundos de atraso entre a atualização dos contadores exibidos</span><span class="sxs-lookup"><span data-stu-id="06b86-145">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="06b86-146">Uma lista de contadores separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="06b86-146">A space separated list of counters.</span></span> <span data-ttu-id="06b86-147">Os contadores podem ser especificados `provider_name[:counter_name]`.</span><span class="sxs-lookup"><span data-stu-id="06b86-147">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="06b86-148">Se o `provider_name` for usado sem uma `counter_name`de qualificação, todos os contadores serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="06b86-148">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="06b86-149">Para descobrir os nomes de provedor e contador, use o comando [dotnet-Counters List](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="06b86-149">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="06b86-150">Exemplos</span><span class="sxs-lookup"><span data-stu-id="06b86-150">Examples</span></span>

- <span data-ttu-id="06b86-151">Monitorar todos os contadores de `System.Runtime` em um intervalo de atualização de 3 segundos:</span><span class="sxs-lookup"><span data-stu-id="06b86-151">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="06b86-152">Monitorar apenas o uso da CPU e o tamanho do heap do GC de `System.Runtime`:</span><span class="sxs-lookup"><span data-stu-id="06b86-152">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="06b86-153">Monitorar `EventCounter` valores de `EventSource`definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="06b86-153">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="06b86-154">Para obter mais informações, consulte [tutorial: como medir o desempenho de eventos muito frequentes usando o EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span><span class="sxs-lookup"><span data-stu-id="06b86-154">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a><span data-ttu-id="06b86-155">dotnet-contadores PS</span><span class="sxs-lookup"><span data-stu-id="06b86-155">dotnet-counters ps</span></span> 

<span data-ttu-id="06b86-156">Exibe uma lista de processos dotnet que podem ser monitorados.</span><span class="sxs-lookup"><span data-stu-id="06b86-156">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="06b86-157">Sinopse</span><span class="sxs-lookup"><span data-stu-id="06b86-157">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="06b86-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06b86-158">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
