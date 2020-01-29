---
title: dotnet-ferramenta de rastreamento-.NET Core
description: Instalando e usando a ferramenta de linha de comando dotnet-Trace.
ms.date: 11/21/2019
ms.openlocfilehash: b19b159636fbf57fa2d461b398fcf9234aab491c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737654"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="30623-103">dotnet-utilitário de análise de desempenho de rastreamento</span><span class="sxs-lookup"><span data-stu-id="30623-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="30623-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 3,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="30623-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="30623-105">Instalar dotnet-Trace</span><span class="sxs-lookup"><span data-stu-id="30623-105">Install dotnet-trace</span></span>

<span data-ttu-id="30623-106">Instale `dotnet-trace` [pacote NuGet](https://www.nuget.org/packages/dotnet-trace) com o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="30623-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="30623-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="30623-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="30623-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="30623-108">Description</span></span>

<span data-ttu-id="30623-109">A ferramenta de `dotnet-trace`:</span><span class="sxs-lookup"><span data-stu-id="30623-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="30623-110">É uma ferramenta .NET Core de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="30623-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="30623-111">Habilita a coleção de rastreamentos do .NET Core de um processo em execução sem um criador de perfil nativo.</span><span class="sxs-lookup"><span data-stu-id="30623-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="30623-112">O é criado em relação à tecnologia de `EventPipe` entre plataformas do tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30623-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="30623-113">Oferece a mesma experiência no Windows, Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="30623-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="30623-114">Opções</span><span class="sxs-lookup"><span data-stu-id="30623-114">Options</span></span>

- **`--version`**

  <span data-ttu-id="30623-115">Exibe a versão do utilitário dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="30623-115">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="30623-116">Mostra a ajuda da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="30623-116">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="30623-117">Comandos</span><span class="sxs-lookup"><span data-stu-id="30623-117">Commands</span></span>

| <span data-ttu-id="30623-118">{1&gt;Comando&lt;1}</span><span class="sxs-lookup"><span data-stu-id="30623-118">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="30623-119">dotnet-coleta de rastreamento</span><span class="sxs-lookup"><span data-stu-id="30623-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="30623-120">dotnet-conversão de rastreamento</span><span class="sxs-lookup"><span data-stu-id="30623-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="30623-121">dotnet-rastrear PS</span><span class="sxs-lookup"><span data-stu-id="30623-121">dotnet-trace ps</span></span>](#dotnet-trace-ps) |
| [<span data-ttu-id="30623-122">dotnet-lista de rastreamento-perfis</span><span class="sxs-lookup"><span data-stu-id="30623-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="30623-123">dotnet-coleta de rastreamento</span><span class="sxs-lookup"><span data-stu-id="30623-123">dotnet-trace collect</span></span>

<span data-ttu-id="30623-124">Coleta um rastreamento de diagnóstico de um processo em execução.</span><span class="sxs-lookup"><span data-stu-id="30623-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="30623-125">Sinopse</span><span class="sxs-lookup"><span data-stu-id="30623-125">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="30623-126">Opções</span><span class="sxs-lookup"><span data-stu-id="30623-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="30623-127">O processo do qual coletar o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="30623-127">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="30623-128">Define o tamanho do buffer circular na memória, em megabytes.</span><span class="sxs-lookup"><span data-stu-id="30623-128">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="30623-129">256 MB padrão.</span><span class="sxs-lookup"><span data-stu-id="30623-129">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="30623-130">O caminho de saída para os dados de rastreamento coletados.</span><span class="sxs-lookup"><span data-stu-id="30623-130">The output path for the collected trace data.</span></span> <span data-ttu-id="30623-131">Se não for especificado, o padrão será `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="30623-131">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="30623-132">Uma lista separada por vírgulas de provedores de `EventPipe` a serem habilitados.</span><span class="sxs-lookup"><span data-stu-id="30623-132">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="30623-133">Esses provedores complementam todos os provedores implícitos por `--profile <profile-name>`.</span><span class="sxs-lookup"><span data-stu-id="30623-133">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="30623-134">Se houver alguma inconsistência para um provedor específico, essa configuração terá precedência sobre a configuração implícita do perfil.</span><span class="sxs-lookup"><span data-stu-id="30623-134">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="30623-135">Esta lista de provedores está no formato:</span><span class="sxs-lookup"><span data-stu-id="30623-135">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="30623-136">`Provider` está no formato: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="30623-136">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="30623-137">`KeyValueArgs` está no formato: `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="30623-137">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="30623-138">Um conjunto nomeado predefinido de configurações de provedor que permite que cenários de rastreamento comuns sejam especificados de forma sucinta.</span><span class="sxs-lookup"><span data-stu-id="30623-138">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format {NetTrace|Speedscope}`**

  <span data-ttu-id="30623-139">Define o formato de saída para a conversão do arquivo de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="30623-139">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="30623-140">O padrão é `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="30623-140">The default is `NetTrace`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="30623-141">dotnet-conversão de rastreamento</span><span class="sxs-lookup"><span data-stu-id="30623-141">dotnet-trace convert</span></span>

<span data-ttu-id="30623-142">Converte `nettrace` rastreamentos em formatos alternativos para uso com ferramentas de análise de rastreamento alternativas.</span><span class="sxs-lookup"><span data-stu-id="30623-142">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="30623-143">Sinopse</span><span class="sxs-lookup"><span data-stu-id="30623-143">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="30623-144">Arguments</span><span class="sxs-lookup"><span data-stu-id="30623-144">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="30623-145">Arquivo de rastreamento de entrada a ser convertido.</span><span class="sxs-lookup"><span data-stu-id="30623-145">Input trace file to be converted.</span></span> <span data-ttu-id="30623-146">O padrão é *trace. NetTrace*.</span><span class="sxs-lookup"><span data-stu-id="30623-146">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="30623-147">Opções</span><span class="sxs-lookup"><span data-stu-id="30623-147">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="30623-148">Define o formato de saída para a conversão do arquivo de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="30623-148">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="30623-149">Nome de arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="30623-149">Output filename.</span></span> <span data-ttu-id="30623-150">A extensão do formato de destino será adicionada.</span><span class="sxs-lookup"><span data-stu-id="30623-150">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="30623-151">dotnet-rastrear PS</span><span class="sxs-lookup"><span data-stu-id="30623-151">dotnet-trace ps</span></span>

<span data-ttu-id="30623-152">Lista os processos dotnet que podem ser anexados ao.</span><span class="sxs-lookup"><span data-stu-id="30623-152">Lists dotnet processes that can be attached to.</span></span>

### <a name="synopsis"></a><span data-ttu-id="30623-153">Sinopse</span><span class="sxs-lookup"><span data-stu-id="30623-153">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="30623-154">dotnet-lista de rastreamento-perfis</span><span class="sxs-lookup"><span data-stu-id="30623-154">dotnet-trace list-profiles</span></span>

<span data-ttu-id="30623-155">Lista os perfis de rastreamento pré-criados com uma descrição de quais provedores e filtros estão em cada perfil.</span><span class="sxs-lookup"><span data-stu-id="30623-155">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="30623-156">Sinopse</span><span class="sxs-lookup"><span data-stu-id="30623-156">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="30623-157">Coletar um rastreamento com dotnet-Trace</span><span class="sxs-lookup"><span data-stu-id="30623-157">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="30623-158">Para coletar rastreamentos usando `dotnet-trace`:</span><span class="sxs-lookup"><span data-stu-id="30623-158">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="30623-159">Obtenha o identificador do processo (PID) do aplicativo .NET Core do qual coletar rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="30623-159">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="30623-160">No Windows, você pode usar o Gerenciador de tarefas ou o comando `tasklist`, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="30623-160">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="30623-161">No Linux, por exemplo, o comando `ps`.</span><span class="sxs-lookup"><span data-stu-id="30623-161">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="30623-162">dotnet-rastrear PS</span><span class="sxs-lookup"><span data-stu-id="30623-162">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="30623-163">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="30623-163">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="30623-164">O comando anterior gera uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="30623-164">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="30623-165">Pare a coleta pressionando a tecla `<Enter>`.</span><span class="sxs-lookup"><span data-stu-id="30623-165">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="30623-166">`dotnet-trace` terminará de registrar eventos no arquivo *trace. NetTrace* .</span><span class="sxs-lookup"><span data-stu-id="30623-166">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="30623-167">Exibir o rastreamento capturado de dotnet-Trace</span><span class="sxs-lookup"><span data-stu-id="30623-167">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="30623-168">No Windows, os arquivos *. NetTrace* podem ser exibidos em [Perfview](https://github.com/microsoft/perfview) para análise: para rastreamentos coletados em outras plataformas, o arquivo de rastreamento pode ser movido para um computador Windows para ser exibido em Perfview.</span><span class="sxs-lookup"><span data-stu-id="30623-168">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="30623-169">No Linux, o rastreamento pode ser exibido alterando o formato de saída de `dotnet-trace` para `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="30623-169">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="30623-170">O formato do arquivo de saída pode ser alterado usando a opção `-f|--format`-`-f speedscope` fará `dotnet-trace` produzir um arquivo `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="30623-170">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="30623-171">Você pode escolher entre `nettrace` (a opção padrão) e `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="30623-171">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="30623-172">`Speedscope` arquivos podem ser abertos em <https://www.speedscope.app>.</span><span class="sxs-lookup"><span data-stu-id="30623-172">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="30623-173">O tempo de execução do .NET Core gera rastreamentos no formato `nettrace`.</span><span class="sxs-lookup"><span data-stu-id="30623-173">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="30623-174">Os rastreamentos são convertidos em speedscope (se especificado) após a conclusão do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="30623-174">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="30623-175">Como algumas conversões podem resultar em perda de dados, o arquivo original de `nettrace` é preservado ao lado do arquivo convertido.</span><span class="sxs-lookup"><span data-stu-id="30623-175">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="30623-176">Usar o rastreamento dotnet para coletar valores de contador ao longo do tempo</span><span class="sxs-lookup"><span data-stu-id="30623-176">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="30623-177">`dotnet-trace` pode:</span><span class="sxs-lookup"><span data-stu-id="30623-177">`dotnet-trace` can:</span></span>

* <span data-ttu-id="30623-178">Use `EventCounter` para o monitoramento de integridade básico em ambientes sensíveis ao desempenho.</span><span class="sxs-lookup"><span data-stu-id="30623-178">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="30623-179">Por exemplo, em produção.</span><span class="sxs-lookup"><span data-stu-id="30623-179">For example, in production.</span></span>
* <span data-ttu-id="30623-180">Colete rastreamentos para que eles não precisem ser exibidos em tempo real.</span><span class="sxs-lookup"><span data-stu-id="30623-180">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="30623-181">Por exemplo, para coletar valores de contador de desempenho de tempo de execução, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="30623-181">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="30623-182">O comando anterior informa os contadores de tempo de execução para relatar uma vez a cada segundo para monitoramento de integridade leve.</span><span class="sxs-lookup"><span data-stu-id="30623-182">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="30623-183">Substituir `EventCounterIntervalSec=1` por um valor mais alto (por exemplo, 60) permite a coleta de um rastreamento menor com menos granularidade nos dados do contador.</span><span class="sxs-lookup"><span data-stu-id="30623-183">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="30623-184">O comando a seguir reduz a sobrecarga e o tamanho do rastreamento mais do que o anterior:</span><span class="sxs-lookup"><span data-stu-id="30623-184">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="30623-185">O comando anterior desabilita os eventos de tempo de execução e o profiler de pilha gerenciado.</span><span class="sxs-lookup"><span data-stu-id="30623-185">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="30623-186">Provedores .NET</span><span class="sxs-lookup"><span data-stu-id="30623-186">.NET Providers</span></span>

<span data-ttu-id="30623-187">O tempo de execução do .NET Core dá suporte aos provedores .NET a seguir.</span><span class="sxs-lookup"><span data-stu-id="30623-187">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="30623-188">O .NET Core usa as mesmas palavras-chave para habilitar rastreamentos `Event Tracing for Windows (ETW)` e `EventPipe`.</span><span class="sxs-lookup"><span data-stu-id="30623-188">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="30623-189">Nome do provedor</span><span class="sxs-lookup"><span data-stu-id="30623-189">Provider name</span></span>                            | <span data-ttu-id="30623-190">Informações do</span><span class="sxs-lookup"><span data-stu-id="30623-190">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="30623-191">O provedor de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="30623-191">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="30623-192">Palavras-chave de tempo de execução CLR</span><span class="sxs-lookup"><span data-stu-id="30623-192">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="30623-193">O provedor de encerramento</span><span class="sxs-lookup"><span data-stu-id="30623-193">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="30623-194">Palavras-chave de resumo do CLR</span><span class="sxs-lookup"><span data-stu-id="30623-194">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="30623-195">Habilita o criador de perfil de exemplo.</span><span class="sxs-lookup"><span data-stu-id="30623-195">Enables the sample profiler.</span></span> |
