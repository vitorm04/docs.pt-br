---
title: Controlando o registro em log no .NET Framework
description: Use o ETW (rastreamento de eventos para Windows) para controlar o log do .NET e registrar eventos de Common Language Runtime (CLR). Use ferramentas como logman, Tracerpt e Xperf.
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
ms.openlocfilehash: bce5ea41149dc3b19106031fae202872dd8a8fb5
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553799"
---
# <a name="controlling-net-framework-logging"></a><span data-ttu-id="03831-104">Controlando o registro em log no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="03831-104">Controlling .NET Framework Logging</span></span>

<span data-ttu-id="03831-105">Você pode usar o ETW (Rastreamento de Eventos para Windows) para registrar eventos de CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="03831-105">You can use event tracing for Windows (ETW) to record common language runtime (CLR) events.</span></span> <span data-ttu-id="03831-106">Você pode criar e exibir rastros usando as seguintes ferramentas:</span><span class="sxs-lookup"><span data-stu-id="03831-106">You can create and view traces by using the following tools:</span></span>

- <span data-ttu-id="03831-107">As ferramentas de linha de comando [Logman](/windows-server/administration/windows-commands/logman) e [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1), ambas incluídas no sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="03831-107">The [Logman](/windows-server/administration/windows-commands/logman) and [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) command-line tools, which are included with the Windows operating system.</span></span>

