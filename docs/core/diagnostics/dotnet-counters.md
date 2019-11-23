---
title: dotnet-contadores-.NET Core
description: Saiba como instalar e usar a ferramenta de linha de comando dotnet-Counter.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: b2fab239713d9d19c580580496e73a91ceafcc52
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321585"
---
# <a name="dotnet-counters"></a><span data-ttu-id="c9e38-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="c9e38-103">dotnet-counters</span></span>

<span data-ttu-id="c9e38-104">**Este artigo aplica-se a: ✓ o** SDK do .net Core 3,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="c9e38-104">**This article applies to: ✓** .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="c9e38-105">Instalar dotnet-contadores</span><span class="sxs-lookup"><span data-stu-id="c9e38-105">Install dotnet-counters</span></span>

<span data-ttu-id="c9e38-106">Para instalar a versão de lançamento mais recente do [pacote NuGet](https://www.nuget.org/packages/dotnet-counters)`dotnet-counters`, use o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="c9e38-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="c9e38-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="c9e38-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="c9e38-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9e38-108">Description</span></span>

<span data-ttu-id="c9e38-109">`dotnet-counters` é uma ferramenta de monitoramento de desempenho para monitoramento de integridade ad hoc e investigação de desempenho de primeiro nível.</span><span class="sxs-lookup"><span data-stu-id="c9e38-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="c9e38-110">Ele pode observar os valores do contador de desempenho que são publicados por meio da API <xref:System.Diagnostics.Tracing.EventCounter>.</span><span class="sxs-lookup"><span data-stu-id="c9e38-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="c9e38-111">Por exemplo, você pode monitorar rapidamente coisas como o uso da CPU ou a taxa de exceções sendo geradas em seu aplicativo .NET Core para ver se há algo suspeito antes de mergulhar em uma investigação de desempenho mais séria usando `PerfView` ou `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="c9e38-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="c9e38-112">Opções</span><span class="sxs-lookup"><span data-stu-id="c9e38-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="c9e38-113">Exibe a versão do utilitário dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="c9e38-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c9e38-114">Mostra a ajuda da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c9e38-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="c9e38-115">Commands</span><span class="sxs-lookup"><span data-stu-id="c9e38-115">Commands</span></span>

| <span data-ttu-id="c9e38-116">{1&gt;Comando&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c9e38-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="c9e38-117">dotnet – lista de contadores</span><span class="sxs-lookup"><span data-stu-id="c9e38-117">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="c9e38-118">dotnet – monitor de contadores</span><span class="sxs-lookup"><span data-stu-id="c9e38-118">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |

## <a name="dotnet-counters-list"></a><span data-ttu-id="c9e38-119">dotnet – lista de contadores</span><span class="sxs-lookup"><span data-stu-id="c9e38-119">dotnet-counters list</span></span>

<span data-ttu-id="c9e38-120">Exibe uma lista de nomes e descrições de contadores, agrupados por provedor.</span><span class="sxs-lookup"><span data-stu-id="c9e38-120">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="c9e38-121">Sinopse</span><span class="sxs-lookup"><span data-stu-id="c9e38-121">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="c9e38-122">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c9e38-122">Example</span></span>

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

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="c9e38-123">dotnet – monitor de contadores</span><span class="sxs-lookup"><span data-stu-id="c9e38-123">dotnet-counters monitor</span></span>

<span data-ttu-id="c9e38-124">Exibe a atualização periódica de valores dos contadores selecionados.</span><span class="sxs-lookup"><span data-stu-id="c9e38-124">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="c9e38-125">Sinopse</span><span class="sxs-lookup"><span data-stu-id="c9e38-125">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="c9e38-126">Opções</span><span class="sxs-lookup"><span data-stu-id="c9e38-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="c9e38-127">A ID do processo a ser monitorado.</span><span class="sxs-lookup"><span data-stu-id="c9e38-127">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="c9e38-128">O número de segundos de atraso entre a atualização dos contadores exibidos</span><span class="sxs-lookup"><span data-stu-id="c9e38-128">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="c9e38-129">Uma lista de contadores separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="c9e38-129">A space separated list of counters.</span></span> <span data-ttu-id="c9e38-130">Os contadores podem ser especificados `provider_name[:counter_name]`.</span><span class="sxs-lookup"><span data-stu-id="c9e38-130">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="c9e38-131">Se o `provider_name` for usado sem uma `counter_name`de qualificação, todos os contadores serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="c9e38-131">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="c9e38-132">Para descobrir os nomes de provedor e contador, use o comando [dotnet-Counters List](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="c9e38-132">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="c9e38-133">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c9e38-133">Examples</span></span>

- <span data-ttu-id="c9e38-134">Monitorar todos os contadores de `System.Runtime` em um intervalo de atualização de 3 segundos:</span><span class="sxs-lookup"><span data-stu-id="c9e38-134">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="c9e38-135">Monitorar apenas o uso da CPU e o tamanho do heap do GC de `System.Runtime`:</span><span class="sxs-lookup"><span data-stu-id="c9e38-135">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="c9e38-136">Monitorar `EventCounter` valores de `EventSource`definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="c9e38-136">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="c9e38-137">Para obter mais informações, consulte [tutorial: como medir o desempenho de eventos muito frequentes usando o EventCounters](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span><span class="sxs-lookup"><span data-stu-id="c9e38-137">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
