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
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="19fee-103">utilitário de análise de desempenho dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="19fee-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="19fee-104">**Este artigo se aplica a:** ✔️ .NET Core 3.0 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="19fee-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="19fee-105">Instale o dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="19fee-105">Install dotnet-trace</span></span>

<span data-ttu-id="19fee-106">Instale `dotnet-trace` [o pacote NuGet](https://www.nuget.org/packages/dotnet-trace) com o comando de instalação da ferramenta [dotnet:](../tools/dotnet-tool-install.md)</span><span class="sxs-lookup"><span data-stu-id="19fee-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="19fee-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="19fee-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="19fee-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="19fee-108">Description</span></span>

<span data-ttu-id="19fee-109">A `dotnet-trace` ferramenta:</span><span class="sxs-lookup"><span data-stu-id="19fee-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="19fee-110">É uma ferramenta multiplataforma .NET Core.</span><span class="sxs-lookup"><span data-stu-id="19fee-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="19fee-111">Habilita a coleta de traços .NET Core de um processo em execução sem um profiler nativo.</span><span class="sxs-lookup"><span data-stu-id="19fee-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="19fee-112">É construído em torno `EventPipe` da tecnologia multiplataforma do tempo de execução .NET Core.</span><span class="sxs-lookup"><span data-stu-id="19fee-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="19fee-113">Oferece a mesma experiência no Windows, Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="19fee-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="19fee-114">Opções</span><span class="sxs-lookup"><span data-stu-id="19fee-114">Options</span></span>

- **`--version`**

  <span data-ttu-id="19fee-115">Exibe a versão do utilitário dotnet-counters.</span><span class="sxs-lookup"><span data-stu-id="19fee-115">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="19fee-116">Mostra ajuda na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="19fee-116">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="19fee-117">Comandos</span><span class="sxs-lookup"><span data-stu-id="19fee-117">Commands</span></span>

| <span data-ttu-id="19fee-118">Comando</span><span class="sxs-lookup"><span data-stu-id="19fee-118">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="19fee-119">dotnet-trace coletar</span><span class="sxs-lookup"><span data-stu-id="19fee-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="19fee-120">dotnet-trace converter</span><span class="sxs-lookup"><span data-stu-id="19fee-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="19fee-121">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="19fee-121">dotnet-trace ps</span></span>](#dotnet-trace-ps) |
| [<span data-ttu-id="19fee-122">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="19fee-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="19fee-123">dotnet-trace coletar</span><span class="sxs-lookup"><span data-stu-id="19fee-123">dotnet-trace collect</span></span>

<span data-ttu-id="19fee-124">Coleta um traço de diagnóstico de um processo em execução.</span><span class="sxs-lookup"><span data-stu-id="19fee-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="19fee-125">Sinopse</span><span class="sxs-lookup"><span data-stu-id="19fee-125">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="19fee-126">Opções</span><span class="sxs-lookup"><span data-stu-id="19fee-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="19fee-127">O processo para coletar o rastro de.</span><span class="sxs-lookup"><span data-stu-id="19fee-127">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="19fee-128">Define o tamanho do buffer circular na memória, em megabytes.</span><span class="sxs-lookup"><span data-stu-id="19fee-128">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="19fee-129">Padrão 256 MB.</span><span class="sxs-lookup"><span data-stu-id="19fee-129">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="19fee-130">O caminho de saída para os dados de rastreamento coletados.</span><span class="sxs-lookup"><span data-stu-id="19fee-130">The output path for the collected trace data.</span></span> <span data-ttu-id="19fee-131">Se não especificado, `trace.nettrace`ele é padrão para .</span><span class="sxs-lookup"><span data-stu-id="19fee-131">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="19fee-132">Uma lista separada por comma de `EventPipe` provedores a serem habilitados.</span><span class="sxs-lookup"><span data-stu-id="19fee-132">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="19fee-133">Esses provedores complementam `--profile <profile-name>`quaisquer provedores implícitos por .</span><span class="sxs-lookup"><span data-stu-id="19fee-133">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="19fee-134">Se houver alguma inconsistência para um determinado provedor, essa configuração tem precedência sobre a configuração implícita do perfil.</span><span class="sxs-lookup"><span data-stu-id="19fee-134">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="19fee-135">Esta lista de provedores está no formulário:</span><span class="sxs-lookup"><span data-stu-id="19fee-135">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="19fee-136">`Provider`está na forma: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="19fee-136">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="19fee-137">`KeyValueArgs`está na forma: `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="19fee-137">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="19fee-138">Um conjunto predefinido de configurações do provedor que permite que cenários comuns de rastreamento sejam especificados de forma sucinta.</span><span class="sxs-lookup"><span data-stu-id="19fee-138">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format {NetTrace|Speedscope}`**

  <span data-ttu-id="19fee-139">Define o formato de saída para a conversão do arquivo de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="19fee-139">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="19fee-140">O padrão é `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="19fee-140">The default is `NetTrace`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="19fee-141">dotnet-trace converter</span><span class="sxs-lookup"><span data-stu-id="19fee-141">dotnet-trace convert</span></span>

<span data-ttu-id="19fee-142">Converte `nettrace` traços em formatos alternativos para uso com ferramentas alternativas de análise de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="19fee-142">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="19fee-143">Sinopse</span><span class="sxs-lookup"><span data-stu-id="19fee-143">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="19fee-144">Argumentos</span><span class="sxs-lookup"><span data-stu-id="19fee-144">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="19fee-145">Arquivo de rastreamento de entrada a ser convertido.</span><span class="sxs-lookup"><span data-stu-id="19fee-145">Input trace file to be converted.</span></span> <span data-ttu-id="19fee-146">Padrão para *trace.nettrace*.</span><span class="sxs-lookup"><span data-stu-id="19fee-146">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="19fee-147">Opções</span><span class="sxs-lookup"><span data-stu-id="19fee-147">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="19fee-148">Define o formato de saída para a conversão do arquivo de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="19fee-148">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="19fee-149">Nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="19fee-149">Output filename.</span></span> <span data-ttu-id="19fee-150">A extensão do formato de destino será adicionada.</span><span class="sxs-lookup"><span data-stu-id="19fee-150">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="19fee-151">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="19fee-151">dotnet-trace ps</span></span>

<span data-ttu-id="19fee-152">Lista processos dotnet que podem ser anexados.</span><span class="sxs-lookup"><span data-stu-id="19fee-152">Lists dotnet processes that can be attached to.</span></span>

### <a name="synopsis"></a><span data-ttu-id="19fee-153">Sinopse</span><span class="sxs-lookup"><span data-stu-id="19fee-153">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="19fee-154">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="19fee-154">dotnet-trace list-profiles</span></span>

<span data-ttu-id="19fee-155">Lista perfis de rastreamento pré-construídos com uma descrição de quais provedores e filtros estão em cada perfil.</span><span class="sxs-lookup"><span data-stu-id="19fee-155">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="19fee-156">Sinopse</span><span class="sxs-lookup"><span data-stu-id="19fee-156">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="19fee-157">Coletar um traço com dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="19fee-157">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="19fee-158">Para coletar vestígios usando: `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="19fee-158">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="19fee-159">Obtenha o identificador de processo (PID) do aplicativo .NET Core para coletar vestígios.</span><span class="sxs-lookup"><span data-stu-id="19fee-159">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="19fee-160">No Windows, você pode usar `tasklist` o Gerenciador de Tarefas ou o comando, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="19fee-160">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="19fee-161">No Linux, por `ps` exemplo, o comando.</span><span class="sxs-lookup"><span data-stu-id="19fee-161">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="19fee-162">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="19fee-162">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="19fee-163">Execute o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="19fee-163">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="19fee-164">O comando anterior gera saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="19fee-164">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="19fee-165">Pare a coleta `<Enter>` pressionando a tecla.</span><span class="sxs-lookup"><span data-stu-id="19fee-165">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="19fee-166">`dotnet-trace`terminará o registro de eventos no arquivo *trace.nettrace.*</span><span class="sxs-lookup"><span data-stu-id="19fee-166">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="19fee-167">Veja o vestígio capturado a partir do dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="19fee-167">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="19fee-168">No Windows, arquivos *.nettrace* podem ser visualizados no [PerfView](https://github.com/microsoft/perfview) para análise: Para rastreamentos coletados em outras plataformas, o arquivo de rastreamento pode ser movido para uma máquina windows para ser visualizado no PerfView.</span><span class="sxs-lookup"><span data-stu-id="19fee-168">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="19fee-169">No Linux, o trace pode ser visualizado alterando o formato de saída de `dotnet-trace` . `speedscope`</span><span class="sxs-lookup"><span data-stu-id="19fee-169">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="19fee-170">O formato do arquivo de `-f|--format` saída `-f speedscope` pode `dotnet-trace` ser `speedscope` alterado usando a opção - fará produzir um arquivo.</span><span class="sxs-lookup"><span data-stu-id="19fee-170">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="19fee-171">Você pode `nettrace` escolher entre (a `speedscope`opção padrão) e .</span><span class="sxs-lookup"><span data-stu-id="19fee-171">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="19fee-172">`Speedscope`arquivos podem ser <https://www.speedscope.app>abertos em .</span><span class="sxs-lookup"><span data-stu-id="19fee-172">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="19fee-173">O tempo de execução do `nettrace` .NET Core gera traços no formato.</span><span class="sxs-lookup"><span data-stu-id="19fee-173">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="19fee-174">Os traços são convertidos em speedscope (se especificado) após a conclusão do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="19fee-174">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="19fee-175">Uma vez que algumas conversões podem `nettrace` resultar em perda de dados, o arquivo original é preservado ao lado do arquivo convertido.</span><span class="sxs-lookup"><span data-stu-id="19fee-175">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="19fee-176">Use dotnet-trace para coletar valores de contador ao longo do tempo</span><span class="sxs-lookup"><span data-stu-id="19fee-176">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="19fee-177">`dotnet-trace`Cna:</span><span class="sxs-lookup"><span data-stu-id="19fee-177">`dotnet-trace` can:</span></span>

* <span data-ttu-id="19fee-178">Uso `EventCounter` para monitoramento básico de saúde em ambientes sensíveis ao desempenho.</span><span class="sxs-lookup"><span data-stu-id="19fee-178">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="19fee-179">Por exemplo, na produção.</span><span class="sxs-lookup"><span data-stu-id="19fee-179">For example, in production.</span></span>
* <span data-ttu-id="19fee-180">Colete vestígios para que não precisem ser vistos em tempo real.</span><span class="sxs-lookup"><span data-stu-id="19fee-180">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="19fee-181">Por exemplo, para coletar valores do contador de desempenho em tempo de execução, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="19fee-181">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="19fee-182">O comando precede diz aos contadores de tempo de execução que informem uma vez a cada segundo para o monitoramento leve da saúde.</span><span class="sxs-lookup"><span data-stu-id="19fee-182">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="19fee-183">A `EventCounterIntervalSec=1` substituição por um valor mais alto (por exemplo, 60) permite a coleta de um traço menor com menos granularidade nos dados do contador.</span><span class="sxs-lookup"><span data-stu-id="19fee-183">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="19fee-184">O comando a seguir reduz o tamanho da sobrecarga e do rastreamento mais do que o anterior:</span><span class="sxs-lookup"><span data-stu-id="19fee-184">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="19fee-185">O comando anterior desativa eventos de tempo de execução e o profiler de pilha gerenciado.</span><span class="sxs-lookup"><span data-stu-id="19fee-185">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="19fee-186">.NET Provedores</span><span class="sxs-lookup"><span data-stu-id="19fee-186">.NET Providers</span></span>

<span data-ttu-id="19fee-187">O tempo de execução do .NET Core suporta os seguintes provedores .NET.</span><span class="sxs-lookup"><span data-stu-id="19fee-187">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="19fee-188">.NET Core usa as mesmas `Event Tracing for Windows (ETW)` `EventPipe` palavras-chave para habilitar ambos e traços.</span><span class="sxs-lookup"><span data-stu-id="19fee-188">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="19fee-189">Nome do provedor</span><span class="sxs-lookup"><span data-stu-id="19fee-189">Provider name</span></span>                            | <span data-ttu-id="19fee-190">Informações</span><span class="sxs-lookup"><span data-stu-id="19fee-190">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="19fee-191">O provedor de runtime</span><span class="sxs-lookup"><span data-stu-id="19fee-191">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="19fee-192">Palavras-chave clr runtime</span><span class="sxs-lookup"><span data-stu-id="19fee-192">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="19fee-193">O provedor de encerramento</span><span class="sxs-lookup"><span data-stu-id="19fee-193">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="19fee-194">Palavras-chave clr rundown</span><span class="sxs-lookup"><span data-stu-id="19fee-194">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="19fee-195">Habilita o profiler de amostra.</span><span class="sxs-lookup"><span data-stu-id="19fee-195">Enables the sample profiler.</span></span> |
