---
title: ferramenta dotnet-trace - .NET Core
description: Instalando e usando a ferramenta de linha de comando dotnet-trace.
ms.date: 11/21/2019
ms.openlocfilehash: b19b159636fbf57fa2d461b398fcf9234aab491c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737654"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>utilitário de análise de desempenho dotnet-trace

**Este artigo se aplica a:** ✔️ .NET Core 3.0 SDK e versões posteriores

## <a name="install-dotnet-trace"></a>Instale o dotnet-trace

Instale `dotnet-trace` [o pacote NuGet](https://www.nuget.org/packages/dotnet-trace) com o comando de instalação da ferramenta [dotnet:](../tools/dotnet-tool-install.md)

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Sinopse

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Descrição

A `dotnet-trace` ferramenta:

* É uma ferramenta multiplataforma .NET Core.
* Habilita a coleta de traços .NET Core de um processo em execução sem um profiler nativo.
* É construído em torno `EventPipe` da tecnologia multiplataforma do tempo de execução .NET Core.
* Oferece a mesma experiência no Windows, Linux ou macOS.

## <a name="options"></a>Opções

- **`--version`**

  Exibe a versão do utilitário dotnet-counters.

- **`-h|--help`**

  Mostra ajuda na linha de comando.

## <a name="commands"></a>Comandos

| Comando                                                     |
| ----------------------------------------------------------- |
| [dotnet-trace coletar](#dotnet-trace-collect)               |
| [dotnet-trace converter](#dotnet-trace-convert)               |
| [dotnet-trace ps](#dotnet-trace-ps) |
| [dotnet-trace list-profiles](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a>dotnet-trace coletar

Coleta um traço de diagnóstico de um processo em execução.

### <a name="synopsis"></a>Sinopse

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a>Opções

- **`-p|--process-id <PID>`**

  O processo para coletar o rastro de.

- **`--buffersize <size>`**

  Define o tamanho do buffer circular na memória, em megabytes. Padrão 256 MB.

- **`-o|--output <trace-file-path>`**

  O caminho de saída para os dados de rastreamento coletados. Se não especificado, `trace.nettrace`ele é padrão para .

- **`--providers <list-of-comma-separated-providers>`**

  Uma lista separada por comma de `EventPipe` provedores a serem habilitados. Esses provedores complementam `--profile <profile-name>`quaisquer provedores implícitos por . Se houver alguma inconsistência para um determinado provedor, essa configuração tem precedência sobre a configuração implícita do perfil.

  Esta lista de provedores está no formulário:

  - `Provider[,Provider]`
  - `Provider`está na forma: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.
  - `KeyValueArgs`está na forma: `[key1=value1][;key2=value2]`.

- **`--profile <profile-name>`**

  Um conjunto predefinido de configurações do provedor que permite que cenários comuns de rastreamento sejam especificados de forma sucinta.

- **`--format {NetTrace|Speedscope}`**

  Define o formato de saída para a conversão do arquivo de rastreamento. O padrão é `NetTrace`.

## <a name="dotnet-trace-convert"></a>dotnet-trace converter

Converte `nettrace` traços em formatos alternativos para uso com ferramentas alternativas de análise de rastreamento.

### <a name="synopsis"></a>Sinopse

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>Argumentos

- **`<input-filename>`**

  Arquivo de rastreamento de entrada a ser convertido. Padrão para *trace.nettrace*.

### <a name="options"></a>Opções

- **`--format <NetTrace|Speedscope>`**

  Define o formato de saída para a conversão do arquivo de rastreamento.

- **`-o|--output <output-filename>`**

  Nome do arquivo de saída. A extensão do formato de destino será adicionada.

## <a name="dotnet-trace-ps"></a>dotnet-trace ps

Lista processos dotnet que podem ser anexados.

### <a name="synopsis"></a>Sinopse

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>dotnet-trace list-profiles

Lista perfis de rastreamento pré-construídos com uma descrição de quais provedores e filtros estão em cada perfil.

### <a name="synopsis"></a>Sinopse

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Coletar um traço com dotnet-trace

Para coletar vestígios usando: `dotnet-trace`

- Obtenha o identificador de processo (PID) do aplicativo .NET Core para coletar vestígios.

  - No Windows, você pode usar `tasklist` o Gerenciador de Tarefas ou o comando, por exemplo.
  - No Linux, por `ps` exemplo, o comando.
  - [dotnet-trace ps](#dotnet-trace-ps)

- Execute o comando a seguir:

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  O comando anterior gera saída semelhante à seguinte:

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- Pare a coleta `<Enter>` pressionando a tecla. `dotnet-trace`terminará o registro de eventos no arquivo *trace.nettrace.*

## <a name="view-the-trace-captured-from-dotnet-trace"></a>Veja o vestígio capturado a partir do dotnet-trace

No Windows, arquivos *.nettrace* podem ser visualizados no [PerfView](https://github.com/microsoft/perfview) para análise: Para rastreamentos coletados em outras plataformas, o arquivo de rastreamento pode ser movido para uma máquina windows para ser visualizado no PerfView.

No Linux, o trace pode ser visualizado alterando o formato de saída de `dotnet-trace` . `speedscope` O formato do arquivo de `-f|--format` saída `-f speedscope` pode `dotnet-trace` ser `speedscope` alterado usando a opção - fará produzir um arquivo. Você pode `nettrace` escolher entre (a `speedscope`opção padrão) e . `Speedscope`arquivos podem ser <https://www.speedscope.app>abertos em .

> [!NOTE]
> O tempo de execução do `nettrace` .NET Core gera traços no formato. Os traços são convertidos em speedscope (se especificado) após a conclusão do rastreamento. Uma vez que algumas conversões podem `nettrace` resultar em perda de dados, o arquivo original é preservado ao lado do arquivo convertido.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Use dotnet-trace para coletar valores de contador ao longo do tempo

`dotnet-trace`Cna:

* Uso `EventCounter` para monitoramento básico de saúde em ambientes sensíveis ao desempenho. Por exemplo, na produção.
* Colete vestígios para que não precisem ser vistos em tempo real.

Por exemplo, para coletar valores do contador de desempenho em tempo de execução, use o seguinte comando:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

O comando precede diz aos contadores de tempo de execução que informem uma vez a cada segundo para o monitoramento leve da saúde. A `EventCounterIntervalSec=1` substituição por um valor mais alto (por exemplo, 60) permite a coleta de um traço menor com menos granularidade nos dados do contador.

O comando a seguir reduz o tamanho da sobrecarga e do rastreamento mais do que o anterior:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

O comando anterior desativa eventos de tempo de execução e o profiler de pilha gerenciado.

## <a name="net-providers"></a>.NET Provedores

O tempo de execução do .NET Core suporta os seguintes provedores .NET. .NET Core usa as mesmas `Event Tracing for Windows (ETW)` `EventPipe` palavras-chave para habilitar ambos e traços.

| Nome do provedor                            | Informações |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [O provedor de runtime](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Palavras-chave clr runtime](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [O provedor de encerramento](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Palavras-chave clr rundown](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Habilita o profiler de amostra. |
