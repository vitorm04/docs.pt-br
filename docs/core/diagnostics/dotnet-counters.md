---
title: dotnet-contadores-.NET Core
description: Saiba como instalar e usar a ferramenta de linha de comando dotnet-Counter.
ms.date: 10/14/2019
ms.openlocfilehash: 399d5908e8ac52bcd4a20c1a819fc6c99f4de2f4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737713"
---
# <a name="dotnet-counters"></a>dotnet-counters

**Este artigo aplica-se a:** ✔️ SDK do .net Core 3,0 e versões posteriores

## <a name="install-dotnet-counters"></a>Instalar dotnet-contadores

Para instalar a versão de lançamento mais recente do [pacote NuGet](https://www.nuget.org/packages/dotnet-counters)`dotnet-counters`, use o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>Sinopse

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Descrição

`dotnet-counters` é uma ferramenta de monitoramento de desempenho para monitoramento de integridade ad hoc e investigação de desempenho de primeiro nível. Ele pode observar os valores do contador de desempenho que são publicados por meio da API <xref:System.Diagnostics.Tracing.EventCounter>. Por exemplo, você pode monitorar rapidamente coisas como o uso da CPU ou a taxa de exceções sendo geradas em seu aplicativo .NET Core para ver se há algo suspeito antes de mergulhar em uma investigação de desempenho mais séria usando `PerfView` ou `dotnet-trace`.

## <a name="options"></a>Opções

- **`--version`**

  Exibe a versão do utilitário dotnet-Counters.

- **`-h|--help`**

  Mostra a ajuda da linha de comando.

## <a name="commands"></a>Comandos

| {1&gt;Comando&lt;1}                                             |
| --------------------------------------------------- |
| [dotnet – lista de contadores](#dotnet-counters-list)       |
| [dotnet – monitor de contadores](#dotnet-counters-monitor) |

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
        cpu-usage                    Amount of time the process has utilized the CPU (ms)
        working-set                  Amount of working set used by the process (MB)
        gc-heap-size                 Total heap size reported by the GC (MB)
        gen-0-gc-count               Number of Gen 0 GCs / sec
        gen-1-gc-count               Number of Gen 1 GCs / sec
        gen-2-gc-count               Number of Gen 2 GCs / sec
        exception-count              Number of Exceptions / sec
```

## <a name="dotnet-counters-monitor"></a>dotnet – monitor de contadores

Exibe a atualização periódica de valores dos contadores selecionados.

### <a name="synopsis"></a>Sinopse

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a>Opções

- **`-p|--process-id <PID>`**

  A ID do processo a ser monitorado.

- **`--refresh-interval <SECONDS>`**

  O número de segundos de atraso entre a atualização dos contadores exibidos

- **`counter_list <COUNTERS>`**

  Uma lista de contadores separados por espaços. Os contadores podem ser especificados `provider_name[:counter_name]`. Se o `provider_name` for usado sem uma `counter_name`de qualificação, todos os contadores serão mostrados. Para descobrir os nomes de provedor e contador, use o comando [dotnet-Counters List](#dotnet-counters-list) .

### <a name="examples"></a>Exemplos

- Monitorar todos os contadores de `System.Runtime` em um intervalo de atualização de 3 segundos:

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

- Monitorar apenas o uso da CPU e o tamanho do heap do GC de `System.Runtime`:

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- Monitorar `EventCounter` valores de `EventSource`definidos pelo usuário. Para obter mais informações, consulte [tutorial: como medir o desempenho de eventos muito frequentes usando o EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
