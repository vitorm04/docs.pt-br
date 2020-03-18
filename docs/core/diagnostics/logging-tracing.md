---
title: Registro e rastreamento - .NET Core
description: Uma introdução ao .NET Core registrando e rastreando.
ms.date: 08/05/2019
ms.openlocfilehash: 392b88c9ea3c31c919a605ac0a5c886f7d63f79a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714418"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="91c05-103">.NET Core registrando e rastreando</span><span class="sxs-lookup"><span data-stu-id="91c05-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="91c05-104">Registro e rastreamento são realmente dois nomes para a mesma técnica.</span><span class="sxs-lookup"><span data-stu-id="91c05-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="91c05-105">A técnica simples tem sido usada desde os primórdios dos computadores.</span><span class="sxs-lookup"><span data-stu-id="91c05-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="91c05-106">Ele simplesmente envolve instrumentar um aplicativo para gravar saída para ser consumido mais tarde.</span><span class="sxs-lookup"><span data-stu-id="91c05-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="91c05-107">Razões para usar o registro e o rastreamento</span><span class="sxs-lookup"><span data-stu-id="91c05-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="91c05-108">Esta técnica simples é surpreendentemente poderosa.</span><span class="sxs-lookup"><span data-stu-id="91c05-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="91c05-109">Ele pode ser usado em situações em que um depurador falha:</span><span class="sxs-lookup"><span data-stu-id="91c05-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="91c05-110">Problemas que ocorrem por longos períodos de tempo, podem ser difíceis de depurar com um depurador tradicional.</span><span class="sxs-lookup"><span data-stu-id="91c05-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="91c05-111">Os registros permitem uma revisão pós-morte detalhada que abrange longos períodos de tempo.</span><span class="sxs-lookup"><span data-stu-id="91c05-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="91c05-112">Em contraste, os depuradores são limitados à análise em tempo real.</span><span class="sxs-lookup"><span data-stu-id="91c05-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="91c05-113">Aplicativos multi-threaded e aplicativos distribuídos são muitas vezes difíceis de depurar.</span><span class="sxs-lookup"><span data-stu-id="91c05-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="91c05-114">Anexar um depurador tende a modificar comportamentos.</span><span class="sxs-lookup"><span data-stu-id="91c05-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="91c05-115">Registros detalhados podem ser analisados conforme necessário para entender sistemas complexos.</span><span class="sxs-lookup"><span data-stu-id="91c05-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="91c05-116">Problemas em aplicativos distribuídos podem surgir de uma interação complexa entre muitos componentes e pode não ser razoável conectar um depurador a cada parte do sistema.</span><span class="sxs-lookup"><span data-stu-id="91c05-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="91c05-117">Muitos serviços não devem ser paralisados.</span><span class="sxs-lookup"><span data-stu-id="91c05-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="91c05-118">Anexar um depurador muitas vezes causa falhas no tempo.</span><span class="sxs-lookup"><span data-stu-id="91c05-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="91c05-119">Problemas nem sempre são previstos.</span><span class="sxs-lookup"><span data-stu-id="91c05-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="91c05-120">O registro e o rastreamento são projetados para baixa sobrecarga para que os programas possam estar sempre gravando caso ocorra um problema.</span><span class="sxs-lookup"><span data-stu-id="91c05-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="91c05-121">.NET Core APIs</span><span class="sxs-lookup"><span data-stu-id="91c05-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="91c05-122">APIs de estilo de impressão</span><span class="sxs-lookup"><span data-stu-id="91c05-122">Print style APIs</span></span>

