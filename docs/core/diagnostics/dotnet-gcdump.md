---
title: dotnet-gcdump-.NET Core
description: Instalando e usando a ferramenta de linha de comando dotnet-gcdump.
ms.date: 07/26/2020
ms.openlocfilehash: a7b19f4d7487677b975621e7267a17894dae2e3a
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656645"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="b10b5-103">Ferramenta de análise de heap (dotNet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="b10b5-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="b10b5-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 3,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="b10b5-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install-dotnet-gcdump"></a><span data-ttu-id="b10b5-105">Instalar dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="b10b5-105">Install dotnet-gcdump</span></span>

<span data-ttu-id="b10b5-106">Para instalar a versão de lançamento mais recente do `dotnet-gcdump` [pacote NuGet](https://www.nuget.org/packages/dotnet-gcdump), use o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="b10b5-106">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-gcdump
```

## <a name="synopsis"></a><span data-ttu-id="b10b5-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="b10b5-107">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="b10b5-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b10b5-108">Description</span></span>

<span data-ttu-id="b10b5-109">A `dotnet-gcdump` ferramenta global é uma maneira de coletar despejos de GC (coletor de lixo) de processos do .net em tempo real.</span><span class="sxs-lookup"><span data-stu-id="b10b5-109">The `dotnet-gcdump` global tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span> <span data-ttu-id="b10b5-110">Ele usa a tecnologia EventPipe, que é uma alternativa de plataforma cruzada para o ETW no Windows.</span><span class="sxs-lookup"><span data-stu-id="b10b5-110">It uses the EventPipe technology, which is a cross-platform alternative to ETW on Windows.</span></span> <span data-ttu-id="b10b5-111">Os despejos de GC são criados disparando um GC no processo de destino, ativando eventos especiais e regenerando o grafo de raízes de objeto a partir do fluxo de eventos.</span><span class="sxs-lookup"><span data-stu-id="b10b5-111">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="b10b5-112">Esse processo permite que os despejos de GC sejam coletados enquanto o processo está em execução e com sobrecarga mínima.</span><span class="sxs-lookup"><span data-stu-id="b10b5-112">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="b10b5-113">Esses despejos são úteis para vários cenários:</span><span class="sxs-lookup"><span data-stu-id="b10b5-113">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="b10b5-114">Comparando o número de objetos no heap em vários pontos no tempo.</span><span class="sxs-lookup"><span data-stu-id="b10b5-114">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="b10b5-115">Análise de raízes de objetos (respondendo a perguntas como "o que ainda tem uma referência a esse tipo?").</span><span class="sxs-lookup"><span data-stu-id="b10b5-115">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="b10b5-116">Coletando estatísticas gerais sobre as contagens de objetos no heap.</span><span class="sxs-lookup"><span data-stu-id="b10b5-116">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="b10b5-117">Exibir o despejo de GC capturado de dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="b10b5-117">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="b10b5-118">No Windows, `.gcdump` os arquivos podem ser exibidos no [Perfview](https://github.com/microsoft/perfview) para análise ou no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b10b5-118">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="b10b5-119">Atualmente, não há nenhuma maneira de abrir um `.gcdump` em plataformas não Windows.</span><span class="sxs-lookup"><span data-stu-id="b10b5-119">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="b10b5-120">Você pode coletar vários `.gcdump` s e abri-los simultaneamente no Visual Studio para obter uma experiência de comparação.</span><span class="sxs-lookup"><span data-stu-id="b10b5-120">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="b10b5-121">Opções</span><span class="sxs-lookup"><span data-stu-id="b10b5-121">Options</span></span>

- **`--version`**

  <span data-ttu-id="b10b5-122">Exibe a versão do `dotnet-gcdump` Utilitário do.</span><span class="sxs-lookup"><span data-stu-id="b10b5-122">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b10b5-123">Mostra a ajuda da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="b10b5-123">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="b10b5-124">Coleta um despejo de GC de um processo em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="b10b5-124">Collects a GC dump from a currently running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b10b5-125">Sinopse</span><span class="sxs-lookup"><span data-stu-id="b10b5-125">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="b10b5-126">Opções</span><span class="sxs-lookup"><span data-stu-id="b10b5-126">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="b10b5-127">Mostra a ajuda da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="b10b5-127">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="b10b5-128">A ID do processo para coletar o despejo do GC.</span><span class="sxs-lookup"><span data-stu-id="b10b5-128">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="b10b5-129">O caminho onde os despejos de GC coletados devem ser gravados.</span><span class="sxs-lookup"><span data-stu-id="b10b5-129">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="b10b5-130">O padrão é *. \\ AAAAMMDD \_ HHMMSS \_ \<pid> . gcdump*.</span><span class="sxs-lookup"><span data-stu-id="b10b5-130">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="b10b5-131">Gere o log durante a coleta do despejo do GC.</span><span class="sxs-lookup"><span data-stu-id="b10b5-131">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="b10b5-132">Desistir da coleta do despejo do GC se levar mais tempo do que esse número de segundos.</span><span class="sxs-lookup"><span data-stu-id="b10b5-132">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="b10b5-133">O valor padrão é 30.</span><span class="sxs-lookup"><span data-stu-id="b10b5-133">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="b10b5-134">O nome do processo do qual coletar o despejo do GC.</span><span class="sxs-lookup"><span data-stu-id="b10b5-134">The name of the process to collect the GC dump from.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="b10b5-135">Lista os processos dotnet para os quais os despejos de GC podem ser coletados.</span><span class="sxs-lookup"><span data-stu-id="b10b5-135">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b10b5-136">Sinopse</span><span class="sxs-lookup"><span data-stu-id="b10b5-136">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="b10b5-137">Gere um relatório de um despejo GC gerado anteriormente ou de um processo em execução e grave no `stdout` .</span><span class="sxs-lookup"><span data-stu-id="b10b5-137">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b10b5-138">Sinopse</span><span class="sxs-lookup"><span data-stu-id="b10b5-138">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="b10b5-139">Opções</span><span class="sxs-lookup"><span data-stu-id="b10b5-139">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="b10b5-140">Mostra a ajuda da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="b10b5-140">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="b10b5-141">A ID do processo para coletar o despejo do GC.</span><span class="sxs-lookup"><span data-stu-id="b10b5-141">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="b10b5-142">O tipo de relatório a ser gerado.</span><span class="sxs-lookup"><span data-stu-id="b10b5-142">The type of report to generate.</span></span> <span data-ttu-id="b10b5-143">Opções disponíveis: heapstat (padrão).</span><span class="sxs-lookup"><span data-stu-id="b10b5-143">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="b10b5-144">Solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="b10b5-144">Troubleshoot</span></span>

- <span data-ttu-id="b10b5-145">Não há nenhuma informação de tipo no gcdump.</span><span class="sxs-lookup"><span data-stu-id="b10b5-145">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="b10b5-146">Antes do .NET Core 3,1, houve um problema em que um cache de tipo não foi limpo entre gcdumps quando eles eram invocados com EventPipe.</span><span class="sxs-lookup"><span data-stu-id="b10b5-146">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="b10b5-147">Isso resultou nos eventos necessários para determinar as informações de tipo que não estão sendo enviadas para o segundo e o gcdumps subsequente.</span><span class="sxs-lookup"><span data-stu-id="b10b5-147">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="b10b5-148">Isso foi corrigido no .NET Core 3,1-Preview2.</span><span class="sxs-lookup"><span data-stu-id="b10b5-148">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="b10b5-149">Os tipos COM e estáticos não estão no despejo de GC.</span><span class="sxs-lookup"><span data-stu-id="b10b5-149">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="b10b5-150">Antes do .NET Core 3,1-Preview2, houve um problema em que os tipos static e COM não eram enviados quando o despejo de GC era invocado via EventPipe.</span><span class="sxs-lookup"><span data-stu-id="b10b5-150">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="b10b5-151">Isso foi corrigido no .NET Core 3,1-Preview2.</span><span class="sxs-lookup"><span data-stu-id="b10b5-151">This has been fixed in .NET Core 3.1-preview2.</span></span>
