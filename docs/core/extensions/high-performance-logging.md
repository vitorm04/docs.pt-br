---
title: Registro em log de alto desempenho no .NET
author: IEvangelist
description: Saiba como usar o LoggerMessage para criar representantes que podem ser armazenados em cache e exigem menos alocações de objeto para cenários de registro em log de alto desempenho.
ms.author: dapine
ms.date: 09/25/2020
ms.openlocfilehash: d722a3a5cb38f33b6833a5c280687ce6c1e46bf9
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91614678"
---
# <a name="high-performance-logging-in-net"></a><span data-ttu-id="259d7-103">Registro em log de alto desempenho no .NET</span><span class="sxs-lookup"><span data-stu-id="259d7-103">High-performance logging in .NET</span></span>

<span data-ttu-id="259d7-104">A <xref:Microsoft.Extensions.Logging.LoggerMessage> classe expõe a funcionalidade para criar delegados em cache que exigem menos alocações de objeto e menor sobrecarga computacional em comparação com os [métodos de extensão do agente](xref:Microsoft.Extensions.Logging.LoggerExtensions), como <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> e <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> .</span><span class="sxs-lookup"><span data-stu-id="259d7-104">The <xref:Microsoft.Extensions.Logging.LoggerMessage> class exposes functionality to create cacheable delegates that require fewer object allocations and reduced computational overhead compared to [logger extension methods](xref:Microsoft.Extensions.Logging.LoggerExtensions), such as <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> and <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A>.</span></span> <span data-ttu-id="259d7-105">Para cenários de registro em log de alto desempenho, use o padrão <xref:Microsoft.Extensions.Logging.LoggerMessage>.</span><span class="sxs-lookup"><span data-stu-id="259d7-105">For high-performance logging scenarios, use the <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern.</span></span>

<span data-ttu-id="259d7-106"><xref:Microsoft.Extensions.Logging.LoggerMessage> fornece as seguintes vantagens de desempenho em relação aos métodos de extensão do Agente:</span><span class="sxs-lookup"><span data-stu-id="259d7-106"><xref:Microsoft.Extensions.Logging.LoggerMessage> provides the following performance advantages over Logger extension methods:</span></span>

- <span data-ttu-id="259d7-107">Métodos de extensão do agente exigem tipos de valor de conversão boxing, como `int`, em `object`.</span><span class="sxs-lookup"><span data-stu-id="259d7-107">Logger extension methods require "boxing" (converting) value types, such as `int`, into `object`.</span></span> <span data-ttu-id="259d7-108">O padrão <xref:Microsoft.Extensions.Logging.LoggerMessage> evita a conversão boxing usando campos <xref:System.Action> estáticos e métodos de extensão com parâmetros fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="259d7-108">The <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern avoids boxing by using static <xref:System.Action> fields and extension methods with strongly-typed parameters.</span></span>
- <span data-ttu-id="259d7-109">Os métodos de extensão do agente precisam analisar o modelo de mensagem (cadeia de caracteres de formato nomeada) sempre que uma mensagem de log é gravada.</span><span class="sxs-lookup"><span data-stu-id="259d7-109">Logger extension methods must parse the message template (named format string) every time a log message is written.</span></span> <span data-ttu-id="259d7-110"><xref:Microsoft.Extensions.Logging.LoggerMessage> exige apenas a análise de um modelo uma vez quando a mensagem é definida.</span><span class="sxs-lookup"><span data-stu-id="259d7-110"><xref:Microsoft.Extensions.Logging.LoggerMessage> only requires parsing a template once when the message is defined.</span></span>

<span data-ttu-id="259d7-111">O aplicativo de exemplo demonstra <xref:Microsoft.Extensions.Logging.LoggerMessage> recursos com um serviço de trabalho de processamento de fila de prioridade.</span><span class="sxs-lookup"><span data-stu-id="259d7-111">The sample app demonstrates <xref:Microsoft.Extensions.Logging.LoggerMessage> features with a priority queue processing worker service.</span></span> <span data-ttu-id="259d7-112">O aplicativo processa itens de trabalho em ordem de prioridade.</span><span class="sxs-lookup"><span data-stu-id="259d7-112">The app processes work items in priority order.</span></span> <span data-ttu-id="259d7-113">Conforme ocorrem essas operações, são geradas mensagens de log usando o padrão <xref:Microsoft.Extensions.Logging.LoggerMessage>.</span><span class="sxs-lookup"><span data-stu-id="259d7-113">As these operations occur, log messages are generated using the <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern.</span></span>

