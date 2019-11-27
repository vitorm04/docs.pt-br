---
title: dotnet-ferramenta de rastreamento-.NET Core
description: Instalando e usando a ferramenta de linha de comando dotnet-Trace.
author: sdmaclea
ms.author: stmaclea
ms.date: 11/21/2019
ms.openlocfilehash: 07eaec843e27f5d291b6d18fab53c43051794626
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428886"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>dotnet-utilitário de análise de desempenho de rastreamento

**Este artigo aplica-se a: ✓ o** SDK do .net Core 3,0 e versões posteriores

## <a name="install-dotnet-trace"></a>Instalar dotnet-Trace

Instale `dotnet-trace` [pacote NuGet](https://www.nuget.org/packages/dotnet-trace) com o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Sinopse

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Descrição

A ferramenta de `dotnet-trace`:

* É uma ferramenta .NET Core de plataforma cruzada.
* Habilita a coleção de rastreamentos do .NET Core de um processo em execução sem um criador de perfil nativo.
* O é criado em relação à tecnologia de `EventPipe` entre plataformas do tempo de execução do .NET Core.
* Oferece a mesma experiência no Windows, Linux ou macOS.

## <a name="options"></a>Opções

- **`--version`**  

  Exibe a versão do utilitário dotnet-Counters.

- **`-h|--help`**

  Mostra a ajuda da linha de comando.

## <a name="commands"></a>Comandos

| Command                                                     |
| ----------------------------------------------------------- |
| [dotnet-coleta de rastreamento](#dotnet-trace-collect)               |
| [dotnet-conversão de rastreamento](#dotnet-trace-convert)               |
| [dotnet-rastrear PS](#dotnet-trace-ps) |
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

  Define o tamanho do buffer circular na memória, em megabytes. 256 MB padrão.

- **`-o|--output <trace-file-path>`**

  O caminho de saída para os dados de rastreamento coletados. Se não for especificado, o padrão será `trace.nettrace`.

- **`--providers <list-of-comma-separated-providers>`**

  Uma lista separada por vírgulas de provedores de `EventPipe` a serem habilitados. Esses provedores complementam todos os provedores implícitos por `--profile <profile-name>`. Se houver alguma inconsistência para um provedor específico, essa configuração terá precedência sobre a configuração implícita do perfil.

  Esta lista de provedores está no formato:

  - `Provider[,Provider]`
  - `Provider` está no formato: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.
  - `KeyValueArgs` está no formato: `[key1=value1][;key2=value2]`.

- **`--profile <profile-name>`**

  Um conjunto nomeado predefinido de configurações de provedor que permite que cenários de rastreamento comuns sejam especificados de forma sucinta.

- **`--format {NetTrace|Speedscope}`**

  Define o formato de saída para a conversão do arquivo de rastreamento. O padrão é `NetTrace`.

## <a name="dotnet-trace-convert"></a>dotnet-conversão de rastreamento

Converte `nettrace` rastreamentos em formatos alternativos para uso com ferramentas de análise de rastreamento alternativas.

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

## <a name="dotnet-trace-ps"></a>dotnet-rastrear PS

Lista os processos dotnet que podem ser anexados ao.

### <a name="synopsis"></a>Sinopse

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>dotnet-lista de rastreamento-perfis

Lista os perfis de rastreamento pré-criados com uma descrição de quais provedores e filtros estão em cada perfil.

### <a name="synopsis"></a>Sinopse

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Coletar um rastreamento com dotnet-Trace

Para coletar rastreamentos usando `dotnet-trace`:

- Obtenha o identificador do processo (PID) do aplicativo .NET Core do qual coletar rastreamentos.

  - No Windows, você pode usar o Gerenciador de tarefas ou o comando `tasklist`, por exemplo.
  - No Linux, por exemplo, o comando `ps`.
  - [dotnet-rastrear PS](#dotnet-trace-ps)

- Execute o seguinte comando:

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  O comando anterior gera uma saída semelhante à seguinte:

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- Pare a coleta pressionando a tecla `<Enter>`. `dotnet-trace` terminará de registrar eventos no arquivo *trace. NetTrace* .

## <a name="view-the-trace-captured-from-dotnet-trace"></a>Exibir o rastreamento capturado de dotnet-Trace

No Windows, os arquivos *. NetTrace* podem ser exibidos em [Perfview](https://github.com/microsoft/perfview) para análise: para rastreamentos coletados em outras plataformas, o arquivo de rastreamento pode ser movido para um computador Windows para ser exibido em Perfview.

No Linux, o rastreamento pode ser exibido alterando o formato de saída de `dotnet-trace` para `speedscope`. O formato do arquivo de saída pode ser alterado usando a opção `-f|--format`-`-f speedscope` fará `dotnet-trace` produzir um arquivo `speedscope`. Você pode escolher entre `nettrace` (a opção padrão) e `speedscope`. `Speedscope` arquivos podem ser abertos em <https://www.speedscope.app>.

> [!NOTE]
> O tempo de execução do .NET Core gera rastreamentos no formato `nettrace`. Os rastreamentos são convertidos em speedscope (se especificado) após a conclusão do rastreamento. Como algumas conversões podem resultar em perda de dados, o arquivo original de `nettrace` é preservado ao lado do arquivo convertido.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Usar o rastreamento dotnet para coletar valores de contador ao longo do tempo

`dotnet-trace` pode:

* Use `EventCounter` para o monitoramento de integridade básico em ambientes sensíveis ao desempenho. Por exemplo, em produção.
* Colete rastreamentos para que eles não precisem ser exibidos em tempo real.

Por exemplo, para coletar valores de contador de desempenho de tempo de execução, use o seguinte comando:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

O comando anterior informa os contadores de tempo de execução para relatar uma vez a cada segundo para monitoramento de integridade leve. Substituir `EventCounterIntervalSec=1` por um valor mais alto (por exemplo, 60) permite a coleta de um rastreamento menor com menos granularidade nos dados do contador.

O comando a seguir reduz a sobrecarga e o tamanho do rastreamento mais do que o anterior:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

O comando anterior desabilita os eventos de tempo de execução e o profiler de pilha gerenciado.

## <a name="net-providers"></a>Provedores .NET

O tempo de execução do .NET Core dá suporte aos provedores .NET a seguir. O .NET Core usa as mesmas palavras-chave para habilitar rastreamentos `Event Tracing for Windows (ETW)` e `EventPipe`.

| Nome do provedor                            | Informações |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [O provedor de tempo de execução](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Palavras-chave de tempo de execução CLR](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [O provedor de encerramento](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Palavras-chave de resumo do CLR](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Habilita o criador de perfil de exemplo. |
