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
# <a name="dotnet-counters"></a>dotnet-counters

**Este artigo se aplica a:** ✔️ .NET Core 3.0 SDK e versões posteriores

## <a name="install-dotnet-counters"></a>Instale contadores de dotnet

Para instalar a versão `dotnet-counters` de versão mais recente do [pacote NuGet,](https://www.nuget.org/packages/dotnet-counters)use o comando [dotnet tool install:](../tools/dotnet-tool-install.md)

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>Sinopse

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Descrição

`dotnet-counters`é uma ferramenta de monitoramento de desempenho para monitoramento de saúde ad-hoc e investigação de desempenho de primeiro nível. Ele pode observar valores de <xref:System.Diagnostics.Tracing.EventCounter> contador de desempenho que são publicados através da API. Por exemplo, você pode monitorar rapidamente coisas como o uso da CPU ou a taxa de exceções que estão sendo `PerfView` lançadas em seu aplicativo .NET Core para ver se há algo suspeito antes de mergulhar em uma investigação de desempenho mais séria usando ou `dotnet-trace`.

## <a name="options"></a>Opções

- **`--version`**

  Exibe a versão do utilitário dotnet-counters.

- **`-h|--help`**

  Mostra ajuda na linha de comando.

## <a name="commands"></a>Comandos

| Comando                                             |
| --------------------------------------------------- |
| [dotnet-contadores coletar](#dotnet-counters-collect) |
| [lista dotnet-contadores](#dotnet-counters-list)       |
| [monitor dotnet-contadores](#dotnet-counters-monitor) |
| [dotnet-counters ps](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a>dotnet-contadores coletar

Coletar periodicamente os valores do contador selecionados e exportá-los para um formato de arquivo especificado para pós-processamento.

### <a name="synopsis"></a>Sinopse

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a>Opções

- **`-p|--process-id <PID>`**

  A id do processo a ser monitorada.

- **`--refresh-interval <SECONDS>`**

  O número de segundos para atrasar entre a atualização dos contadores exibidos

- **`counter_list <COUNTERS>`**

  Uma lista de contadores separados no espaço. Os contadores podem `provider_name[:counter_name]`ser especificados . Se `provider_name` o for usado `counter_name`sem uma qualificação, todos os contadores serão mostrados. Para descobrir nomes de provedores e contadores, use o comando [dotnet-counters list.](#dotnet-counters-list)

- **`--format <csv|json>`**

  TO formato a ser exportado. Atualmente disponível: csv, json.

- **`-o|--output <output>`**

  O nome do arquivo de saída.

### <a name="examples"></a>Exemplos

- Coletar todos os contadores em um intervalo de atualização de 3 segundos e gerar um csv como saída:

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a>lista dotnet-contadores

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

## <a name="dotnet-counters-monitor"></a>monitor dotnet-contadores

Exibe valores de atualização periódica dos contadores selecionados.

### <a name="synopsis"></a>Sinopse

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a>Opções

- **`-p|--process-id <PID>`**

  A id do processo a ser monitorada.

- **`--refresh-interval <SECONDS>`**

  O número de segundos para atrasar entre a atualização dos contadores exibidos

- **`counter_list <COUNTERS>`**

  Uma lista de contadores separados no espaço. Os contadores podem `provider_name[:counter_name]`ser especificados . Se `provider_name` o for usado `counter_name`sem uma qualificação, todos os contadores serão mostrados. Para descobrir nomes de provedores e contadores, use o comando [dotnet-counters list.](#dotnet-counters-list)

### <a name="examples"></a>Exemplos

- Monitore todos `System.Runtime` os contadores a partir de um intervalo de atualização de 3 segundos:

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

- Monitore apenas o uso `System.Runtime`da CPU e o tamanho do heap GC de:

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- Monitore `EventCounter` os valores a partir de definidos pelo `EventSource`usuário . Para obter mais informações, consulte [Tutorial: Como medir o desempenho para eventos muito frequentes usando EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a>dotnet-counters ps

Exibir uma lista de processos dotnet que podem ser monitorados.

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