- <span data-ttu-id="03831-108">As ferramentas [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) no [Windows Performance Toolkit](/windows-hardware/test/wpt/).</span><span class="sxs-lookup"><span data-stu-id="03831-108">The [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools in the [Windows Performance Toolkit](/windows-hardware/test/wpt/).</span></span> <span data-ttu-id="03831-109">Para obter mais informações sobre o Xperf, visite o [blog de Desempenho do Windows](/archive/blogs/pigscanfly/).</span><span class="sxs-lookup"><span data-stu-id="03831-109">For more information about Xperf, see the [Windows Performance blog](/archive/blogs/pigscanfly/).</span></span>

<span data-ttu-id="03831-110">Para capturar informações de eventos de CLR, o provedor de CLR deve estar instalado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="03831-110">To capture CLR event information, the CLR provider must be installed on your computer.</span></span> <span data-ttu-id="03831-111">Para confirmar que o provedor está instalado, digite `logman query providers` no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="03831-111">To confirm that the provider is installed, type `logman query providers` at the command prompt.</span></span> <span data-ttu-id="03831-112">Uma lista de provedores é exibida.</span><span class="sxs-lookup"><span data-stu-id="03831-112">A list of providers is displayed.</span></span> <span data-ttu-id="03831-113">Essa lista deve conter uma entrada para o provedor CLR, conforme mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="03831-113">This list should contain an entry for the CLR provider, as follows.</span></span>

```output
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

<span data-ttu-id="03831-114">Se o provedor CLR não estiver listado, você poderá instalá-lo no Windows Vista e em sistemas operacionais posteriores usando a ferramenta de linha de comando [Wevtutil](/windows-server/administration/windows-commands/wevtutil) do Windows.</span><span class="sxs-lookup"><span data-stu-id="03831-114">If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil) command-line tool.</span></span> <span data-ttu-id="03831-115">Abra uma janela de prompt de comando como administrador.</span><span class="sxs-lookup"><span data-stu-id="03831-115">Open the Command Prompt window as an administrator.</span></span> <span data-ttu-id="03831-116">Altere o diretório de prompts para a pasta .NET Framework 4 (%WINDIR%\Microsoft.NET\Framework [64] \v4. \<.NET version> \ ).</span><span class="sxs-lookup"><span data-stu-id="03831-116">Change the prompt directory to the .NET Framework 4 folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ).</span></span> <span data-ttu-id="03831-117">Esta pasta contém o arquivo CLR-ETW.man.</span><span class="sxs-lookup"><span data-stu-id="03831-117">This folder contains the CLR-ETW.man file.</span></span> <span data-ttu-id="03831-118">No prompt de comando, digite o seguinte comando para instalar o provedor de CLR:</span><span class="sxs-lookup"><span data-stu-id="03831-118">At the command prompt, type the following command to install the CLR provider:</span></span>

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a><span data-ttu-id="03831-119">Capturando eventos de CLR com o ETW</span><span class="sxs-lookup"><span data-stu-id="03831-119">Capturing CLR ETW Events</span></span>

<span data-ttu-id="03831-120">Use as ferramentas de linha de comando [Logman](/windows-server/administration/windows-commands/logman) e [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) para capturar eventos ETW e as ferramentas [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) e [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) para decodificar eventos de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="03831-120">You can use the [Logman](/windows-server/administration/windows-commands/logman) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) command-line tools to capture ETW events, and the [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools to decode the trace events.</span></span>

<span data-ttu-id="03831-121">Para ativar o log, um usuário deve especificar três coisas:</span><span class="sxs-lookup"><span data-stu-id="03831-121">To turn on logging, a user must specify three things:</span></span>

- <span data-ttu-id="03831-122">O provedor com o qual a comunicação será feita.</span><span class="sxs-lookup"><span data-stu-id="03831-122">The provider to communicate to.</span></span>

- <span data-ttu-id="03831-123">Um número de 64 bits que representa um conjunto de palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="03831-123">A 64-bit number that represents a set of keywords.</span></span> <span data-ttu-id="03831-124">Cada palavra-chave representa um conjunto de eventos que o provedor pode ativar.</span><span class="sxs-lookup"><span data-stu-id="03831-124">Each keyword represents a set of events that the provider can turn on.</span></span> <span data-ttu-id="03831-125">O número representa um conjunto combinado de palavras-chave para ativar.</span><span class="sxs-lookup"><span data-stu-id="03831-125">The number represents a combined set of keywords to turn on.</span></span>

- <span data-ttu-id="03831-126">Um número pequeno representando o nível (detalhamento) em que o registro será feito.</span><span class="sxs-lookup"><span data-stu-id="03831-126">A small number representing the level (verbosity) to log at.</span></span> <span data-ttu-id="03831-127">O nível 1 é o menos detalhado, enquanto que o nível 5 é o mais detalhado.</span><span class="sxs-lookup"><span data-stu-id="03831-127">Level 1 is the least verbose, and level 5 is the most verbose.</span></span> <span data-ttu-id="03831-128">O nível 0 é um padrão cujo significado é específico do provedor.</span><span class="sxs-lookup"><span data-stu-id="03831-128">Level 0 is a default whose meaning is provider-specific.</span></span>

### <a name="to-capture-clr-etw-events-using-logman"></a><span data-ttu-id="03831-129">Para capturar eventos ETW de CLR usando o Logman</span><span class="sxs-lookup"><span data-stu-id="03831-129">To capture CLR ETW events using Logman</span></span>

1. <span data-ttu-id="03831-130">No prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="03831-130">At the command prompt, type:</span></span>

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     <span data-ttu-id="03831-131">em que:</span><span class="sxs-lookup"><span data-stu-id="03831-131">where:</span></span>

    - <span data-ttu-id="03831-132">O parâmetro `-p` identifica o GUID do provedor.</span><span class="sxs-lookup"><span data-stu-id="03831-132">The `-p` parameter identifies the provider GUID.</span></span>

    - <span data-ttu-id="03831-133">`0x1CCBD` especifica as categorias de eventos que serão geradas.</span><span class="sxs-lookup"><span data-stu-id="03831-133">`0x1CCBD` specifies the categories of events that will be raised.</span></span>

    - <span data-ttu-id="03831-134">`0x5` define o nível do log (nesse caso, detalhado (5)).</span><span class="sxs-lookup"><span data-stu-id="03831-134">`0x5` sets the level of logging (in this case, verbose (5)).</span></span>

    - <span data-ttu-id="03831-135">O parâmetro `-ets` instrui o Logman a enviar comandos para a seções de rastreamento de eventos.</span><span class="sxs-lookup"><span data-stu-id="03831-135">The `-ets` parameter instructs Logman to send commands to event tracing sessions.</span></span>

    - <span data-ttu-id="03831-136">O parâmetro `-ct perf` especifica que a função `QueryPerformanceCounter` será usada para registrar o carimbo de data/hora para cada evento.</span><span class="sxs-lookup"><span data-stu-id="03831-136">The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.</span></span>

2. <span data-ttu-id="03831-137">Para parar de registrar os eventos, digite:</span><span class="sxs-lookup"><span data-stu-id="03831-137">To stop logging the events, type:</span></span>

     `logman stop clrevents -ets`

     <span data-ttu-id="03831-138">Este comando cria um arquivo binário de rastreamento chamado clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="03831-138">This command creates a binary trace file named clrevents.etl.</span></span>

### <a name="to-capture-clr-etw-events-using-xperf"></a><span data-ttu-id="03831-139">Para capturar eventos CLR ETW usando o Xperf</span><span class="sxs-lookup"><span data-stu-id="03831-139">To capture CLR ETW events using Xperf</span></span>

1. <span data-ttu-id="03831-140">No prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="03831-140">At the command prompt, type:</span></span>

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     <span data-ttu-id="03831-141">Onde o GUID é o GUID do provedor ETW de CLR, e `0x1CCBD:5` rastreia tudo no nível 5 (detalhado) e nos níveis inferiores.</span><span class="sxs-lookup"><span data-stu-id="03831-141">where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).</span></span>

2. <span data-ttu-id="03831-142">Para parar o rastreamento, digite:</span><span class="sxs-lookup"><span data-stu-id="03831-142">To stop tracing, type:</span></span>

     `Xperf -stop clr`

     <span data-ttu-id="03831-143">Este comando cria um arquivo de rastreamento chamado clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="03831-143">This command creates a trace file named clrevents.etl.</span></span>

## <a name="viewing-clr-etw-events"></a><span data-ttu-id="03831-144">Exibindo eventos ETW de CLR</span><span class="sxs-lookup"><span data-stu-id="03831-144">Viewing CLR ETW Events</span></span>

<span data-ttu-id="03831-145">Use os comandos listados abaixo para exibir os eventos ETW de CLR.</span><span class="sxs-lookup"><span data-stu-id="03831-145">Use the commands listed below to view the CLR ETW events.</span></span> <span data-ttu-id="03831-146">Para obter uma descrição dos eventos, consulte [Eventos CLR ETW](clr-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="03831-146">For a description of the events, see [CLR ETW Events](clr-etw-events.md).</span></span>

### <a name="to-view-clr-etw-events-using-tracerpt"></a><span data-ttu-id="03831-147">Para exibir eventos ETW de CLR usando o Tracerpt</span><span class="sxs-lookup"><span data-stu-id="03831-147">To view CLR ETW events using Tracerpt</span></span>

- <span data-ttu-id="03831-148">No prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="03831-148">At the command prompt, type:</span></span>

     `tracerpt clrevents.etl`

     <span data-ttu-id="03831-149">Este comando cria dois arquivos: dumpfile.xml e summary.txt.</span><span class="sxs-lookup"><span data-stu-id="03831-149">This command creates two files: dumpfile.xml and summary.txt.</span></span> <span data-ttu-id="03831-150">O arquivo dumpfile.xml lista todos os eventos, enquanto que summary.txt fornece um resumo dos eventos.</span><span class="sxs-lookup"><span data-stu-id="03831-150">The dumpfile.xml file lists all the events, and summary.txt provides a summary of the events.</span></span>

### <a name="to-view-clr-etw-events-using-xperf"></a><span data-ttu-id="03831-151">Para exibir eventos ETW de CLR usando Xperf</span><span class="sxs-lookup"><span data-stu-id="03831-151">To view CLR ETW events using Xperf</span></span>

- <span data-ttu-id="03831-152">No prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="03831-152">At the command prompt, type:</span></span>

     `xperf clrevents.etl`

     <span data-ttu-id="03831-153">Este comando abre o visualizador de arquivos Xperf ETL.</span><span class="sxs-lookup"><span data-stu-id="03831-153">This command opens the Xperf ETL file viewer.</span></span> <span data-ttu-id="03831-154">Nesse visualizador, os eventos CLR são mostrados na exibição **Eventos Genéricos**.</span><span class="sxs-lookup"><span data-stu-id="03831-154">In this viewer, the CLR events show up in the **Generic Events** view.</span></span> <span data-ttu-id="03831-155">Para exibir uma grade de dados de eventos categorizados por tipo, selecione uma região de tempo nessa exibição e, em seguida, clique com o botão direito do mouse e selecione **Resumo**.</span><span class="sxs-lookup"><span data-stu-id="03831-155">To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.</span></span>

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a><span data-ttu-id="03831-156">Para converter o arquivo .etl em um arquivo de valores separados por vírgula.</span><span class="sxs-lookup"><span data-stu-id="03831-156">To convert the .etl file to a comma-separated value file</span></span>

- <span data-ttu-id="03831-157">No prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="03831-157">At the command prompt, type:</span></span>

     `xperf -i clrevents.etl -f clrevents.csv`

     <span data-ttu-id="03831-158">Este comando faz com que XPerf despeje os eventos na forma de um arquivo de valores separados por vírgula (CSV) que você pode abrir.</span><span class="sxs-lookup"><span data-stu-id="03831-158">This command causes XPerf to dump the events as a comma separated value (CSV) file that you can view.</span></span> <span data-ttu-id="03831-159">Porque eventos diferentes possuem campos diferentes, esse arquivo CSV contém mais de uma linha de cabeçalho antes dos dados.</span><span class="sxs-lookup"><span data-stu-id="03831-159">Because different events have different fields, this CSV file is contains more than one header line before the data.</span></span> <span data-ttu-id="03831-160">O primeiro campo de cada linha é o tipo de evento, que indica qual cabeçalho deve ser usado para determinar o restante dos campos.</span><span class="sxs-lookup"><span data-stu-id="03831-160">The first field of every line is the event type, which indicates which header should be used to determine the rest of the fields.</span></span>

## <a name="see-also"></a><span data-ttu-id="03831-161">Confira também</span><span class="sxs-lookup"><span data-stu-id="03831-161">See also</span></span>

- [<span data-ttu-id="03831-162">Windows Performance Toolkit</span><span class="sxs-lookup"><span data-stu-id="03831-162">Windows Performance Toolkit</span></span>](/windows-hardware/test/wpt/)
- [<span data-ttu-id="03831-163">Eventos ETW no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="03831-163">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