## <a name="define-a-logger-message"></a><span data-ttu-id="259d7-114">Definir uma mensagem de agente</span><span class="sxs-lookup"><span data-stu-id="259d7-114">Define a logger message</span></span>

<span data-ttu-id="259d7-115">Use [define (LogLevel, EventID, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) para criar um <xref:System.Action> delegado para registrar uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="259d7-115">Use [Define(LogLevel, EventId, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) to create an <xref:System.Action> delegate for logging a message.</span></span> <span data-ttu-id="259d7-116">Sobrecargas de <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> permitem passar até seis parâmetros de tipo para uma cadeia de caracteres de formato nomeada (modelo).</span><span class="sxs-lookup"><span data-stu-id="259d7-116"><xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> overloads permit passing up to six type parameters to a named format string (template).</span></span>

<span data-ttu-id="259d7-117">A cadeia de caracteres fornecida para o método <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> é um modelo e não uma cadeia de caracteres interpolada.</span><span class="sxs-lookup"><span data-stu-id="259d7-117">The string provided to the <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> method is a template and not an interpolated string.</span></span> <span data-ttu-id="259d7-118">Os espaços reservados são preenchidos na ordem em que os tipos são especificados.</span><span class="sxs-lookup"><span data-stu-id="259d7-118">Placeholders are filled in the order that the types are specified.</span></span> <span data-ttu-id="259d7-119">Os nomes do espaço reservado no modelo devem ser descritivos e consistentes em todos os modelos.</span><span class="sxs-lookup"><span data-stu-id="259d7-119">Placeholder names in the template should be descriptive and consistent across templates.</span></span> <span data-ttu-id="259d7-120">Eles servem como nomes de propriedade em dados de log estruturado.</span><span class="sxs-lookup"><span data-stu-id="259d7-120">They serve as property names within structured log data.</span></span> <span data-ttu-id="259d7-121">Recomendamos o uso da [formatação Pascal Case](../../standard/design-guidelines/capitalization-conventions.md) para nomes de espaço reservado.</span><span class="sxs-lookup"><span data-stu-id="259d7-121">We recommend [Pascal casing](../../standard/design-guidelines/capitalization-conventions.md) for placeholder names.</span></span> <span data-ttu-id="259d7-122">Por exemplo, `{Item}`, `{DateTime}`.</span><span class="sxs-lookup"><span data-stu-id="259d7-122">For example, `{Item}`, `{DateTime}`.</span></span>

<span data-ttu-id="259d7-123">Cada mensagem de log é uma <xref:System.Action> mantida em um campo estático criado por [LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A).</span><span class="sxs-lookup"><span data-stu-id="259d7-123">Each log message is an <xref:System.Action> held in a static field created by [LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A).</span></span> <span data-ttu-id="259d7-124">Por exemplo, o aplicativo de exemplo cria um campo para descrever uma mensagem de log para o processamento de itens de trabalho:</span><span class="sxs-lookup"><span data-stu-id="259d7-124">For example, the sample app creates a field to describe a log message for the processing of work items:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkField":::

<span data-ttu-id="259d7-125">Para a <xref:System.Action>, especifique:</span><span class="sxs-lookup"><span data-stu-id="259d7-125">For the <xref:System.Action>, specify:</span></span>

- <span data-ttu-id="259d7-126">O nível de log.</span><span class="sxs-lookup"><span data-stu-id="259d7-126">The log level.</span></span>
- <span data-ttu-id="259d7-127">Um identificador de evento exclusivo (<xref:Microsoft.Extensions.Logging.EventId>) com o nome do método de extensão estático.</span><span class="sxs-lookup"><span data-stu-id="259d7-127">A unique event identifier (<xref:Microsoft.Extensions.Logging.EventId>) with the name of the static extension method.</span></span>
- <span data-ttu-id="259d7-128">O modelo de mensagem (cadeia de caracteres de formato nomeada).</span><span class="sxs-lookup"><span data-stu-id="259d7-128">The message template (named format string).</span></span>

<span data-ttu-id="259d7-129">À medida que os itens de trabalho são recolocados na fila para processamento, o aplicativo do serviço de trabalho define:</span><span class="sxs-lookup"><span data-stu-id="259d7-129">As work items are dequeued for processing the worker service app sets the:</span></span>

- <span data-ttu-id="259d7-130">O nível de log como `Critical`.</span><span class="sxs-lookup"><span data-stu-id="259d7-130">Log level to `Critical`.</span></span>
- <span data-ttu-id="259d7-131">A ID do evento como `13` com o nome do método `FailedToProcessWorkItem`.</span><span class="sxs-lookup"><span data-stu-id="259d7-131">Event id to `13` with the name of the `FailedToProcessWorkItem` method.</span></span>
- <span data-ttu-id="259d7-132">Modelo de mensagem (cadeia de caracteres de formato nomeada) como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="259d7-132">Message template (named format string) to a string.</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkAssignment":::

<span data-ttu-id="259d7-133">Repositórios de log estruturado podem usar o nome do evento quando recebem a ID do evento para enriquecer o log.</span><span class="sxs-lookup"><span data-stu-id="259d7-133">Structured logging stores may use the event name when it's supplied with the event id to enrich logging.</span></span> <span data-ttu-id="259d7-134">Por exemplo, [Serilog](https://github.com/serilog/serilog-extensions-logging) usa o nome do evento.</span><span class="sxs-lookup"><span data-stu-id="259d7-134">For example, [Serilog](https://github.com/serilog/serilog-extensions-logging) uses the event name.</span></span>

<span data-ttu-id="259d7-135">A <xref:System.Action> é invocada por meio de um método de extensão fortemente tipado.</span><span class="sxs-lookup"><span data-stu-id="259d7-135">The <xref:System.Action> is invoked through a strongly-typed extension method.</span></span> <span data-ttu-id="259d7-136">O `FailedToProcessWorkItem` método registra uma mensagem toda vez que um item de trabalho está sendo processado:</span><span class="sxs-lookup"><span data-stu-id="259d7-136">The `FailedToProcessWorkItem` method logs a message every time a work item is being processed:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkMethod":::

<span data-ttu-id="259d7-137">`FailedToProcessWorkItem` é chamado no agente de log no `ExecuteAsync` método em *Worker.cs* quando ocorre um erro:</span><span class="sxs-lookup"><span data-stu-id="259d7-137">`FailedToProcessWorkItem` is called on the logger in the `ExecuteAsync` method in *Worker.cs* when an error occurs:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="15-18":::

<span data-ttu-id="259d7-138">Inspecione a saída do console do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="259d7-138">Inspect the app's console output:</span></span>

```console
crit: WorkerServiceOptions.Example.Worker[13]
      Epic failure processing item!
      System.Exception: Failed to verify communications.
         at WorkerServiceOptions.Example.Worker.ExecuteAsync(CancellationToken stoppingToken) in
         ..\Worker.cs:line 27
```

<span data-ttu-id="259d7-139">Para passar parâmetros para uma mensagem de log, defina até seis tipos ao criar o campo estático.</span><span class="sxs-lookup"><span data-stu-id="259d7-139">To pass parameters to a log message, define up to six types when creating the static field.</span></span> <span data-ttu-id="259d7-140">O aplicativo de exemplo registra em log os detalhes do item de trabalho ao processar itens definindo um `WorkItem` tipo para o <xref:System.Action> campo:</span><span class="sxs-lookup"><span data-stu-id="259d7-140">The sample app logs the work item details when processing items by defining a `WorkItem` type for the <xref:System.Action> field:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemField":::

<span data-ttu-id="259d7-141">O modelo de mensagem de log do delegado recebe seus valores de espaço reservado dos tipos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="259d7-141">The delegate's log message template receives its placeholder values from the types provided.</span></span> <span data-ttu-id="259d7-142">O aplicativo de exemplo define um delegado para adicionar aspas quando o parâmetro de aspas é uma `WorkItem`:</span><span class="sxs-lookup"><span data-stu-id="259d7-142">The sample app defines a delegate for adding a quote where the quote parameter is a `WorkItem`:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemAssignment":::

<span data-ttu-id="259d7-143">O método de extensão estático para registrar em log que um item de trabalho está sendo processado, `PriorityItemProcessed` , recebe o valor do argumento de item de trabalho e o passa para o <xref:System.Action> delegado:</span><span class="sxs-lookup"><span data-stu-id="259d7-143">The static extension method for logging that a work item is being processed, `PriorityItemProcessed`, receives the work item argument value and passes it to the <xref:System.Action> delegate:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemMethod":::

<span data-ttu-id="259d7-144">No método do serviço de trabalho `ExecuteAsync` , `PriorityItemProcessed` é chamado para registrar a mensagem:</span><span class="sxs-lookup"><span data-stu-id="259d7-144">In the worker service's `ExecuteAsync` method, `PriorityItemProcessed` is called to log the message:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="12":::

<span data-ttu-id="259d7-145">Inspecione a saída do console do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="259d7-145">Inspect the app's console output:</span></span>

```console
info: WorkerServiceOptions.Example.Worker[1]
      Processing priority item: Priority-Extreme (50db062a-9732-4418-936d-110549ad79e4): 'Verify communications'
```

## <a name="define-logger-message-scope"></a><span data-ttu-id="259d7-146">Definir escopo de mensagem de agente</span><span class="sxs-lookup"><span data-stu-id="259d7-146">Define logger message scope</span></span>

<span data-ttu-id="259d7-147">O método [DefineScope (String)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) cria um <xref:System.Func%601> delegado para definir um [escopo de log](logging.md#log-scopes).</span><span class="sxs-lookup"><span data-stu-id="259d7-147">The [DefineScope(string)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) method creates a <xref:System.Func%601> delegate for defining a [log scope](logging.md#log-scopes).</span></span> <span data-ttu-id="259d7-148">Sobrecargas de <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> permitem passar até três parâmetros de tipo para uma cadeia de caracteres de formato nomeada (modelo).</span><span class="sxs-lookup"><span data-stu-id="259d7-148"><xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> overloads permit passing up to three type parameters to a named format string (template).</span></span>

<span data-ttu-id="259d7-149">Como é o caso com o método <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A>, a cadeia de caracteres fornecida ao método <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> é um modelo e não uma cadeia de caracteres interpolada.</span><span class="sxs-lookup"><span data-stu-id="259d7-149">As is the case with the <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> method, the string provided to the <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> method is a template and not an interpolated string.</span></span> <span data-ttu-id="259d7-150">Os espaços reservados são preenchidos na ordem em que os tipos são especificados.</span><span class="sxs-lookup"><span data-stu-id="259d7-150">Placeholders are filled in the order that the types are specified.</span></span> <span data-ttu-id="259d7-151">Os nomes do espaço reservado no modelo devem ser descritivos e consistentes em todos os modelos.</span><span class="sxs-lookup"><span data-stu-id="259d7-151">Placeholder names in the template should be descriptive and consistent across templates.</span></span> <span data-ttu-id="259d7-152">Eles servem como nomes de propriedade em dados de log estruturado.</span><span class="sxs-lookup"><span data-stu-id="259d7-152">They serve as property names within structured log data.</span></span> <span data-ttu-id="259d7-153">Recomendamos o uso da [formatação Pascal Case](/dotnet/standard/design-guidelines/capitalization-conventions) para nomes de espaço reservado.</span><span class="sxs-lookup"><span data-stu-id="259d7-153">We recommend [Pascal casing](/dotnet/standard/design-guidelines/capitalization-conventions) for placeholder names.</span></span> <span data-ttu-id="259d7-154">Por exemplo, `{Item}`, `{DateTime}`.</span><span class="sxs-lookup"><span data-stu-id="259d7-154">For example, `{Item}`, `{DateTime}`.</span></span>

<span data-ttu-id="259d7-155">Defina um [escopo de log](logging.md#log-scopes) a ser aplicado a uma série de mensagens de log usando o método <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A>.</span><span class="sxs-lookup"><span data-stu-id="259d7-155">Define a [log scope](logging.md#log-scopes) to apply to a series of log messages using the <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> method.</span></span>

<span data-ttu-id="259d7-156">O aplicativo de exemplo tem um botão **Limpar Tudo** para excluir todas as aspas no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="259d7-156">The sample app has a **Clear All** button for deleting all of the quotes in the database.</span></span> <span data-ttu-id="259d7-157">As aspas são excluídas com a remoção das aspas individualmente, uma por vez.</span><span class="sxs-lookup"><span data-stu-id="259d7-157">The quotes are deleted by removing them one at a time.</span></span> <span data-ttu-id="259d7-158">Sempre que aspas são excluídas, o método `QuoteDeleted` é chamado no agente.</span><span class="sxs-lookup"><span data-stu-id="259d7-158">Each time a quote is deleted, the `QuoteDeleted` method is called on the logger.</span></span> <span data-ttu-id="259d7-159">Um escopo de log é adicionado a essas mensagens de log.</span><span class="sxs-lookup"><span data-stu-id="259d7-159">A log scope is added to these log messages.</span></span>

<span data-ttu-id="259d7-160">Habilite `IncludeScopes` na seção de agente do console de *appSettings.json*:</span><span class="sxs-lookup"><span data-stu-id="259d7-160">Enable `IncludeScopes` in the console logger section of *appsettings.json*:</span></span>

:::code language="json" source="snippets/configuration/worker-service-options/appsettings.json" highlight="3-5":::

<span data-ttu-id="259d7-161">Para criar um escopo de log, adicione um campo para conter um delegado <xref:System.Func%601> para o escopo.</span><span class="sxs-lookup"><span data-stu-id="259d7-161">To create a log scope, add a field to hold a <xref:System.Func%601> delegate for the scope.</span></span> <span data-ttu-id="259d7-162">O aplicativo de exemplo cria um campo chamado `_allQuotesDeletedScope` (*Internal/LoggerExtensions.cs*):</span><span class="sxs-lookup"><span data-stu-id="259d7-162">The sample app creates a field called `_allQuotesDeletedScope` (*Internal/LoggerExtensions.cs*):</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkField":::

<span data-ttu-id="259d7-163">Use <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> para criar o delegado.</span><span class="sxs-lookup"><span data-stu-id="259d7-163">Use <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> to create the delegate.</span></span> <span data-ttu-id="259d7-164">Até três tipos podem ser especificados para uso como argumentos de modelo quando o delegado é invocado.</span><span class="sxs-lookup"><span data-stu-id="259d7-164">Up to three types can be specified for use as template arguments when the delegate is invoked.</span></span> <span data-ttu-id="259d7-165">O aplicativo de exemplo usa um modelo de mensagem que inclui o número de aspas excluídas (um tipo `int`):</span><span class="sxs-lookup"><span data-stu-id="259d7-165">The sample app uses a message template that includes the number of deleted quotes (an `int` type):</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkAssignment":::

<span data-ttu-id="259d7-166">Forneça um método de extensão estático para a mensagem de log.</span><span class="sxs-lookup"><span data-stu-id="259d7-166">Provide a static extension method for the log message.</span></span> <span data-ttu-id="259d7-167">Inclua os parâmetros de tipo para propriedades nomeadas exibidos no modelo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="259d7-167">Include any type parameters for named properties that appear in the message template.</span></span> <span data-ttu-id="259d7-168">O aplicativo de exemplo usa um `DateTime` para um carimbo de data/hora personalizado para registrar e retornar `_processingWorkScope` :</span><span class="sxs-lookup"><span data-stu-id="259d7-168">The sample app takes in a `DateTime` for a custom time stamp to log and returns `_processingWorkScope`:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkMethod":::

<span data-ttu-id="259d7-169">O escopo encapsula as chamadas de extensão de log em um bloco [using](../../csharp/language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="259d7-169">The scope wraps the logging extension calls in a [using](../../csharp/language-reference/keywords/using-statement.md) block:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="4":::

<span data-ttu-id="259d7-170">Inspecione as mensagens de log na saída do console do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="259d7-170">Inspect the log messages in the app's console output.</span></span> <span data-ttu-id="259d7-171">O seguinte resultado mostra três aspas excluídas com a mensagem de escopo de log incluída:</span><span class="sxs-lookup"><span data-stu-id="259d7-171">The following result shows three quotes deleted with the log scope message included:</span></span>

```console
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Extreme (f5090ede-a337-4041-b914-f6bc0db5ae64): 'Verify communications'
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: ..\worker-service-options
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-High (496d440f-2007-4391-b179-09d75ab52373): 'Validate collection'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (dea9e3f4-d7df-46d2-b7cd-5e0232eb98a5): 'Propagate selections'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (089d7f0d-da72-4b55-92fe-57b147838056): 'Enter pooling [contention]'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Low (6e68c4be-089f-4450-9080-1ea63fcbb686): 'Health check network'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (6f324134-6bb6-455f-81d4-553ab307c421): 'Ping weather service'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (37bf736c-7a26-4a2a-9e56-e89bcf3b8f35): 'Set process state'
```

## <a name="see-also"></a><span data-ttu-id="259d7-172">Confira também</span><span class="sxs-lookup"><span data-stu-id="259d7-172">See also</span></span>

- [<span data-ttu-id="259d7-173">Registro em log no .NET</span><span class="sxs-lookup"><span data-stu-id="259d7-173">Logging in .NET</span></span>](logging.md)
