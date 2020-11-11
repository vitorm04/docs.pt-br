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
# <a name="dotnet-counters"></a>dotnet-counters

**Este artigo aplica-se a:** ✔️ SDK do .net Core 3,0 e versões posteriores

## <a name="install-dotnet-counters"></a>Instalar dotnet-contadores

Para instalar a versão de lançamento mais recente do `dotnet-counters` [pacote NuGet](https://www.nuget.org/packages/dotnet-counters), use o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>Sinopse

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Descrição

`dotnet-counters` é uma ferramenta de monitoramento de desempenho para monitoramento de integridade ad hoc e investigação de desempenho de primeiro nível. Ele pode observar os valores do contador de desempenho que são publicados por meio da <xref:System.Diagnostics.Tracing.EventCounter> API. Por exemplo, você pode monitorar rapidamente coisas como o uso da CPU ou a taxa de exceções que estão sendo geradas em seu aplicativo .NET Core para ver se há algo suspeito antes de mergulhar em uma investigação de desempenho mais séria usando o `PerfView` ou o `dotnet-trace` .

## <a name="options"></a>Opções

- **`--version`**

  Exibe a versão do utilitário dotnet-Counters.

- **`-h|--help`**

  Mostra a ajuda da linha de comando.

## <a name="commands"></a>Comandos

| Comando                                             |
|-----------------------------------------------------|
| [dotnet – coleta de contadores](#dotnet-counters-collect) |
| [dotnet – lista de contadores](#dotnet-counters-list)       |
| [dotnet – monitor de contadores](#dotnet-counters-monitor) |
| [dotnet-contadores PS](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a>dotnet – coleta de contadores

Coletar periodicamente os valores de contador selecionados e exportá-los para um formato de arquivo especificado para o pós-processamento.

### <a name="synopsis"></a>Sinopse

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a>Opções

- **`-p|--process-id <PID>`**

  A ID do processo a ser monitorado.

- **`--refresh-interval <SECONDS>`**

  O número de segundos de atraso entre a atualização dos contadores exibidos

- **`--counters <COUNTERS>`**

  Uma lista separada por vírgulas de contadores. Os contadores podem ser especificados `provider_name[:counter_name]` . Se o `provider_name` for usado sem uma lista de contadores de qualificação, todos os contadores do provedor serão mostrados. Para descobrir os nomes de provedor e contador, use o comando [dotnet-Counters List](#dotnet-counters-list) .

- **`--format <csv|json>`**

  O formato a ser exportado. Atualmente disponível: CSV, JSON.

- **`-o|--output <output>`**

  O nome do arquivo de saída.

- **`-- <command>` (para aplicativos de destino que executam o .NET 5,0 ou posterior somente)**

  Após os parâmetros de configuração da coleção, o usuário pode acrescentar `--` seguido por um comando para iniciar um aplicativo .NET com pelo menos um tempo de execução de 5,0. `dotnet-counters` o iniciará um processo com o comando fornecido e coletará as métricas solicitadas. Isso geralmente é útil para coletar métricas para o caminho de inicialização do aplicativo e pode ser usado para diagnosticar ou monitorar problemas que ocorrem antes ou logo após o ponto de entrada principal.

> [!NOTE]
> O uso dessa opção monitora o primeiro processo do .NET 5,0 que se comunica de volta à ferramenta, o que significa que, se o comando iniciar vários aplicativos .NET, ele só coletará o primeiro aplicativo. Portanto, é recomendável usar essa opção em aplicativos independentes ou usando a `dotnet exec <app.dll>` opção.

### <a name="examples"></a>Exemplos

- Colete todos os contadores em um intervalo de atualização de 3 segundos e gere um CSV como saída:

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- Inicie `dotnet mvc.dll` o como um processo filho e comece a coletar contadores de tempo de execução e ASP.NET Core contadores de hospedagem da inicialização e salve-os como uma saída JSON:

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a>dotnet – lista de contadores

Exibe uma lista de nomes e descrições de contadores, agrupados por provedor.

### <a name="synopsis"></a>Sinopse

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a>Exemplo

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
> Os `Microsoft.AspNetCore.Hosting` contadores são exibidos quando há processos identificados que dão suporte a esses contadores, por exemplo, quando um aplicativo ASP.NET Core está em execução no computador host.

## <a name="dotnet-counters-monitor"></a>dotnet – monitor de contadores

Exibe a atualização periódica de valores dos contadores selecionados.

### <a name="synopsis"></a>Sinopse

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [--counters] [-- <command>]
```

### <a name="options"></a>Opções

- **`-p|--process-id <PID>`**

  A ID do processo a ser monitorado.

- **`--refresh-interval <SECONDS>`**

  O número de segundos de atraso entre a atualização dos contadores exibidos

- **`--counters <COUNTERS>`**

  Uma lista separada por vírgulas de contadores. Os contadores podem ser especificados `provider_name[:counter_name]` . Se o `provider_name` for usado sem uma lista de contadores de qualificação, todos os contadores do provedor serão mostrados. Para descobrir os nomes de provedor e contador, use o comando [dotnet-Counters List](#dotnet-counters-list) .

 **`-- <command>` (para aplicativos de destino que executam o .NET 5,0 ou posterior somente)**

  Após os parâmetros de configuração da coleção, o usuário pode acrescentar `--` seguido por um comando para iniciar um aplicativo .NET com pelo menos um tempo de execução de 5,0. `dotnet-counters` o iniciará um processo com o comando fornecido e monitorará as métricas solicitadas. Isso geralmente é útil para coletar métricas para o caminho de inicialização do aplicativo e pode ser usado para diagnosticar ou monitorar problemas que ocorrem antes ou logo após o ponto de entrada principal.

  > [!NOTE]
  > O uso dessa opção monitora o primeiro processo do .NET 5,0 que se comunica de volta à ferramenta, o que significa que, se o comando iniciar vários aplicativos .NET, ele só coletará o primeiro aplicativo. Portanto, é recomendável usar essa opção em aplicativos independentes ou usando a `dotnet exec <app.dll>` opção.

### <a name="examples"></a>Exemplos

- Monitorar todos os contadores de `System.Runtime` em um intervalo de atualização de 3 segundos:

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

- Monitorar apenas o uso da CPU e o tamanho do heap do GC de `System.Runtime` :

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- Monitorar `EventCounter` valores de definidos pelo usuário `EventSource` . Para obter mais informações, consulte [tutorial: medir o desempenho usando o EventCounters no .NET Core](event-counter-perf.md).

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- Inicie `my-aspnet-server.exe` e monitore o número de assemblies carregados a partir de sua inicialização (somente .net 5,0 ou posterior):

  Observação: isso funciona somente para aplicativos que executam o .NET 5,0 ou posterior.

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- Inicie `my-aspnet-server.exe` com `arg1` e `arg2` como argumentos de linha de comando e monitore seu conjunto de trabalho e o tamanho do heap de GC de sua inicialização (somente .NET 5,0 ou posterior):

  Observação: isso funciona somente para aplicativos que executam o .NET 5,0 ou posterior.

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

## <a name="dotnet-counters-ps"></a>dotnet-contadores PS

Exibe uma lista de processos dotnet que podem ser monitorados.

### <a name="synopsis"></a>Sinopse

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a>Exemplo

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
