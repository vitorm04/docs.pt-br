---
title: Registro em log e rastreamento – .NET Core
description: Uma introdução ao rastreamento e registro em log do .NET Core.
ms.date: 10/12/2020
ms.openlocfilehash: e3f809dab64d66d8b4ba16ca55fc426309614715
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439918"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="1be11-103">Log e rastreamento do .NET Core</span><span class="sxs-lookup"><span data-stu-id="1be11-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="1be11-104">O registro em log e o rastreamento são, na verdade, dois nomes para a mesma técnica.</span><span class="sxs-lookup"><span data-stu-id="1be11-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="1be11-105">A técnica simples foi usada desde os primórdios dos computadores.</span><span class="sxs-lookup"><span data-stu-id="1be11-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="1be11-106">Ele simplesmente envolve a instrumentação de um aplicativo para gravar a saída a ser consumida posteriormente.</span><span class="sxs-lookup"><span data-stu-id="1be11-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="1be11-107">Motivos para usar o log e o rastreamento</span><span class="sxs-lookup"><span data-stu-id="1be11-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="1be11-108">Essa técnica simples é surpreendentemente poderosa.</span><span class="sxs-lookup"><span data-stu-id="1be11-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="1be11-109">Ele pode ser usado em situações em que um depurador falha:</span><span class="sxs-lookup"><span data-stu-id="1be11-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="1be11-110">Problemas que ocorrem por longos períodos podem ser difíceis de depurar com um depurador tradicional.</span><span class="sxs-lookup"><span data-stu-id="1be11-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="1be11-111">Os logs permitem uma análise detalhada post mortem, abrangendo longos períodos.</span><span class="sxs-lookup"><span data-stu-id="1be11-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="1be11-112">Por outro lado, os depuradores são limitados a análises em tempo real.</span><span class="sxs-lookup"><span data-stu-id="1be11-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="1be11-113">Aplicativos distribuídos e com multithread costumam ser difíceis de depurar.</span><span class="sxs-lookup"><span data-stu-id="1be11-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="1be11-114">A anexação de um depurador tende a modificar comportamentos.</span><span class="sxs-lookup"><span data-stu-id="1be11-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="1be11-115">Logs detalhados podem ser analisados conforme necessário para entender sistemas complexos.</span><span class="sxs-lookup"><span data-stu-id="1be11-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="1be11-116">Problemas em aplicativos distribuídos podem surgir de uma interação complexa entre vários componentes, e talvez não seja plausível conectar um depurador a todas as partes do sistema.</span><span class="sxs-lookup"><span data-stu-id="1be11-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="1be11-117">Muitos serviços não devem ser interrompidos.</span><span class="sxs-lookup"><span data-stu-id="1be11-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="1be11-118">A anexação de um depurador geralmente causa falhas de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="1be11-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="1be11-119">Os problemas nem sempre são previstos.</span><span class="sxs-lookup"><span data-stu-id="1be11-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="1be11-120">O registro em log e o rastreamento são projetados para baixa sobrecarga, de modo que os programas possam ser gravados caso ocorra um problema.</span><span class="sxs-lookup"><span data-stu-id="1be11-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="1be11-121">APIs do .NET Core</span><span class="sxs-lookup"><span data-stu-id="1be11-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="1be11-122">APIs de estilo de impressão</span><span class="sxs-lookup"><span data-stu-id="1be11-122">Print style APIs</span></span>

