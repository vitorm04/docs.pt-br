---
title: dotnet-ferramenta de rastreamento-.NET Core
description: Instalando e usando a ferramenta de linha de comando dotnet-Trace.
ms.date: 11/21/2019
ms.openlocfilehash: 25178a0e59ce9edb69d15ee761c1b9e56aa5eb3a
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517302"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="db3e0-103">dotnet-utilitário de análise de desempenho de rastreamento</span><span class="sxs-lookup"><span data-stu-id="db3e0-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="db3e0-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 3,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="db3e0-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="db3e0-105">Instalar dotnet-Trace</span><span class="sxs-lookup"><span data-stu-id="db3e0-105">Install dotnet-trace</span></span>

<span data-ttu-id="db3e0-106">Instale `dotnet-trace` o [pacote NuGet](https://www.nuget.org/packages/dotnet-trace) com o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="db3e0-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="db3e0-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="db3e0-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="db3e0-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="db3e0-108">Description</span></span>

<span data-ttu-id="db3e0-109">A `dotnet-trace` ferramenta:</span><span class="sxs-lookup"><span data-stu-id="db3e0-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="db3e0-110">É uma ferramenta .NET Core de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="db3e0-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="db3e0-111">Habilita a coleção de rastreamentos do .NET Core de um processo em execução sem um criador de perfil nativo.</span><span class="sxs-lookup"><span data-stu-id="db3e0-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="db3e0-112">O é criado em relação à tecnologia de plataforma cruzada `EventPipe` do tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="db3e0-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="db3e0-113">Oferece a mesma experiência no Windows, Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="db3e0-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="db3e0-114">Opções</span><span class="sxs-lookup"><span data-stu-id="db3e0-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="db3e0-115">Mostra a ajuda da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="db3e0-115">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="db3e0-116">Exibe a versão do utilitário dotnet-Trace.</span><span class="sxs-lookup"><span data-stu-id="db3e0-116">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="db3e0-117">Comandos</span><span class="sxs-lookup"><span data-stu-id="db3e0-117">Commands</span></span>

| <span data-ttu-id="db3e0-118">Comando</span><span class="sxs-lookup"><span data-stu-id="db3e0-118">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="db3e0-119">dotnet-coleta de rastreamento</span><span class="sxs-lookup"><span data-stu-id="db3e0-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="db3e0-120">dotnet-conversão de rastreamento</span><span class="sxs-lookup"><span data-stu-id="db3e0-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="db3e0-121">dotnet-rastrear PS</span><span class="sxs-lookup"><span data-stu-id="db3e0-121">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="db3e0-122">dotnet-lista de rastreamento-perfis</span><span class="sxs-lookup"><span data-stu-id="db3e0-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="db3e0-123">dotnet-coleta de rastreamento</span><span class="sxs-lookup"><span data-stu-id="db3e0-123">dotnet-trace collect</span></span>

<span data-ttu-id="db3e0-124">Coleta um rastreamento de diagnóstico de um processo em execução.</span><span class="sxs-lookup"><span data-stu-id="db3e0-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="db3e0-125">Sinopse</span><span class="sxs-lookup"><span data-stu-id="db3e0-125">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>]  [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
```

### <a name="options"></a><span data-ttu-id="db3e0-126">Opções</span><span class="sxs-lookup"><span data-stu-id="db3e0-126">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="db3e0-127">Define o tamanho do buffer circular na memória, em megabytes.</span><span class="sxs-lookup"><span data-stu-id="db3e0-127">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="db3e0-128">256 MB padrão.</span><span class="sxs-lookup"><span data-stu-id="db3e0-128">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="db3e0-129">Detalhes dos eventos CLR a serem emitidos.</span><span class="sxs-lookup"><span data-stu-id="db3e0-129">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="db3e0-130">Lista de eventos de tempo de execução CLR a serem emitidos.</span><span class="sxs-lookup"><span data-stu-id="db3e0-130">List of CLR runtime events to emit.</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="db3e0-131">Define o formato de saída para a conversão do arquivo de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="db3e0-131">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="db3e0-132">O padrão é `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="db3e0-132">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="db3e0-133">O nome do processo do qual coletar o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="db3e0-133">The name of the process to collect the trace from.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="db3e0-134">O caminho de saída para os dados de rastreamento coletados.</span><span class="sxs-lookup"><span data-stu-id="db3e0-134">The output path for the collected trace data.</span></span> <span data-ttu-id="db3e0-135">Se não for especificado, o padrão será `trace.nettrace` .</span><span class="sxs-lookup"><span data-stu-id="db3e0-135">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="db3e0-136">A ID do processo da qual coletar o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="db3e0-136">The process id to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="db3e0-137">Um conjunto nomeado predefinido de configurações de provedor que permite que cenários de rastreamento comuns sejam especificados de forma sucinta.</span><span class="sxs-lookup"><span data-stu-id="db3e0-137">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="db3e0-138">Uma lista separada por vírgulas de `EventPipe` provedores a serem habilitados.</span><span class="sxs-lookup"><span data-stu-id="db3e0-138">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="db3e0-139">Esses provedores complementam todos os provedores implícitos pelo `--profile <profile-name>` .</span><span class="sxs-lookup"><span data-stu-id="db3e0-139">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="db3e0-140">Se houver alguma inconsistência para um provedor específico, essa configuração terá precedência sobre a configuração implícita do perfil.</span><span class="sxs-lookup"><span data-stu-id="db3e0-140">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="db3e0-141">Esta lista de provedores está no formato:</span><span class="sxs-lookup"><span data-stu-id="db3e0-141">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="db3e0-142">`Provider`está no formato: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` .</span><span class="sxs-lookup"><span data-stu-id="db3e0-142">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="db3e0-143">`KeyValueArgs`está no formato: `[key1=value1][;key2=value2]` .</span><span class="sxs-lookup"><span data-stu-id="db3e0-143">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="db3e0-144">dotnet-conversão de rastreamento</span><span class="sxs-lookup"><span data-stu-id="db3e0-144">dotnet-trace convert</span></span>

<span data-ttu-id="db3e0-145">Converte `nettrace` rastreamentos em formatos alternativos para uso com ferramentas de análise de rastreamento alternativas.</span><span class="sxs-lookup"><span data-stu-id="db3e0-145">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="db3e0-146">Sinopse</span><span class="sxs-lookup"><span data-stu-id="db3e0-146">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="db3e0-147">Argumentos</span><span class="sxs-lookup"><span data-stu-id="db3e0-147">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="db3e0-148">Arquivo de rastreamento de entrada a ser convertido.</span><span class="sxs-lookup"><span data-stu-id="db3e0-148">Input trace file to be converted.</span></span> <span data-ttu-id="db3e0-149">O padrão é *trace. NetTrace*.</span><span class="sxs-lookup"><span data-stu-id="db3e0-149">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="db3e0-150">Opções</span><span class="sxs-lookup"><span data-stu-id="db3e0-150">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="db3e0-151">Define o formato de saída para a conversão do arquivo de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="db3e0-151">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="db3e0-152">Nome de arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="db3e0-152">Output filename.</span></span> <span data-ttu-id="db3e0-153">A extensão do formato de destino será adicionada.</span><span class="sxs-lookup"><span data-stu-id="db3e0-153">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="db3e0-154">dotnet-rastrear PS</span><span class="sxs-lookup"><span data-stu-id="db3e0-154">dotnet-trace ps</span></span>

 <span data-ttu-id="db3e0-155">Lista os processos dotnet dos quais os rastreamentos podem ser coletados.</span><span class="sxs-lookup"><span data-stu-id="db3e0-155">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="db3e0-156">Sinopse</span><span class="sxs-lookup"><span data-stu-id="db3e0-156">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="db3e0-157">dotnet-lista de rastreamento-perfis</span><span class="sxs-lookup"><span data-stu-id="db3e0-157">dotnet-trace list-profiles</span></span>

<span data-ttu-id="db3e0-158">Lista os perfis de rastreamento pré-criados com uma descrição de quais provedores e filtros estão em cada perfil.</span><span class="sxs-lookup"><span data-stu-id="db3e0-158">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="db3e0-159">Sinopse</span><span class="sxs-lookup"><span data-stu-id="db3e0-159">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="db3e0-160">Coletar um rastreamento com dotnet-Trace</span><span class="sxs-lookup"><span data-stu-id="db3e0-160">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="db3e0-161">Para coletar rastreamentos usando `dotnet-trace` :</span><span class="sxs-lookup"><span data-stu-id="db3e0-161">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="db3e0-162">Obtenha o identificador do processo (PID) do aplicativo .NET Core do qual coletar rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="db3e0-162">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="db3e0-163">No Windows, você pode usar o Gerenciador de tarefas ou o `tasklist` comando, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="db3e0-163">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="db3e0-164">No Linux, por exemplo, o `ps` comando.</span><span class="sxs-lookup"><span data-stu-id="db3e0-164">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="db3e0-165">dotnet-rastrear PS</span><span class="sxs-lookup"><span data-stu-id="db3e0-165">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="db3e0-166">Execute o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="db3e0-166">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="db3e0-167">O comando anterior gera uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="db3e0-167">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="db3e0-168">Pare a coleta pressionando a `<Enter>` tecla.</span><span class="sxs-lookup"><span data-stu-id="db3e0-168">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="db3e0-169">`dotnet-trace`encerrará eventos de log no arquivo *trace. NetTrace* .</span><span class="sxs-lookup"><span data-stu-id="db3e0-169">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="db3e0-170">Exibir o rastreamento capturado de dotnet-Trace</span><span class="sxs-lookup"><span data-stu-id="db3e0-170">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="db3e0-171">No Windows, os arquivos *. NetTrace* podem ser exibidos em [Perfview](https://github.com/microsoft/perfview) para análise: para rastreamentos coletados em outras plataformas, o arquivo de rastreamento pode ser movido para um computador Windows para ser exibido em Perfview.</span><span class="sxs-lookup"><span data-stu-id="db3e0-171">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="db3e0-172">No Linux, o rastreamento pode ser exibido alterando o formato de saída de `dotnet-trace` para `speedscope` .</span><span class="sxs-lookup"><span data-stu-id="db3e0-172">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="db3e0-173">O formato do arquivo de saída pode ser alterado usando a `-f|--format` opção- `-f speedscope` fará com que o `dotnet-trace` produza um `speedscope` arquivo.</span><span class="sxs-lookup"><span data-stu-id="db3e0-173">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="db3e0-174">Você pode escolher entre `nettrace` (a opção padrão) e `speedscope` .</span><span class="sxs-lookup"><span data-stu-id="db3e0-174">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="db3e0-175">`Speedscope`os arquivos podem ser abertos em <https://www.speedscope.app> .</span><span class="sxs-lookup"><span data-stu-id="db3e0-175">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="db3e0-176">O tempo de execução do .NET Core gera rastreamentos no `nettrace` formato.</span><span class="sxs-lookup"><span data-stu-id="db3e0-176">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="db3e0-177">Os rastreamentos são convertidos em speedscope (se especificado) após a conclusão do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="db3e0-177">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="db3e0-178">Como algumas conversões podem resultar em perda de dados, o arquivo original `nettrace` é preservado ao lado do arquivo convertido.</span><span class="sxs-lookup"><span data-stu-id="db3e0-178">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="db3e0-179">Usar o rastreamento dotnet para coletar valores de contador ao longo do tempo</span><span class="sxs-lookup"><span data-stu-id="db3e0-179">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="db3e0-180">`dotnet-trace`podem</span><span class="sxs-lookup"><span data-stu-id="db3e0-180">`dotnet-trace` can:</span></span>

* <span data-ttu-id="db3e0-181">Use `EventCounter` para o monitoramento de integridade básico em ambientes sensíveis ao desempenho.</span><span class="sxs-lookup"><span data-stu-id="db3e0-181">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="db3e0-182">Por exemplo, em produção.</span><span class="sxs-lookup"><span data-stu-id="db3e0-182">For example, in production.</span></span>
* <span data-ttu-id="db3e0-183">Colete rastreamentos para que eles não precisem ser exibidos em tempo real.</span><span class="sxs-lookup"><span data-stu-id="db3e0-183">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="db3e0-184">Por exemplo, para coletar valores de contador de desempenho de tempo de execução, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="db3e0-184">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="db3e0-185">O comando anterior informa os contadores de tempo de execução para relatar uma vez a cada segundo para monitoramento de integridade leve.</span><span class="sxs-lookup"><span data-stu-id="db3e0-185">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="db3e0-186">Substituir `EventCounterIntervalSec=1` por um valor mais alto (por exemplo, 60) permite a coleta de um rastreamento menor com menos granularidade nos dados do contador.</span><span class="sxs-lookup"><span data-stu-id="db3e0-186">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="db3e0-187">O comando a seguir reduz a sobrecarga e o tamanho do rastreamento mais do que o anterior:</span><span class="sxs-lookup"><span data-stu-id="db3e0-187">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="db3e0-188">O comando anterior desabilita os eventos de tempo de execução e o profiler de pilha gerenciado.</span><span class="sxs-lookup"><span data-stu-id="db3e0-188">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="db3e0-189">Provedores .NET</span><span class="sxs-lookup"><span data-stu-id="db3e0-189">.NET Providers</span></span>

<span data-ttu-id="db3e0-190">O tempo de execução do .NET Core dá suporte aos provedores .NET a seguir.</span><span class="sxs-lookup"><span data-stu-id="db3e0-190">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="db3e0-191">O .NET Core usa as mesmas palavras-chave para habilitar `Event Tracing for Windows (ETW)` os `EventPipe` rastreamentos e.</span><span class="sxs-lookup"><span data-stu-id="db3e0-191">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="db3e0-192">Nome do provedor</span><span class="sxs-lookup"><span data-stu-id="db3e0-192">Provider name</span></span>                            | <span data-ttu-id="db3e0-193">Informações do</span><span class="sxs-lookup"><span data-stu-id="db3e0-193">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="db3e0-194">O provedor de runtime</span><span class="sxs-lookup"><span data-stu-id="db3e0-194">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="db3e0-195">Palavras-chave de tempo de execução CLR</span><span class="sxs-lookup"><span data-stu-id="db3e0-195">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="db3e0-196">O provedor de encerramento</span><span class="sxs-lookup"><span data-stu-id="db3e0-196">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="db3e0-197">Palavras-chave de resumo do CLR</span><span class="sxs-lookup"><span data-stu-id="db3e0-197">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="db3e0-198">Habilita o criador de perfil de exemplo.</span><span class="sxs-lookup"><span data-stu-id="db3e0-198">Enables the sample profiler.</span></span> |