<span data-ttu-id="91c05-123">As <xref:System.Console?displayProperty=nameWithType> <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType> e as classes fornecem APIs de estilo de impressão semelhantes convenientes para o registro.</span><span class="sxs-lookup"><span data-stu-id="91c05-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="91c05-124">A escolha de qual API estilo de impressão usar depende de você.</span><span class="sxs-lookup"><span data-stu-id="91c05-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="91c05-125">As principais diferenças são:</span><span class="sxs-lookup"><span data-stu-id="91c05-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="91c05-126">Sempre habilitado e sempre escreve para o console.</span><span class="sxs-lookup"><span data-stu-id="91c05-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="91c05-127">Útil para informações que seu cliente pode precisar ver na versão.</span><span class="sxs-lookup"><span data-stu-id="91c05-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="91c05-128">Por ser a abordagem mais simples, é frequentemente usada para depuração temporária ad-hoc.</span><span class="sxs-lookup"><span data-stu-id="91c05-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="91c05-129">Este código de depuração muitas vezes nunca é verificado no controle de origem.</span><span class="sxs-lookup"><span data-stu-id="91c05-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="91c05-130">Somente ativado `TRACE` quando definido.</span><span class="sxs-lookup"><span data-stu-id="91c05-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="91c05-131">Grava em <xref:System.Diagnostics.Trace.Listeners>anexo, por <xref:System.Diagnostics.DefaultTraceListener>padrão o .</span><span class="sxs-lookup"><span data-stu-id="91c05-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="91c05-132">Use esta API ao criar logs que serão ativados na maioria das compilações.</span><span class="sxs-lookup"><span data-stu-id="91c05-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="91c05-133">Somente ativado `DEBUG` quando definido.</span><span class="sxs-lookup"><span data-stu-id="91c05-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="91c05-134">Grava para um depurador anexado.</span><span class="sxs-lookup"><span data-stu-id="91c05-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="91c05-135">Em `*nix` gravações para `COMPlus_DebugWriteToStdErr` stderr se estiver definido.</span><span class="sxs-lookup"><span data-stu-id="91c05-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="91c05-136">Use esta API ao criar logs que serão ativados apenas em compilações de depuração.</span><span class="sxs-lookup"><span data-stu-id="91c05-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="91c05-137">Eventos de registro</span><span class="sxs-lookup"><span data-stu-id="91c05-137">Logging events</span></span>