<span data-ttu-id="1be11-123">As <xref:System.Console?displayProperty=nameWithType> <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes, e <xref:System.Diagnostics.Debug?displayProperty=nameWithType> fornecem, cada uma, APIs semelhantes de estilo de impressão conveniente para o registro em log.</span><span class="sxs-lookup"><span data-stu-id="1be11-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="1be11-124">A escolha da API de estilo de impressão a ser usada cabe a você.</span><span class="sxs-lookup"><span data-stu-id="1be11-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="1be11-125">As principais diferenças são:</span><span class="sxs-lookup"><span data-stu-id="1be11-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="1be11-126">Está sempre habilitado e sempre grava no console.</span><span class="sxs-lookup"><span data-stu-id="1be11-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="1be11-127">Útil para informações que seu cliente talvez precise ver na versão.</span><span class="sxs-lookup"><span data-stu-id="1be11-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="1be11-128">Por ser a abordagem mais simples, costuma ser usado para a depuração temporária ad hoc.</span><span class="sxs-lookup"><span data-stu-id="1be11-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="1be11-129">Geralmente, esse código de depuração nunca é submetido a check-in no controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="1be11-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="1be11-130">Habilitado somente quando `TRACE` é definido.</span><span class="sxs-lookup"><span data-stu-id="1be11-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="1be11-131">Grava em anexado <xref:System.Diagnostics.Trace.Listeners> , por padrão, o <xref:System.Diagnostics.DefaultTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="1be11-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="1be11-132">Use essa API ao criar logs que serão habilitados na maioria dos builds.</span><span class="sxs-lookup"><span data-stu-id="1be11-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="1be11-133">Habilitado somente quando `DEBUG` é definido.</span><span class="sxs-lookup"><span data-stu-id="1be11-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="1be11-134">Grava em um depurador anexado.</span><span class="sxs-lookup"><span data-stu-id="1be11-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="1be11-135">Em `*nix` gravações em stderr, se `COMPlus_DebugWriteToStdErr` estiver definido.</span><span class="sxs-lookup"><span data-stu-id="1be11-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="1be11-136">Use essa API ao criar logs que serão habilitados apenas nos builds de depuração.</span><span class="sxs-lookup"><span data-stu-id="1be11-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="1be11-137">Eventos de log</span><span class="sxs-lookup"><span data-stu-id="1be11-137">Logging events</span></span>

<span data-ttu-id="1be11-138">As APIs a seguir são mais orientadas a eventos.</span><span class="sxs-lookup"><span data-stu-id="1be11-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="1be11-139">Em vez de registrar cadeias de caracteres simples, eles registram objetos de evento.</span><span class="sxs-lookup"><span data-stu-id="1be11-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="1be11-140">EventSource é a principal API de rastreamento do .NET Core raiz.</span><span class="sxs-lookup"><span data-stu-id="1be11-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="1be11-141">Disponível em todas as versões de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1be11-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="1be11-142">Permite apenas rastrear objetos serializáveis.</span><span class="sxs-lookup"><span data-stu-id="1be11-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="1be11-143">Pode ser consumido em processo por meio de todas as instâncias de [EventListener](xref:System.Diagnostics.Tracing.EventListener) configuradas para consumir a EventSource.</span><span class="sxs-lookup"><span data-stu-id="1be11-143">Can be consumed in-process via any [EventListener](xref:System.Diagnostics.Tracing.EventListener) instances configured to consume the EventSource.</span></span>
  - <span data-ttu-id="1be11-144">Pode ser consumido fora do processo por meio de:</span><span class="sxs-lookup"><span data-stu-id="1be11-144">Can be consumed out-of-process via:</span></span>
    - <span data-ttu-id="1be11-145">EventPipe do .NET Core em todas as plataformas</span><span class="sxs-lookup"><span data-stu-id="1be11-145">.NET Core's EventPipe on all platforms</span></span>
    - [<span data-ttu-id="1be11-146">ETW (Rastreamento de Eventos para Windows)</span><span class="sxs-lookup"><span data-stu-id="1be11-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="1be11-147">Estrutura de rastreamento do LTTng para Linux</span><span class="sxs-lookup"><span data-stu-id="1be11-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)
      - <span data-ttu-id="1be11-148">Walkthrough: [coletar um rastreamento de LTTng usando PerfCollect](trace-perfcollect-lttng.md).</span><span class="sxs-lookup"><span data-stu-id="1be11-148">Walkthrough: [Collect an LTTng trace using PerfCollect](trace-perfcollect-lttng.md).</span></span>

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="1be11-149">Incluído no .NET Core e como um [pacote NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) para .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1be11-149">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="1be11-150">Permite o rastreamento em processo de objetos não serializáveis.</span><span class="sxs-lookup"><span data-stu-id="1be11-150">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="1be11-151">Inclui uma ponte para permitir que os campos selecionados de objetos registrados sejam gravados em um <xref:System.Diagnostics.Tracing.EventSource> .</span><span class="sxs-lookup"><span data-stu-id="1be11-151">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="1be11-152">Fornece uma maneira definitiva de identificar mensagens de log resultantes de uma atividade ou transação específica.</span><span class="sxs-lookup"><span data-stu-id="1be11-152">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="1be11-153">Esse objeto pode ser usado para correlacionar logs entre diferentes serviços.</span><span class="sxs-lookup"><span data-stu-id="1be11-153">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="1be11-154">Somente Windows.</span><span class="sxs-lookup"><span data-stu-id="1be11-154">Windows only.</span></span>
  - <span data-ttu-id="1be11-155">Grava mensagens no log de eventos do Windows.</span><span class="sxs-lookup"><span data-stu-id="1be11-155">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="1be11-156">Os administradores do sistema esperam que as mensagens de erro fatais do aplicativo apareçam no log de eventos do Windows.</span><span class="sxs-lookup"><span data-stu-id="1be11-156">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="1be11-157">ILogger e estruturas de registro em log</span><span class="sxs-lookup"><span data-stu-id="1be11-157">ILogger and logging frameworks</span></span>

