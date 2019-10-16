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
# <a name="trace-for-performance-analysis-utility-dotnet-trace"></a><span data-ttu-id="e67fa-103">Rastreamento para o utilitário de análise de desempenho (`dotnet-trace`)</span><span class="sxs-lookup"><span data-stu-id="e67fa-103">Trace for performance analysis utility (`dotnet-trace`)</span></span>

<span data-ttu-id="e67fa-104">**Este artigo aplica-se a:** SDK do .net Core 3,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="e67fa-104">**This article applies to:** .NET Core 3.0 SDK and later versions</span></span>

## <a name="installing-dotnet-trace"></a><span data-ttu-id="e67fa-105">Instalando o `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="e67fa-105">Installing `dotnet-trace`</span></span>

<span data-ttu-id="e67fa-106">Para instalar a versão de lançamento mais recente do [pacote NuGet](https://www.nuget.org/packages/dotnet-trace)`dotnet-trace`, use o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="e67fa-106">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="e67fa-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e67fa-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="e67fa-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="e67fa-108">Description</span></span>

<span data-ttu-id="e67fa-109">A ferramenta `dotnet-trace` é uma ferramenta global de CLI de plataforma cruzada que permite a coleta de rastreamentos do .NET Core de um processo em execução sem qualquer criador de perfil nativo envolvido.</span><span class="sxs-lookup"><span data-stu-id="e67fa-109">The `dotnet-trace` tool is a cross-platform CLI global tool that enables the collection of .NET Core traces of a running process without any native profiler involved.</span></span> <span data-ttu-id="e67fa-110">Ele foi criado em relação à tecnologia `EventPipe` de plataforma cruzada do tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e67fa-110">It's built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span> <span data-ttu-id="e67fa-111">o `dotnet-trace` oferece a mesma experiência no Windows, Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="e67fa-111">`dotnet-trace` delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="e67fa-112">Opções</span><span class="sxs-lookup"><span data-stu-id="e67fa-112">Options</span></span>

- **`--version`**

<span data-ttu-id="e67fa-113">Exiba a versão do utilitário dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="e67fa-113">Display the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

<span data-ttu-id="e67fa-114">Mostrar ajuda de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e67fa-114">Show command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="e67fa-115">Comandos</span><span class="sxs-lookup"><span data-stu-id="e67fa-115">Commands</span></span>

| <span data-ttu-id="e67fa-116">Comando</span><span class="sxs-lookup"><span data-stu-id="e67fa-116">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="e67fa-117">dotnet-coleta de rastreamento</span><span class="sxs-lookup"><span data-stu-id="e67fa-117">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="e67fa-118">dotnet-conversão de rastreamento</span><span class="sxs-lookup"><span data-stu-id="e67fa-118">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="e67fa-119">dotnet-lista de rastreamento-processos</span><span class="sxs-lookup"><span data-stu-id="e67fa-119">dotnet-trace list-processes</span></span>](#dotnet-trace-list-processes) |
| [<span data-ttu-id="e67fa-120">dotnet-lista de rastreamento-perfis</span><span class="sxs-lookup"><span data-stu-id="e67fa-120">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="e67fa-121">dotnet-coleta de rastreamento</span><span class="sxs-lookup"><span data-stu-id="e67fa-121">dotnet-trace collect</span></span>

<span data-ttu-id="e67fa-122">Coleta um rastreamento de diagnóstico de um processo em execução.</span><span class="sxs-lookup"><span data-stu-id="e67fa-122">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e67fa-123">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e67fa-123">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="e67fa-124">Opções</span><span class="sxs-lookup"><span data-stu-id="e67fa-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="e67fa-125">O processo do qual coletar o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e67fa-125">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="e67fa-126">Define o tamanho do buffer circular na memória em megabytes.</span><span class="sxs-lookup"><span data-stu-id="e67fa-126">Sets the size of the in-memory circular buffer in megabytes.</span></span> <span data-ttu-id="e67fa-127">256 MB padrão.</span><span class="sxs-lookup"><span data-stu-id="e67fa-127">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="e67fa-128">O caminho de saída para os dados de rastreamento coletados.</span><span class="sxs-lookup"><span data-stu-id="e67fa-128">The output path for the collected trace data.</span></span> <span data-ttu-id="e67fa-129">Se não for especificado, o padrão será `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="e67fa-129">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="e67fa-130">Uma lista separada por vírgulas de provedores de `EventPipe` a serem habilitados.</span><span class="sxs-lookup"><span data-stu-id="e67fa-130">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="e67fa-131">Esses provedores complementam todos os provedores implícitos por `--profile <profile-name>`.</span><span class="sxs-lookup"><span data-stu-id="e67fa-131">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="e67fa-132">Se houver alguma inconsistência para um provedor específico, a configuração aqui terá precedência sobre a configuração implícita do perfil.</span><span class="sxs-lookup"><span data-stu-id="e67fa-132">If there's any inconsistency for a particular provider, the configuration here takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="e67fa-133">Esta lista de provedores está no formato:</span><span class="sxs-lookup"><span data-stu-id="e67fa-133">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="e67fa-134">`Provider` está no formato: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="e67fa-134">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="e67fa-135">`KeyValueArgs` está no formato: `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="e67fa-135">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="e67fa-136">Um conjunto nomeado predefinido de configurações de provedor que permite que cenários de rastreamento comuns sejam especificados de forma sucinta.</span><span class="sxs-lookup"><span data-stu-id="e67fa-136">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="e67fa-137">Define o formato de saída para a conversão do arquivo de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e67fa-137">Sets the output format for the trace file conversion.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="e67fa-138">dotnet-conversão de rastreamento</span><span class="sxs-lookup"><span data-stu-id="e67fa-138">dotnet-trace convert</span></span>

<span data-ttu-id="e67fa-139">Converte os rastreamentos `nettrace` em formatos alternativos para uso com ferramentas de análise de rastreamento alternativas.</span><span class="sxs-lookup"><span data-stu-id="e67fa-139">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e67fa-140">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e67fa-140">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="e67fa-141">Arguments</span><span class="sxs-lookup"><span data-stu-id="e67fa-141">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="e67fa-142">Arquivo de rastreamento de entrada a ser convertido.</span><span class="sxs-lookup"><span data-stu-id="e67fa-142">Input trace file to be converted.</span></span> <span data-ttu-id="e67fa-143">O padrão é *trace. NetTrace*.</span><span class="sxs-lookup"><span data-stu-id="e67fa-143">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="e67fa-144">Opções</span><span class="sxs-lookup"><span data-stu-id="e67fa-144">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="e67fa-145">Define o formato de saída para a conversão do arquivo de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e67fa-145">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="e67fa-146">Nome de arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="e67fa-146">Output filename.</span></span> <span data-ttu-id="e67fa-147">A extensão do formato de destino será adicionada.</span><span class="sxs-lookup"><span data-stu-id="e67fa-147">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-list-processes"></a><span data-ttu-id="e67fa-148">dotnet-lista de rastreamento-processos</span><span class="sxs-lookup"><span data-stu-id="e67fa-148">dotnet-trace list-processes</span></span>

<span data-ttu-id="e67fa-149">Lista os processos dotnet que podem ser rastreados.</span><span class="sxs-lookup"><span data-stu-id="e67fa-149">Lists dotnet processes that can be traced.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e67fa-150">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e67fa-150">Synopsis</span></span>

```console
dotnet-trace list-processes [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="e67fa-151">dotnet-lista de rastreamento-perfis</span><span class="sxs-lookup"><span data-stu-id="e67fa-151">dotnet-trace list-profiles</span></span>

<span data-ttu-id="e67fa-152">Lista os perfis de rastreamento pré-criados com uma descrição de quais provedores e filtros estão em cada perfil.</span><span class="sxs-lookup"><span data-stu-id="e67fa-152">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e67fa-153">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e67fa-153">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="e67fa-154">Coletar um rastreamento com `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="e67fa-154">Collect a trace with `dotnet-trace`</span></span>

- <span data-ttu-id="e67fa-155">Para coletar rastreamentos usando `dotnet-trace`, você precisará primeiro descobrir o identificador do processo (PID) do aplicativo .NET Core do qual os rastreamentos serão coletados.</span><span class="sxs-lookup"><span data-stu-id="e67fa-155">To collect traces using `dotnet-trace`, you'll need to first, find out the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="e67fa-156">No Windows, há opções como usar o Gerenciador de tarefas ou o comando `tasklist`.</span><span class="sxs-lookup"><span data-stu-id="e67fa-156">On Windows, there are options such as using the task manager or the `tasklist` command.</span></span>
  - <span data-ttu-id="e67fa-157">No Linux, a opção trivial poderia usar o comando `ps`.</span><span class="sxs-lookup"><span data-stu-id="e67fa-157">On Linux, the trivial option could be using `ps` command.</span></span>

<span data-ttu-id="e67fa-158">Você também pode usar o comando [dotnet-Trace List-Processes](#dotnet-trace-list-processes) para descobrir quais processos do .NET Core estão em execução, juntamente com seus PIDs.</span><span class="sxs-lookup"><span data-stu-id="e67fa-158">You may also use the [dotnet-trace list-processes](#dotnet-trace-list-processes) command to find out what .NET Core processes are running, along with their PIDs.</span></span>

- <span data-ttu-id="e67fa-159">Em seguida, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e67fa-159">Then, run the following command:</span></span>

```console
> dotnet-trace collect --process-id <PID>

Press <Enter> to exit...
Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
```

- <span data-ttu-id="e67fa-160">Por fim, interrompa a coleta pressionando a chave `<Enter>` e `dotnet-trace` terminará os eventos de log no arquivo `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="e67fa-160">Finally, stop collection by pressing the `<Enter>` key, and `dotnet-trace` will finish logging events to `trace.nettrace` file.</span></span>

## <a name="viewing-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="e67fa-161">Exibindo o rastreamento capturado do `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="e67fa-161">Viewing the trace captured from `dotnet-trace`</span></span>

<span data-ttu-id="e67fa-162">No Windows, os arquivos `.nettrace` podem ser exibidos em [Perfview](https://github.com/microsoft/perfview) para análise, assim como os rastreamentos coletados com o ETW ou o LTTng.</span><span class="sxs-lookup"><span data-stu-id="e67fa-162">On Windows, `.nettrace` files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis, just like traces collected with ETW or LTTng.</span></span> <span data-ttu-id="e67fa-163">Para rastreamentos coletados no Linux, você pode mover o rastreamento para um computador Windows a ser exibido em PerfView.</span><span class="sxs-lookup"><span data-stu-id="e67fa-163">For traces collected on Linux, you can move the trace to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="e67fa-164">Você também pode exibir o rastreamento em um computador Linux alterando o formato de saída de `dotnet-trace` para `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="e67fa-164">You may also view the trace on a Linux machine by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="e67fa-165">Você pode alterar o formato do arquivo de saída usando a opção `-f|--format`-`-f speedscope` fará com que `dotnet-trace` gere um arquivo `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="e67fa-165">You can change the output file format using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` to produce a `speedscope` file.</span></span> <span data-ttu-id="e67fa-166">No momento, você pode escolher entre `nettrace` (a opção padrão) e `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="e67fa-166">You can currently choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="e67fa-167">os arquivos `Speedscope` podem ser abertos em <https://www.speedscope.app>.</span><span class="sxs-lookup"><span data-stu-id="e67fa-167">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="e67fa-168">O tempo de execução do .NET Core gera rastreamentos no formato `nettrace` e eles são convertidos em speedscope (se especificado) após a conclusão do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e67fa-168">The .NET Core runtime generates traces in the `nettrace` format, and they're converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="e67fa-169">Como algumas conversões podem resultar em perda de dados, o arquivo original `nettrace` é preservado ao lado do arquivo convertido.</span><span class="sxs-lookup"><span data-stu-id="e67fa-169">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="using-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="e67fa-170">Usando `dotnet-trace` para coletar valores de contador ao longo do tempo</span><span class="sxs-lookup"><span data-stu-id="e67fa-170">Using `dotnet-trace` to collect counter values over time</span></span>

<span data-ttu-id="e67fa-171">Se você estiver tentando usar `EventCounter` para o monitoramento de integridade básico em configurações sensíveis ao desempenho, como ambientes de produção e desejar coletar rastreamentos em vez de assisti-los em tempo real, você pode fazer isso com o `dotnet-trace` também.</span><span class="sxs-lookup"><span data-stu-id="e67fa-171">If you're trying to use `EventCounter` for basic health monitoring in  performance-sensitive settings like production environments and you want to collect traces instead of watching them in real time, you can do that with `dotnet-trace` as well.</span></span>

<span data-ttu-id="e67fa-172">Por exemplo, se você quiser coletar valores de contador de desempenho de tempo de execução, poderá usar o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e67fa-172">For example, if you want to collect runtime performance counter values, you can use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="e67fa-173">Esse comando informa os contadores de tempo de execução a serem relatados uma vez a cada segundo para o monitoramento de integridade leve.</span><span class="sxs-lookup"><span data-stu-id="e67fa-173">This command tells the runtime counters to be reported once every second for lightweight health monitoring.</span></span> <span data-ttu-id="e67fa-174">Substituir `EventCounterIntervalSec=1` por um valor mais alto (por exemplo, 60) permite que você colete um rastreamento menor com menos granularidade nos dados do contador.</span><span class="sxs-lookup"><span data-stu-id="e67fa-174">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows you to collect a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="e67fa-175">Se você quiser desabilitar eventos de tempo de execução para reduzir a sobrecarga (e o tamanho do rastreamento) ainda mais, use o comando a seguir para desabilitar os eventos de tempo de execução e o gerador de perfil de pilha gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e67fa-175">If you want to disable runtime events to reduce the overhead (and trace size) even further, you can use the following command to disable runtime events and managed stack profiler.</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

## <a name="net-providers"></a><span data-ttu-id="e67fa-176">Provedores .NET</span><span class="sxs-lookup"><span data-stu-id="e67fa-176">.NET Providers</span></span>

<span data-ttu-id="e67fa-177">O tempo de execução do .NET Core dá suporte aos provedores .NET a seguir.</span><span class="sxs-lookup"><span data-stu-id="e67fa-177">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="e67fa-178">O .NET Core usa as mesmas palavras-chave para habilitar rastreamentos `Event Tracing for Windows (ETW)` e `EventPipe`.</span><span class="sxs-lookup"><span data-stu-id="e67fa-178">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="e67fa-179">Nome do provedor</span><span class="sxs-lookup"><span data-stu-id="e67fa-179">Provider name</span></span>                            | <span data-ttu-id="e67fa-180">Informações</span><span class="sxs-lookup"><span data-stu-id="e67fa-180">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="e67fa-181">O provedor de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e67fa-181">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="e67fa-182">Palavras-chave de tempo de execução CLR</span><span class="sxs-lookup"><span data-stu-id="e67fa-182">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="e67fa-183">O provedor de encerramento</span><span class="sxs-lookup"><span data-stu-id="e67fa-183">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="e67fa-184">Palavras-chave de resumo do CLR</span><span class="sxs-lookup"><span data-stu-id="e67fa-184">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="e67fa-185">Habilita o criador de perfil de exemplo.</span><span class="sxs-lookup"><span data-stu-id="e67fa-185">Enables the sample profiler.</span></span> |