<span data-ttu-id="91c05-138">As APIs a seguir são mais orientadas para eventos.</span><span class="sxs-lookup"><span data-stu-id="91c05-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="91c05-139">Em vez de registrar cadeias simples, eles registram objetos de evento.</span><span class="sxs-lookup"><span data-stu-id="91c05-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="91c05-140">EventSource é a API de rastreamento principal do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="91c05-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="91c05-141">Disponível em todas as versões .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="91c05-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="91c05-142">Só permite rastrear objetos serializáveis.</span><span class="sxs-lookup"><span data-stu-id="91c05-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="91c05-143">Escreve para os [ouvintes](xref:System.Diagnostics.Tracing.EventListener)do evento anexado.</span><span class="sxs-lookup"><span data-stu-id="91c05-143">Writes to the attached [event listeners](xref:System.Diagnostics.Tracing.EventListener).</span></span>
  - <span data-ttu-id="91c05-144">O .NET Core fornece aos ouvintes:</span><span class="sxs-lookup"><span data-stu-id="91c05-144">.NET Core provides listeners for:</span></span>
    - <span data-ttu-id="91c05-145">EventPipe da .NET Core em todas as plataformas</span><span class="sxs-lookup"><span data-stu-id="91c05-145">.NET Core's EventPipe on all platforms</span></span>
    - [<span data-ttu-id="91c05-146">ETW (Rastreamento de Eventos do Windows)</span><span class="sxs-lookup"><span data-stu-id="91c05-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="91c05-147">Estrutura de rastreamento LTTng para Linux</span><span class="sxs-lookup"><span data-stu-id="91c05-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="91c05-148">Incluído no .NET Core e como um [pacote NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) para .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91c05-148">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="91c05-149">Permite o rastreamento em processo de objetos não serializáveis.</span><span class="sxs-lookup"><span data-stu-id="91c05-149">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="91c05-150">Inclui uma ponte para permitir que campos selecionados <xref:System.Diagnostics.Tracing.EventSource>de objetos registrados sejam gravados em um .</span><span class="sxs-lookup"><span data-stu-id="91c05-150">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="91c05-151">Fornece uma maneira definitiva de identificar mensagens de log resultantes de uma atividade ou transação específica.</span><span class="sxs-lookup"><span data-stu-id="91c05-151">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="91c05-152">Este objeto pode ser usado para correlacionar registros em diferentes serviços.</span><span class="sxs-lookup"><span data-stu-id="91c05-152">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="91c05-153">Somente Windows.</span><span class="sxs-lookup"><span data-stu-id="91c05-153">Windows only.</span></span>
  - <span data-ttu-id="91c05-154">Escreve mensagens no Registro de Eventos do Windows.</span><span class="sxs-lookup"><span data-stu-id="91c05-154">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="91c05-155">Os administradores do sistema esperam que mensagens fatais de erro de aplicativo apareçam no Registro de Eventos do Windows.</span><span class="sxs-lookup"><span data-stu-id="91c05-155">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="91c05-156">Estruturas de ILogger e registro</span><span class="sxs-lookup"><span data-stu-id="91c05-156">ILogger and logging frameworks</span></span>

<span data-ttu-id="91c05-157">As APIs de baixo nível podem não ser a escolha certa para suas necessidades de registro.</span><span class="sxs-lookup"><span data-stu-id="91c05-157">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="91c05-158">Você pode querer considerar uma estrutura de registro.</span><span class="sxs-lookup"><span data-stu-id="91c05-158">You may want to consider a logging framework.</span></span>

<span data-ttu-id="91c05-159">A <xref:Microsoft.Extensions.Logging.ILogger> interface foi usada para criar uma interface de registro comum onde os madeireiros podem ser inseridos através de injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="91c05-159">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="91c05-160">Por exemplo, permitir que você faça a `ASP.NET` melhor escolha para o seu aplicativo oferece suporte para uma seleção de frameworks integrados e de terceiros:</span><span class="sxs-lookup"><span data-stu-id="91c05-160">For instance, to allow you to make the best choice for your application `ASP.NET` offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="91c05-161">ASP.NET construído em provedores de registro</span><span class="sxs-lookup"><span data-stu-id="91c05-161">ASP.NET built in logging providers</span></span>](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [<span data-ttu-id="91c05-162">ASP.NET provedores de registro de terceiros</span><span class="sxs-lookup"><span data-stu-id="91c05-162">ASP.NET Third-party logging providers</span></span>](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="91c05-163">Referências relacionadas ao registro</span><span class="sxs-lookup"><span data-stu-id="91c05-163">Logging related references</span></span>

- [<span data-ttu-id="91c05-164">Como compilar condicionalmente com Trace e Debug</span><span class="sxs-lookup"><span data-stu-id="91c05-164">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="91c05-165">Como adicionar instruções de rastreamento ao código de um aplicativo</span><span class="sxs-lookup"><span data-stu-id="91c05-165">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="91c05-166">[ASP.NET Logging](/aspnet/core/fundamentals/logging) fornece uma visão geral das técnicas de registro que suporta.</span><span class="sxs-lookup"><span data-stu-id="91c05-166">[ASP.NET Logging](/aspnet/core/fundamentals/logging) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="91c05-167">[C# Interpolação de strings](../../csharp/language-reference/tokens/interpolated.md) pode simplificar a escrita do código de registro.</span><span class="sxs-lookup"><span data-stu-id="91c05-167">[C# String Interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- <span data-ttu-id="91c05-168">A <xref:System.Exception.Message?displayProperty=nameWithType> propriedade é útil para registrar exceções.</span><span class="sxs-lookup"><span data-stu-id="91c05-168">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="91c05-169">A <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> classe pode ser útil para fornecer informações de pilha em seus registros.</span><span class="sxs-lookup"><span data-stu-id="91c05-169">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="91c05-170">Considerações sobre o desempenho</span><span class="sxs-lookup"><span data-stu-id="91c05-170">Performance considerations</span></span>

<span data-ttu-id="91c05-171">A formatação de strings pode levar um tempo perceptível de processamento da CPU.</span><span class="sxs-lookup"><span data-stu-id="91c05-171">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="91c05-172">Em aplicações críticas de desempenho, recomenda-se que você:</span><span class="sxs-lookup"><span data-stu-id="91c05-172">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="91c05-173">Evite muitos registros quando ninguém estiver ouvindo.</span><span class="sxs-lookup"><span data-stu-id="91c05-173">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="91c05-174">Evite construir mensagens de registro caras verificando se o registro está ativado primeiro.</span><span class="sxs-lookup"><span data-stu-id="91c05-174">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="91c05-175">Só registre o que é útil.</span><span class="sxs-lookup"><span data-stu-id="91c05-175">Only log what's useful.</span></span>
- <span data-ttu-id="91c05-176">Adie a formatação extravagante para o estágio de análise.</span><span class="sxs-lookup"><span data-stu-id="91c05-176">Defer fancy formatting to the analysis stage.</span></span>