<span data-ttu-id="1be11-158">As APIs de nível baixo podem não ser a escolha certa para suas necessidades de registro em log.</span><span class="sxs-lookup"><span data-stu-id="1be11-158">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="1be11-159">Talvez você queira considerar uma estrutura de registro em log.</span><span class="sxs-lookup"><span data-stu-id="1be11-159">You may want to consider a logging framework.</span></span>

<span data-ttu-id="1be11-160">A <xref:Microsoft.Extensions.Logging.ILogger> interface foi usada para criar uma interface de log comum em que os agentes podem ser inseridos por meio da injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="1be11-160">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="1be11-161">Por exemplo, para permitir que você faça a melhor escolha para o seu aplicativo, o .NET oferece suporte para uma seleção de estruturas internas e de terceiros:</span><span class="sxs-lookup"><span data-stu-id="1be11-161">For instance, to allow you to make the best choice for your application .NET offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="1be11-162">Provedores de log internos do .NET</span><span class="sxs-lookup"><span data-stu-id="1be11-162">.NET Built-in logging providers</span></span>](../extensions/logging-providers.md#built-in-logging-providers)
- [<span data-ttu-id="1be11-163">Provedores de log de terceiros do .NET</span><span class="sxs-lookup"><span data-stu-id="1be11-163">.NET Third-party logging providers</span></span>](../extensions/logging-providers.md#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="1be11-164">Referências relacionadas ao log</span><span class="sxs-lookup"><span data-stu-id="1be11-164">Logging related references</span></span>

- [<span data-ttu-id="1be11-165">Como: compilar condicionalmente com Trace e Debug</span><span class="sxs-lookup"><span data-stu-id="1be11-165">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="1be11-166">Como: adicionar instruções de rastreamento ao código de um aplicativo</span><span class="sxs-lookup"><span data-stu-id="1be11-166">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="1be11-167">O [registro em log no .net](../extensions/logging.md) fornece uma visão geral das técnicas de log que ele suporta.</span><span class="sxs-lookup"><span data-stu-id="1be11-167">[Logging in .NET](../extensions/logging.md) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="1be11-168">A [interpolação de cadeia de caracteres C#](../../csharp/language-reference/tokens/interpolated.md) pode simplificar o código de registro</span><span class="sxs-lookup"><span data-stu-id="1be11-168">[C# string interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- <span data-ttu-id="1be11-169">A <xref:System.Exception.Message?displayProperty=nameWithType> propriedade é útil para registrar exceções.</span><span class="sxs-lookup"><span data-stu-id="1be11-169">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="1be11-170">A <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> classe pode ser útil para fornecer informações de pilha em seus logs.</span><span class="sxs-lookup"><span data-stu-id="1be11-170">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="1be11-171">Considerações sobre o desempenho</span><span class="sxs-lookup"><span data-stu-id="1be11-171">Performance considerations</span></span>

<span data-ttu-id="1be11-172">A formatação da cadeia de caracteres pode levar tempo de processamento de CPU perceptível.</span><span class="sxs-lookup"><span data-stu-id="1be11-172">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="1be11-173">Em aplicativos de desempenho crítico, é recomendável que você:</span><span class="sxs-lookup"><span data-stu-id="1be11-173">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="1be11-174">Evite muitos registros em log quando ninguém estiver ouvindo.</span><span class="sxs-lookup"><span data-stu-id="1be11-174">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="1be11-175">Evite construir mensagens de registro em log dispendiosas verificando se o log está habilitado primeiro.</span><span class="sxs-lookup"><span data-stu-id="1be11-175">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="1be11-176">Registre apenas o que é útil.</span><span class="sxs-lookup"><span data-stu-id="1be11-176">Only log what's useful.</span></span>
- <span data-ttu-id="1be11-177">Adie a formatação sofisticada para o estágio de análise.</span><span class="sxs-lookup"><span data-stu-id="1be11-177">Defer fancy formatting to the analysis stage.</span></span>
