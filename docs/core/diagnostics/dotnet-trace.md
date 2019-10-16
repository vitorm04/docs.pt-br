---
title: dotnet-Trace-.NET Core
description: Instalando e usando a ferramenta de linha de comando dotnet-Trace.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: 6513cf63070bc1984006da75313e9912d76a6c95
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321578"
---
# <a name="trace-for-performance-analysis-utility-dotnet-trace"></a>Rastreamento para o utilitário de análise de desempenho (`dotnet-trace`)

**Este artigo aplica-se a:** SDK do .net Core 3,0 e versões posteriores

## <a name="installing-dotnet-trace"></a>Instalando o `dotnet-trace`

Para instalar a versão de lançamento mais recente do [pacote NuGet](https://www.nuget.org/packages/dotnet-trace)`dotnet-trace`, use o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Sinopse

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Descrição

A ferramenta `dotnet-trace` é uma ferramenta global de CLI de plataforma cruzada que permite a coleta de rastreamentos do .NET Core de um processo em execução sem qualquer criador de perfil nativo envolvido. Ele foi criado em relação à tecnologia `EventPipe` de plataforma cruzada do tempo de execução do .NET Core. o `dotnet-trace` oferece a mesma experiência no Windows, Linux ou macOS.

## <a name="options"></a>Opções

- **`--version`**

Exiba a versão do utilitário dotnet-Counters.

- **`-h|--help`**

Mostrar ajuda de linha de comando.

## <a name="commands"></a>Comandos

| Comando                                                     |
| ----------------------------------------------------------- |
| [dotnet-coleta de rastreamento](#dotnet-trace-collect)               |
| [dotnet-conversão de rastreamento](#dotnet-trace-convert)               |
| [dotnet-lista de rastreamento-processos](#dotnet-trace-list-processes) |
| [dotnet-lista de rastreamento-perfis](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a>dotnet-coleta de rastreamento

Coleta um rastreamento de diagnóstico de um processo em execução.

### <a name="synopsis"></a>Sinopse

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a>Opções

- **`-p|--process-id <PID>`**

  O processo do qual coletar o rastreamento.

- **`--buffersize <size>`**

  Define o tamanho do buffer circular na memória em megabytes. 256 MB padrão.

- **`-o|--output <trace-file-path>`**

  O caminho de saída para os dados de rastreamento coletados. Se não for especificado, o padrão será `trace.nettrace`.

- **`--providers <list-of-comma-separated-providers>`**

  Uma lista separada por vírgulas de provedores de `EventPipe` a serem habilitados. Esses provedores complementam todos os provedores implícitos por `--profile <profile-name>`. Se houver alguma inconsistência para um provedor específico, a configuração aqui terá precedência sobre a configuração implícita do perfil.

  Esta lista de provedores está no formato:

  - `Provider[,Provider]`
  - `Provider` está no formato: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.
  - `KeyValueArgs` está no formato: `[key1=value1][;key2=value2]`.

- **`--profile <profile-name>`**

  Um conjunto nomeado predefinido de configurações de provedor que permite que cenários de rastreamento comuns sejam especificados de forma sucinta.

- **`--format <NetTrace|Speedscope>`**

  Define o formato de saída para a conversão do arquivo de rastreamento.

## <a name="dotnet-trace-convert"></a>dotnet-conversão de rastreamento

Converte os rastreamentos `nettrace` em formatos alternativos para uso com ferramentas de análise de rastreamento alternativas.

### <a name="synopsis"></a>Sinopse

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>Arguments

- **`<input-filename>`**

  Arquivo de rastreamento de entrada a ser convertido. O padrão é *trace. NetTrace*.

### <a name="options"></a>Opções

- **`--format <NetTrace|Speedscope>`**

  Define o formato de saída para a conversão do arquivo de rastreamento.

- **`-o|--output <output-filename>`**

  Nome de arquivo de saída. A extensão do formato de destino será adicionada.

## <a name="dotnet-trace-list-processes"></a>dotnet-lista de rastreamento-processos

Lista os processos dotnet que podem ser rastreados.

### <a name="synopsis"></a>Sinopse

```console
dotnet-trace list-processes [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>dotnet-lista de rastreamento-perfis

Lista os perfis de rastreamento pré-criados com uma descrição de quais provedores e filtros estão em cada perfil.

### <a name="synopsis"></a>Sinopse

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Coletar um rastreamento com `dotnet-trace`

- Para coletar rastreamentos usando `dotnet-trace`, você precisará primeiro descobrir o identificador do processo (PID) do aplicativo .NET Core do qual os rastreamentos serão coletados.

  - No Windows, há opções como usar o Gerenciador de tarefas ou o comando `tasklist`.
  - No Linux, a opção trivial poderia usar o comando `ps`.

Você também pode usar o comando [dotnet-Trace List-Processes](#dotnet-trace-list-processes) para descobrir quais processos do .NET Core estão em execução, juntamente com seus PIDs.

- Em seguida, execute o seguinte comando:

```console
> dotnet-trace collect --process-id <PID>

Press <Enter> to exit...
Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
```

- Por fim, interrompa a coleta pressionando a chave `<Enter>` e `dotnet-trace` terminará os eventos de log no arquivo `trace.nettrace`.

## <a name="viewing-the-trace-captured-from-dotnet-trace"></a>Exibindo o rastreamento capturado do `dotnet-trace`

No Windows, os arquivos `.nettrace` podem ser exibidos em [Perfview](https://github.com/microsoft/perfview) para análise, assim como os rastreamentos coletados com o ETW ou o LTTng. Para rastreamentos coletados no Linux, você pode mover o rastreamento para um computador Windows a ser exibido em PerfView.

Você também pode exibir o rastreamento em um computador Linux alterando o formato de saída de `dotnet-trace` para `speedscope`. Você pode alterar o formato do arquivo de saída usando a opção `-f|--format`-`-f speedscope` fará com que `dotnet-trace` gere um arquivo `speedscope`. No momento, você pode escolher entre `nettrace` (a opção padrão) e `speedscope`. os arquivos `Speedscope` podem ser abertos em <https://www.speedscope.app>.

> [!NOTE]
> O tempo de execução do .NET Core gera rastreamentos no formato `nettrace` e eles são convertidos em speedscope (se especificado) após a conclusão do rastreamento. Como algumas conversões podem resultar em perda de dados, o arquivo original `nettrace` é preservado ao lado do arquivo convertido.

## <a name="using-dotnet-trace-to-collect-counter-values-over-time"></a>Usando `dotnet-trace` para coletar valores de contador ao longo do tempo

Se você estiver tentando usar `EventCounter` para o monitoramento de integridade básico em configurações sensíveis ao desempenho, como ambientes de produção e desejar coletar rastreamentos em vez de assisti-los em tempo real, você pode fazer isso com o `dotnet-trace` também.

Por exemplo, se você quiser coletar valores de contador de desempenho de tempo de execução, poderá usar o seguinte comando:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

Esse comando informa os contadores de tempo de execução a serem relatados uma vez a cada segundo para o monitoramento de integridade leve. Substituir `EventCounterIntervalSec=1` por um valor mais alto (por exemplo, 60) permite que você colete um rastreamento menor com menos granularidade nos dados do contador.

Se você quiser desabilitar eventos de tempo de execução para reduzir a sobrecarga (e o tamanho do rastreamento) ainda mais, use o comando a seguir para desabilitar os eventos de tempo de execução e o gerador de perfil de pilha gerenciado.

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

## <a name="net-providers"></a>Provedores .NET

O tempo de execução do .NET Core dá suporte aos provedores .NET a seguir. O .NET Core usa as mesmas palavras-chave para habilitar rastreamentos `Event Tracing for Windows (ETW)` e `EventPipe`.

| Nome do provedor                            | Informações |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [O provedor de tempo de execução](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Palavras-chave de tempo de execução CLR](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [O provedor de encerramento](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Palavras-chave de resumo do CLR](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Habilita o criador de perfil de exemplo. |
